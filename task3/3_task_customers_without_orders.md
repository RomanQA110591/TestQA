
# Задача 3: Клиенты без заказов

## Условие

Даны две таблицы:
- `Customers` (`id` INT PRIMARY KEY, `name` VARCHAR)
- `Orders` (`id` INT PRIMARY KEY, `customerId` INT FOREIGN KEY ссылается на `Customers.id`)

Необходимо вывести имена всех клиентов, у которых **нет ни одного заказа** в таблице `Orders`.

## Решение (PostgreSQL)

SELECT c.name
FROM Customers c
LEFT JOIN Orders o ON c.id = o.customerId
WHERE o.id IS NULL;


*Пояснение*

LEFT JOIN – объединяем клиентов с заказами. Если заказа нет, поля из Orders будут NULL, и условие o.id IS NULL отбирает таких клиентов.
