# lb7                                                                                                        
  
завдання 13
# Проект: Управління базою даних

Цей репозиторій містить скрипти для виконання лабораторних завдань з баз даних.

## Файли:

- **SETUP.SQL** - створення таблиць і їхньої структури.
- **INSERT.SQL** - вставка початкових даних в таблиці.
- **UPDATE.SQL** - оновлення даних в таблицях.
- **QUERY.SQL** - приклади запитів до бази даних.
- **FUNCTIONS.SQL** - визначення функцій в SQL.
- **CURSORES.SQL** - використання курсорів.
- **TRIGGERS.SQL** - тригери для виконання дій після змін в таблицях.

## Завдання:
1. **Завдання 7**: Реалізація тригерів для підтримки цілісності.
2. **Завдання 8**: Використання тригерів в практичних завданнях.
3. **Завдання 9**: Створення обмежень цілісності.
4. **Завдання 10**: Створення DDL тригерів для створення та видалення таблиць.

## Інструкція для запуску контейнера:

1. Створіть Docker контейнер з MSSQL сервером:
  SETUP.SQL
CREATE TABLE Products (
  ProductID INT PRIMARY KEY,
  ProductName NVARCHAR(100),
  Price DECIMAL(10, 2)
);

CREATE TABLE Customers (
  CustomerID INT PRIMARY KEY,
  CustomerName NVARCHAR(100),
  Email NVARCHAR(100)
);

INSERT INTO Products (ProductID, ProductName, Price)
VALUES (1, 'Product A', 50.00), (2, 'Product B', 30.00);

INSERT INTO Customers (CustomerID, CustomerName, Email)
VALUES (1, 'Customer 1', 'customer1@example.com');
 TRIGGERS.SQL 
 CREATE TRIGGER trg_logon
ON ALL SERVER
FOR LOGON
AS
BEGIN
  PRINT 'Користувач увійшов до системи';
END;
 INTEGRITY_CONSTRAINTS.SQL
 -- Приклад обмеження цілісності (CHECK)
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name NVARCHAR(100) NOT NULL,
    Age INT CHECK (Age >= 18)
);

-- Обмеження зовнішнього ключа
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    EmployeeID INT,
    OrderDate DATE,
    CONSTRAINT FK_Employee FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
