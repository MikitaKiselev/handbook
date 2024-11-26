# Шаг 1: Справочники

## Справочники

1. **Справочник сотрудников**
2. **Справочник отделов**

## Перечень колонок

### Справочник сотрудников (Employees):
- **Id** (int, Primary Key) — Уникальный идентификатор сотрудника.
- **FirstName** (nvarchar(50)) — Имя сотрудника.
- **LastName** (nvarchar(50)) — Фамилия сотрудника.
- **DepartmentId** (int, Foreign Key) — Идентификатор отдела из справочника отделов.
- **HireDate** (date) — Дата приема на работу.
- **Salary** (decimal(18, 2)) — Зарплата сотрудника.

### Справочник отделов (Departments):
- **Id** (int, Primary Key) — Уникальный идентификатор отдела.
- **Name** (nvarchar(100)) — Наименование отдела.
- **Location** (nvarchar(100)) — Местоположение отдела.
- **Budget** (decimal(18, 2)) — Бюджет отдела.

# Шаг 2: Проектирование и создание таблиц

## Выбор СУБД
**СУБД**: Microsoft SQL Server

## Схема БД

```sql
CREATE TABLE Departments (
    Id INT PRIMARY KEY IDENTITY(1,1),
    Name NVARCHAR(100) NOT NULL,
    Location NVARCHAR(100) NOT NULL,
    Budget DECIMAL(18, 2) NOT NULL
);

CREATE TABLE Employees (
    Id INT PRIMARY KEY IDENTITY(1,1),
    FirstName NVARCHAR(50) NOT NULL,
    LastName NVARCHAR(50) NOT NULL,
    DepartmentId INT,
    HireDate DATE NOT NULL,
    Salary DECIMAL(18, 2) NOT NULL,
    FOREIGN KEY (DepartmentId) REFERENCES Departments(Id)
);
```
## Пример заполнения данных

### Вставка данных

```sql
INSERT INTO Departments (Name, Location, Budget) VALUES
(N'Отдел продаж', N'Минск', 150000.00),
(N'Отдел разработки', N'Гомель', 200000.00),
(N'Отдел маркетинга', N'Витебск', 100000.00);

INSERT INTO Employees (FirstName, LastName, DepartmentId, HireDate, Salary) VALUES
(N'Иван', N'Иванов', 1, '2020-02-15', 50000.00),
(N'Мария', N'Петрова', 2, '2019-06-01', 60000.00),
(N'Александр', N'Сидоров', 1, '2021-08-20', 55000.00);
```
