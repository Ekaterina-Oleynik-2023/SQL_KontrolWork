# SQL_KontrolWork
Контрольная работа к курсу - Базы данных и SQL.
![pictures MySQL for SQL](https://github.com/Terekhov-A-S/SQL_Seminar_6/blob/main/MySQL.jpg)
## Задача 1:

#### Создайте функцию, которая принимает кол-во сек и формат их в кол-во дней часов. 
#### Пример: 123456 ->'1 days 10 hours 17 minutes 36 seconds '
```
DELIMITER //
CREATE PROCEDURE times(seconds INT)
BEGIN
    DECLARE days INT default 0;
    DECLARE hours INT default 0;
    DECLARE minutes INT default 0;

    WHILE seconds >= 86400 DO
    SET days = floor(seconds / 86400);
    SET seconds = seconds % 86400;
    END WHILE;

    WHILE seconds >= 3600 DO
    SET hours = floor(seconds / 3600);
    SET seconds = seconds % 3600;
    END WHILE;

    WHILE seconds >= 60 DO
    SET minutes = floor(seconds / 60);
    SET seconds = seconds % 60;
    END WHILE;

SELECT days, hours, minutes, seconds;
END //
DELIMITER ;
```
#### проверка
```
CALL times(123456);
```
## Задача 2:

#### Выведите только четные числа от 1 до 10. Пример: 2,4,6,8,10
```
DELIMITER //
CREATE PROCEDURE numbers()
BEGIN
    DECLARE x INT default 0;
    DROP TABLE IF EXISTS nums;
    CREATE TABLE nums (x INT);

    WHILE x < 10 DO
    SET x = x + 2;
    INSERT INTO nums VALUES(x);
    END WHILE;

SELECT * FROM nums;
END //
DELIMITER ;
```
#### проверка
```
CALL numbers();
```
#### *Подготовил студент Geek Brains ОЛЕЙНИК ЕКАТЕРИНА* 
