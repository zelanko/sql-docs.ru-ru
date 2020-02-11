---
title: Параметры сортировки и кодовые страницы | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c626dcac-0474-432d-acc0-cfa643345372
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1969a3e30b31a21c380559a3e8898f87eb8848b1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62786739"
---
# <a name="collations-and-code-pages"></a>Параметры сортировки и кодовые страницы
  
  [!INCLUDE[hek_2](../includes/hek-2-md.md)] имеет ограничения на поддерживаемые кодовые страницы для столбцов (var)char в оптимизированных для памяти таблицах и на параметры сортировки, используемые в индексах и скомпилированные в собственном коде в хранимых процедурах.  
  
 Кодовая страница для значений a (var)char определяет сопоставление символов и байтовое представление, которое хранится в таблице. Например, в кодовой странице 1252 (Latin1 Windows; по умолчанию [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]) символ «a» соответствует байту 0x61.  
  
 Кодовая страница значения (var)char определяется параметрами сортировки, связанными со значением. Например, параметры сортировки SQL_Latin1_General_CP1_CI_AS имеют связанную кодовую страницу 1252.  
  
 Параметры сортировки значения наследуются от параметров сортировки базы данных или могут быть заданы явным образом с помощью ключевого слова COLLATE. Параметры сортировки базы данных нельзя изменить, если база данных содержит таблицы, оптимизированные для памяти, или скомпилированные хранимые процедуры. Следующий пример устанавливает параметры сортировки базы данных и создает таблицу, которая содержит столбец с иными параметрами сортировки. База данных использует параметры сортировки Latin без учета регистра.  
  
 Индексы могут создаваться только для столбцов строкового типа, если они используют параметры сортировки BIN2. Переменная LastName использует параметры сортировки BIN2. FirstName использует значение по умолчанию для базы данных CI_AS (без учета регистра, с учетом диакритических знаков).  
  
> [!IMPORTANT]  
>  Нельзя использовать функции упорядочивания и группировки в столбцах строк индекса, в которых не используются параметры сортировки BIN2.  
  
```sql  
CREATE DATABASE IMOLTP  
  
ALTER DATABASE IMOLTP ADD FILEGROUP IMOLTP_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE IMOLTP ADD FILE( NAME = 'IMOLTP_mod' , FILENAME = 'c:\data\IMOLTP_mod') TO FILEGROUP IMOLTP_mod;  
--GO  
  
--  set the database collations  
ALTER DATABASE IMOLTP COLLATE Latin1_General_100_CI_AS  
GO  
  
--  
USE IMOLTP   
GO  
  
-- create a table with collation  
CREATE TABLE Employees (  
  EmployeeID int NOT NULL ,   
  LastName nvarchar(20) COLLATE Latin1_General_100_BIN2 NOT NULL INDEX IX_LastName NONCLUSTERED,   
  FirstName nvarchar(10) NOT NULL ,  
  CONSTRAINT PK_Employees PRIMARY KEY NONCLUSTERED HASH(EmployeeID)  WITH (BUCKET_COUNT=1024)  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY=SCHEMA_AND_DATA)  
GO  
```  
  
 Следующие ограничения применяются к таблицам, оптимизированным для памяти, и хранимым процедурам, скомпилированным в собственном коде:  
  
-   Столбцы (var)char в таблицах, оптимизированных для памяти, должны использовать параметры сортировки кодовой страницы 1252. Данное ограничение не относится к столбцам n(var)char. Следующий код извлекает все параметры сортировки 1252:  
  
    ```sql  
    -- all supported collations for (var)char columns in memory-optimized tables  
    select * from sys.fn_helpcollations()  
    where collationproperty(name, 'codepage') = 1252;  
    ```  
  
     Если необходимо сохранять символы, отличные от латиницы, используйте столбцы n(var)char.  
  
-   Индексы столбцов (n)var(char) могут быть определены только с параметрами сортировки BIN2 (см. первый пример). Следующий запрос получает все поддерживаемые параметры сортировки BIN2:  
  
    ```sql  
    -- all supported collations for indexes on memory-optimized tables and   
    -- comparison/sorting in natively compiled stored procedures  
    select * from sys.fn_helpcollations() where name like '%BIN2'  
    ```  
  
     Если доступ к таблице осуществляется через интерпретируемый [!INCLUDE[tsql](../includes/tsql-md.md)], можно использовать ключевое слово `COLLATE` для изменения параметров сортировки с выражениями или операциями сортировки. Образец этого см. в последнем примере.  
  
-   Скомпилированные хранимые процедуры не могут использовать параметры, локальные переменные и строковые константы типа (var)char, если параметры сортировки базы данных отличаются от кодовой страницы 1252.  
  
-   Все выражения и операции сортировки в хранимых процедурах, скомпилированных в собственном коде, должны использовать параметры сортировки BIN2. Подразумевается, что все сравнения и операции сортировки создаются на основе кодовых точек символов Юникода (двоичных представлений). Например, все сортировки выполняются с учетом регистра («Z» находится перед «a»). При необходимости используйте интерпретируемый [!INCLUDE[tsql](../includes/tsql-md.md)] без учета регистра для сортировки и сравнения.  
  
-   Усечение данных UTF-16, неподдерживаемых внутри хранимых процедур, скомпилированных в собственном коде. Это означает**, что значения n (VAR) char (*n*) не могут быть преобразованы в тип n (VAR) char (*i*), если ** < параметры сортировки имеют _SC свойство. Например, следующее выражение не поддерживается:  
  
    ```sql  
    -- column definition using an _SC collation  
     c2 nvarchar(200) collate Latin1_General_100_CS_AS_SC not null   
    -- assignment to a smaller variable, requiring truncation  
     declare @c2 nvarchar(100) = '';  
     select @c2 = c2  
    ```  
  
     Функции обработки строк, такие как LEN, SUBSTRING, LTRIM и RTRIM, с данными UTF-16 не поддерживаются в хранимых процедурах, скомпилированных в собственном коде. Нельзя использовать эти функции для значений типа n(var)char с параметрами сортировки _SC.  
  
     Объявляйте переменные с типами, объем памяти которых позволит избежать усечения.  
  
 В следующем примере показаны некоторые последствия и решения для ограничений параметров сортировки в OLTP в памяти. В примере используется приведенная выше таблица Employees. В этом примере список всех сотрудников. Обратите внимание, что для LastName вследствие параметров двоичной сортировки имена в верхнем регистре варианта сортируются раньше имен в нижнем регистре. Поэтому «Thomas» предшествует «nolan», так как символы в верхнем регистре имеют более низкие кодовые точки. FirstName имеет параметры сортировки без учета регистра. Поэтому сортировка выполняется по буквам алфавита, а не кодовым точкам символов.  
  
```sql  
-- insert a number of values  
INSERT Employees VALUES (1,'thomas', 'john')  
INSERT Employees VALUES (2,'Thomas', 'rupert')  
INSERT Employees VALUES (3,'Thomas', 'Jack')  
INSERT Employees VALUES (4,'Thomas', 'annie')  
INSERT Employees VALUES (5,'nolan', 'John')  
GO  
  
-- ===========  
SELECT EmployeeID, LastName, FirstName FROM Employees  
ORDER BY LastName, FirstName  
GO  
  
-- ===========  
-- specify collation: sorting uses case-insensitive collation, thus 'nolan' comes before 'Thomas'  
SELECT * FROM Employees  
ORDER BY LastName COLLATE Latin1_General_100_CI_AS, FirstName  
GO  
  
-- ===========  
-- retrieve employee by Name  
-- must use BIN2 collation for comparison in natively compiled stored procedures  
CREATE PROCEDURE usp_EmployeeByName @LastName nvarchar(20), @FirstName nvarchar(10)  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
  LANGUAGE = N'us_english'  
)  
  SELECT EmployeeID, LastName, FirstName FROM dbo.Employees  
  WHERE   
    LastName = @LastName AND  
    FirstName COLLATE Latin1_General_100_BIN2 = @FirstName  
  
END  
GO  
  
-- this does not return any rows, as EmployeeID 1 has first name 'john', which is not equal to 'John' in a binary collation  
EXEC usp_EmployeeByName 'thomas', 'John'  
  
-- this retrieves EmployeeID 1  
EXEC usp_EmployeeByName 'thomas', 'john'  
```  
  
## <a name="see-also"></a>См. также:  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
