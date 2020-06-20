---
title: Порядковые номера | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- sequence number object, overview
- sequence [Database Engine]
- autonumbers, sequences
- sequence numbers [SQL Server]
- sequence number object
ms.assetid: c900e30d-2fd3-4d5f-98ee-7832f37e79d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6c65b4df915a85cf0ec7c7c0c8c0ff9f6607ad96
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055304"
---
# <a name="sequence-numbers"></a>Порядковые номера
  Последовательность представляет собой определяемый пользователем объект, привязанный к схеме, который формирует последовательность числовых значений в соответствии со спецификацией, с которой эта последовательность создавалась. Последовательность числовых значений формируется в возрастающем или убывающем порядке с определенным интервалом и может повторяться запрошенным образом. В отличие от столбцов идентификаторов последовательности не связаны с таблицами. Приложение обращается к объекту последовательности, чтобы получить следующее значение. Приложения управляют связями между последовательностями и таблицами. Пользовательские приложения могут ссылаться на объект последовательности и координировать ключи значений между несколькими строками и таблицами.  
  
 Последовательность создается независимо от таблиц с помощью инструкции **CREATE SEQUENCE** . Параметры позволяют управлять приращением, максимальным и минимальным значением, начальной точкой, возможностью автоматического перезапуска и кэшированием для повышения производительности. Сведения о параметрах см. в разделе [CREATE SEQUENCE](/sql/t-sql/statements/create-sequence-transact-sql).  
  
 В отличие от значений столбцов идентификаторов, которые создаются при вставке строк, приложение может получить следующий порядковый номер до вставки строки, вызвав функцию [NEXT VALUE FOR](/sql/t-sql/functions/next-value-for-transact-sql) . Порядковый номер выделяется, когда вызывается функция NEXT VALUE FOR, даже если номер так и не вставляется в таблицу. Функцию NEXT VALUE FOR можно использовать в качестве значения по умолчанию для столбца в определении таблицы. Сразу получить диапазон порядковых номеров можно с помощью процедуры [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) .  
  
 Последовательность может быть определена с любым типом данных integer. Если тип данных не указан, по умолчанию для последовательности используется тип `bigint`.  
  
## <a name="using-sequences"></a>Использование последовательностей  
 Последовательности используются вместо столбцов идентификаторов в следующих сценариях.  
  
-   Приложению требуется номер до выполнения вставки в таблицу.  
  
-   Приложению требуется единая нумерация для нескольких таблиц или нескольких столбцов в таблице.  
  
-   Приложение должно перезапускать последовательность номеров по достижении определенного номера. Например, после назначения значений от 1 до 10 приложение вновь начинает назначать значения от 1 до 10.  
  
-   Приложению необходимо сортировать значения последовательности по другому полю. Функция NEXT VALUE FOR может применять предложение OVER к вызову функции. Предложение OVER гарантирует, что возвращаемые значения создаются в порядке, указанном предложением ORDER BY в предложении OVER.  
  
-   Приложению требуется одновременно назначать несколько номеров. Например, приложению требуется зарезервировать пять порядковых номеров. Запрос значений идентификаторов может вызвать пропуски в последовательности, если другие процессы одновременно запросили номера. Вызов процедуры sp_sequence_get_range может получить несколько номеров в последовательности сразу.  
  
-   Необходимо изменить спецификацию последовательности, например значение приращения.  
  
## <a name="limitations"></a>Ограничения  
 В отличие от столбцов идентификаторов, значения которых нельзя изменять, значения последовательностей не защищаются автоматически после вставки в таблицу. Чтобы запретить изменение значений последовательности, используйте в таблице триггер Update для отката изменений.  
  
 Уникальность значений последовательности не соблюдается автоматически. Значения последовательностей изначально предусматривают многократное использование. Если значения последовательности в таблице должны быть уникальными, создайте для столбца уникальный индекс. Если значения последовательности должны быть уникальными в пределах группы таблиц, создайте триггеры для исключения повторов, вызываемых инструкциями обновлений или циклической сменой порядковых номеров.  
  
 Объект последовательности создает номера в соответствии с определением, однако он не контролирует использование этих номеров. В порядковых номерах, вставляемых в таблицу, могут возникать промежутки в случае отката транзакции, если объект последовательности совместно используется несколькими таблицами или если порядковые номера выделяются, но не используются в таблицах. Если создание производилось с параметром CACHE, то непредвиденное завершение (например, сбой питания) может привести к потере последовательных номеров в кэше.  
  
 Если несколько экземпляров функции `NEXT VALUE FOR` определяют один и тот же генератор последовательностей в одной инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)], то все такие экземпляры возвращают одно и то же значение для строки, обрабатываемой этой инструкцией [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Такое поведение согласуется со стандартом ANSI.  
  
## <a name="typical-use"></a>Типичные случаи использования  
 Чтобы создать целочисленный порядковый номер с приращением 1, меняющийся от -2 147 483 648 до 2 147 483 647, используйте следующую инструкцию.  
  
```  
CREATE SEQUENCE Schema.SequenceName  
    AS int  
    INCREMENT BY 1 ;  
```  
  
 Чтобы создать целочисленный порядковый номер, аналогичный столбцу идентификаторов с приращением 1, меняющемуся от 1 до 2 147 483 647, используйте следующую инструкцию.  
  
```  
CREATE SEQUENCE Schema.SequenceName  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
  
```  
  
## <a name="managing-sequences"></a>Управление последовательностями  
 Чтобы получить сведения о последовательностях, запросите представление [sys.sequences](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql).  
  
## <a name="examples"></a>Примеры  
 Дополнительные примеры см. в статьях [CREATE SEQUENCE (Transact-SQL)](/sql/t-sql/statements/create-sequence-transact-sql), [NEXT VALUE FOR (Transact-SQL)](/sql/t-sql/functions/next-value-for-transact-sql) и [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql).  
  
### <a name="a-using-a-sequence-number-in-a-single-table"></a>A. Использование порядкового номера в одной таблице  
 В следующем примере создается схема с именем Test, таблица с именем Orders и последовательность с именем CountBy1, а затем строки вставляются в таблицу с помощью функции NEXT VALUE FOR.  
  
```  
--Create the Test schema  
CREATE SCHEMA Test ;  
GO  
  
-- Create a table  
CREATE TABLE Test.Orders  
    (OrderID int PRIMARY KEY,  
    Name varchar(20) NOT NULL,  
    Qty int NOT NULL);  
GO  
  
-- Create a sequence  
CREATE SEQUENCE Test.CountBy1  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
-- Insert three records  
INSERT Test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Tire', 2) ;  
INSERT test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Seat', 1) ;  
INSERT test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Brake', 1) ;  
GO  
  
-- View the table  
SELECT * FROM Test.Orders ;  
GO  
```  
  
 [!INCLUDE[ssResult](../../../includes/ssresult-md.md)]  
  
 `OrderID  Name    Qty`  
  
 `1        Tire    2`  
  
 `2        Seat    1`  
  
 `3        Brake   1`  
  
### <a name="b-calling-next-value-for-before-inserting-a-row"></a>Б. Вызов NEXT VALUE FOR до вставки строки  
 В следующем примере с помощью таблицы `Orders` , созданной в примере А, объявляется переменная с именем `@nextID`, а затем с помощью функции NEXT VALUE FOR этой переменной присваивается следующий доступный порядковый номер. Предполагается, что в приложении выполняется некоторая обработка заказа, например заказчику сообщается номер `OrderID` потенциального заказа, а затем проводится проверка заказа. Независимо от времени, затрачиваемого на такую обработку, и от числа других заказов, добавляемых во время обработки, исходный номер сохраняется для использования в этом соединении. Наконец, инструкция `INSERT` добавляет заказ в таблицу `Orders` .  
  
```  
DECLARE @NextID int ;  
SET @NextID = NEXT VALUE FOR Test.CountBy1;  
-- Some work happens  
INSERT Test.Orders (OrderID, Name, Qty)  
    VALUES (@NextID, 'Rim', 2) ;  
GO  
  
```  
  
### <a name="c-using-a-sequence-number-in-multiple-tables"></a>В. Использование порядкового номера в нескольких таблицах  
 В этом примере предполагается, что процесс мониторинга производственной линии получает уведомления о событиях, происходящих в цеху. Каждое событие получает уникальный, монотонно возрастающий номер `EventID` . Все события используют один порядковый номер `EventID` , и поэтому отчеты, где объединяются все события, могут однозначно определить каждое событие. Данные событий хранятся в трех различных таблицах в зависимости от типа события. В примере кода создается схема с именем `Audit`, последовательность с именем `EventCounter`и три таблицы, каждая из которых использует последовательность `EventCounter` в качестве значения по умолчанию. Затем в примере добавляются строки в три таблицы и запрашиваются результаты.  
  
```  
CREATE SCHEMA Audit ;  
GO  
CREATE SEQUENCE Audit.EventCounter  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
CREATE TABLE Audit.ProcessEvents  
(  
    EventID int PRIMARY KEY CLUSTERED   
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EventCode nvarchar(5) NOT NULL,  
    Description nvarchar(300) NULL  
) ;  
GO  
  
CREATE TABLE Audit.ErrorEvents  
(  
    EventID int PRIMARY KEY CLUSTERED  
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EquipmentID int NULL,  
    ErrorNumber int NOT NULL,  
    EventDesc nvarchar(256) NULL  
) ;  
GO  
  
CREATE TABLE Audit.StartStopEvents  
(  
    EventID int PRIMARY KEY CLUSTERED  
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EquipmentID int NOT NULL,  
    StartOrStop bit NOT NULL  
) ;  
GO  
  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (248, 0) ;  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (72, 0) ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (2735,   
    'Clean room temperature 18 degrees C.') ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (18, 'Spin rate threashold exceeded.') ;  
INSERT Audit.ErrorEvents (EquipmentID, ErrorNumber, EventDesc)   
    VALUES (248, 82, 'Feeder jam') ;  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (248, 1) ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (1841, 'Central feed in bypass mode.') ;  
-- The following statement combines all events, though not all fields.  
SELECT EventID, EventTime, Description FROM Audit.ProcessEvents   
UNION SELECT EventID, EventTime, EventDesc FROM Audit.ErrorEvents   
UNION SELECT EventID, EventTime,   
CASE StartOrStop   
    WHEN 0 THEN 'Start'   
    ELSE 'Stop'  
END   
FROM Audit.StartStopEvents  
ORDER BY EventID ;  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../../includes/ssresult-md.md)]  
  
 `EventID  EventTime                Description`  
  
 `1        2009-11-02 15:00:51.157  Start`  
  
 `2        2009-11-02 15:00:51.160  Start`  
  
 `3        2009-11-02 15:00:51.167  Clean room temperature 18 degrees C.`  
  
 `4        2009-11-02 15:00:51.167  Spin rate threshold exceeded.`  
  
 `5        2009-11-02 15:00:51.173  Feeder jam`  
  
 `6        2009-11-02 15:00:51.177  Stop`  
  
 `7        2009-11-02 15:00:51.180  Central feed in bypass mode.`  
  
### <a name="d-generating-repeating-sequence-numbers-in-a-result-set"></a>Г. Создание повторяющихся порядковых номеров в результирующем наборе  
 В следующем примере показаны две возможности работы с порядковыми номерами: циклическое повторение и использование `NEXT VALUE FOR` в инструкции SELECT.  
  
```  
CREATE SEQUENCE CountBy5  
   AS tinyint  
    START WITH 1  
    INCREMENT BY 1  
    MINVALUE 1  
    MAXVALUE 5  
    CYCLE ;  
GO  
  
SELECT NEXT VALUE FOR CountBy5 AS SurveyGroup, Name FROM sys.objects ;  
GO  
```  
  
### <a name="e-generating-sequence-numbers-for-a-result-set-by-using-the-over-clause"></a>Д. Создание порядковых номеров для результирующего набора с помощью предложения OVER  
 В следующем примере предложение `OVER` используется для сортировки результирующего набора по столбцу `Name` перед добавлением столбца с порядковым номером.  
  
```  
USE AdventureWorks2012 ;  
GO  
  
CREATE SCHEMA Samples ;  
GO  
  
CREATE SEQUENCE Samples.IDLabel  
    AS tinyint  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
### <a name="f-resetting-the-sequence-number"></a>Е. Сброс порядкового номера  
 В примере Д обработаны первые 79 порядковых номеров `Samples.IDLabel`. (В используемой версии `AdventureWorks2012` может возвращаться другое число результатов.) Чтобы обработать следующие 79 порядковых номеров (от 80 до 158), выполните следующий код.  
  
```  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
 Выполните следующую инструкцию, чтобы перезапустить последовательность `Samples.IDLabel`  
  
```  
ALTER SEQUENCE Samples.IDLabel  
RESTART WITH 1 ;  
```  
  
 Снова выполните инструкцию SELECT, чтобы убедиться, что последовательность `Samples.IDLabel` перезапущена с номера 1.  
  
```  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
### <a name="g-changing-a-table-from-identity-to-sequence"></a>Ж. Перевод таблицы с идентификаторов на последовательность  
 В следующем примере создается схема и таблица, содержащая три строки. Затем в примере добавляется новый столбец и удаляется старый столбец.  
  
```  
-- Create a schema  
CREATE SCHEMA Test ;  
GO  
  
-- Create a table  
CREATE TABLE Test.Department  
    (  
        DepartmentID smallint IDENTITY(1,1) NOT NULL,  
        Name nvarchar(100) NOT NULL,  
        GroupName nvarchar(100) NOT NULL  
    CONSTRAINT PK_Department_DepartmentID PRIMARY KEY CLUSTERED   
         (DepartmentID ASC)   
    ) ;  
GO  
  
-- Insert three rows into the table  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Engineering', 'Research and Development');  
GO  
  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Tool Design', 'Research and Development');  
GO  
  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Sales', 'Sales and Marketing');  
GO  
  
-- View the table that will be changed  
SELECT * FROM Test.Department ;  
GO  
  
-- End of portion creating a sample table  
--------------------------------------------------------  
-- Add the new column that does not have the IDENTITY property  
ALTER TABLE Test.Department   
    ADD DepartmentIDNew smallint NULL  
GO  
  
-- Copy values from the old column to the new column  
UPDATE Test.Department  
    SET DepartmentIDNew = DepartmentID ;  
GO  
  
-- Drop the primary key constraint on the old column  
ALTER TABLE Test.Department  
    DROP CONSTRAINT [PK_Department_DepartmentID];  
-- Drop the old column  
ALTER TABLE Test.Department  
    DROP COLUMN DepartmentID ;  
GO  
  
-- Rename the new column to the old columns name  
EXEC sp_rename 'Test.Department.DepartmentIDNew',   
    'DepartmentID', 'COLUMN';  
GO  
  
-- Change the new column to NOT NULL  
ALTER TABLE Test.Department  
    ALTER COLUMN DepartmentID smallint NOT NULL ;  
-- Add the unique primary key constraint  
ALTER TABLE Test.Department  
    ADD CONSTRAINT PK_Department_DepartmentID PRIMARY KEY CLUSTERED   
         (DepartmentID ASC) ;  
-- Get the highest current value from the DepartmentID column   
-- and create a sequence to use with the column. (Returns 3.)  
SELECT MAX(DepartmentID) FROM Test.Department ;  
-- Use the next desired value (4) as the START WITH VALUE;  
CREATE SEQUENCE Test.DeptSeq  
    AS smallint  
    START WITH 4  
    INCREMENT BY 1 ;  
GO  
  
-- Add a default value for the DepartmentID column  
ALTER TABLE Test.Department  
    ADD CONSTRAINT DefSequence DEFAULT (NEXT VALUE FOR Test.DeptSeq)   
        FOR DepartmentID;  
GO  
  
-- View the result  
SELECT DepartmentID, Name, GroupName  
FROM Test.Department ;   
-- Test insert  
INSERT Test.Department (Name, GroupName)  
    VALUES ('Audit', 'Quality Assurance') ;  
GO  
  
-- View the result  
SELECT DepartmentID, Name, GroupName  
FROM Test.Department ;  
GO  
  
```  
  
 Инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)], использующие `SELECT *`, будут получать новый столбец последним, а не первым. Если такая обработка нежелательна, необходимо создать новую таблицу, переместить в нее данные, а затем повторно создать разрешения для новой таблицы.  
  
## <a name="related-content"></a>См. также  
 [CREATE SEQUENCE (Transact-SQL)](/sql/t-sql/statements/create-sequence-transact-sql)  
  
 [ALTER SEQUENCE (Transact-SQL)](/sql/t-sql/statements/alter-sequence-transact-sql)  
  
 [DROP SEQUENCE (Transact-SQL)](/sql/t-sql/statements/drop-sequence-transact-sql)  
  
 [Свойство IDENTITY (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql-identity-property)  
  
  
