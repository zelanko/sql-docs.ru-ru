---
title: "SET QUOTED_IDENTIFIER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 02/03/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- QUOTED_IDENTIFIER_TSQL
- SET_QUOTED_IDENTIFIER_TSQL
- SET QUOTED_IDENTIFIER
- QUOTED_IDENTIFIER
dev_langs: TSQL
helpviewer_keywords:
- delimited identifiers [SQL Server]
- identifiers [SQL Server], delimited
- QUOTED_IDENTIFIER option
- quoted identifiers
- ISO delimited identifiers rules
- SET QUOTED_IDENTIFIER statement
ms.assetid: 10f66b71-9241-4a3a-9292-455ae7252565
caps.latest.revision: "48"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 207cf23523a315a0a4a4bc923ae9e52d7b82f8b0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="set-quotedidentifier-transact-sql"></a>SET QUOTED_IDENTIFIER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Заставляет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следовать правилам ISO относительно разделения кавычками идентификаторов и строк-литералов. Идентификаторы, заключенные в двойные кавычки, могут быть либо зарезервированными ключевыми словами [!INCLUDE[tsql](../../includes/tsql-md.md)], либо могут содержать символы, которые обычно запрещены правилами синтаксиса для идентификаторов [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET QUOTED_IDENTIFIER { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET QUOTED_IDENTIFIER ON   
```  
  
## <a name="remarks"></a>Замечания  
 Если параметру SET QUOTED_IDENTIFIER присвоено значение ON, то идентификаторы можно заключать в двойные кавычки и литералы должны быть разделены одинарными кавычками. Если параметру SET QUOTED_IDENTIFIER присвоено значение OFF, то идентификаторы нельзя заключать в кавычки и должны учитываться все правила [!INCLUDE[tsql](../../includes/tsql-md.md)] для идентификаторов. Дополнительные сведения см. в разделе [Database Identifiers](../../relational-databases/databases/database-identifiers.md). Литералы могут разделяться как одинарными, так и двойными кавычками.  
  
 Если параметру SET QUOTED_IDENTIFIER присвоено значение ON (по умолчанию), то все строки, разделенные двойными кавычками, рассматриваются как идентификаторы объектов. Такие образом, заключенные в кавычки идентификаторы не должны удовлетворять правилам языка [!INCLUDE[tsql](../../includes/tsql-md.md)] для идентификаторов. Они могут быть зарезервированными ключевыми словами, а также могут содержать символы, обычно запрещенные для идентификаторов языка [!INCLUDE[tsql](../../includes/tsql-md.md)]. Выражения со строками-литералами нельзя заключать в двойные кавычки; для этих целей необходимо использовать одинарные кавычки. Если одинарная кавычка (**"**) входит в состав строки-литерала, он может быть представлена двумя одинарными кавычками (**»**). Если в именах объектов базы данных используются зарезервированные ключевые слова, то параметру SET QUOTED_IDENTIFIER должно быть присвоено значение ON.  
  
 Если параметру SET QUOTED_IDENTIFIER присвоено значение OFF, строки-литералы в выражениях можно разделять либо одинарными, либо двойными кавычками. Если строки-литералы разделяются двойными кавычками, то в строке могут содержаться внедренные одинарные кавычки, такие как апострофы.  
  
 При создании или изменении индексов в вычисляемых столбцах или индексированных представлениях параметру SET QUOTED_IDENTIFIER должно быть присвоено значение OFF. Если параметр SET QUOTED_IDENTIFIER имеет значение OFF, то в таблицах с индексами инструкции CREATE, UPDATE, INSERT и DELETE в вычисляемых столбцах или индексированных представлениях не будут работать. Дополнительные сведения о необходимых УСТАНОВКАХ параметров SET для индексированных представлений и индексов на вычисляемых столбцах см. в разделе «Вопросы при вы использования операторов SET» в [инструкции SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md).  
  
 SET QUOTED_IDENTIFIER должен иметь значение ON при создании отфильтрованного индекса.  
  
 SET QUOTED_IDENTIFIER должно быть присвоено значение ON при вызове методов типа данных XML.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при соединении автоматически устанавливают параметр QUOTED_IDENTIFIER ON. Это может быть настроено в источниках данных ODBC, в атрибутах соединения ODBC или свойствах соединения OLE DB. По умолчанию параметр SET QUOTED_IDENTIFIER имеет значение OFF для соединений из приложений DB-Library.  
  
 После создания таблицы параметр QUOTED IDENTIFIER всегда записывается в метаданные таблицы со значением ON, даже если он был установлен в OFF при создании таблицы.  
  
 Когда создается хранимая процедура, параметры SET QUOTED_IDENTIFIER и SET ANSI_NULLS фиксируются и используются для последующих вызовов этой хранимой процедуры.  
  
 При выполнении операций внутри хранимой процедуры значение SET QUOTED_IDENTIFIER не меняется.  
  
 Если параметр SET ANSI_DEFAULTS имеет значение ON, параметр SET QUOTED_IDENTIFIER включается.  
  
 Также параметр SET QUOTED_IDENTIFIER связан с параметром QUOTED_IDENTIFER инструкции ALTER DATABASE. Дополнительные сведения о параметрах базы данных см. в разделе [инструкции ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
 SET QUOTED_IDENTIFIER имеет вступает в силу во время синтаксического анализа и влияет только на синтаксический анализ, не для выполнения запроса.  
  
 Для верхнего уровня нерегламентированных пакетных начинается анализ с помощью текущего параметра сеанса для QUOTED_IDENTIFIER.  При анализе пакета все вхождения SET QUOTED_IDENTIFIER изменить синтаксического анализа поведение из этой точки в и сохранить этот параметр для сеанса.  Поэтому после синтаксического анализа и выполнения пакета будет установить параметр QUOTED_IDENTIFER сеанса в соответствии с последнего вхождения значения SET QUOTED_IDENTIFIER в пакете.  
 Статический SQL в хранимой процедуре анализируется с использованием параметра QUOTED_IDENTIFIER в силе для раздела, создании или изменении хранимой процедуры.  Параметр SET QUOTED_IDENTIFIER не оказывает влияния в тексте хранимой процедуры в виде статических SQL.  
  
 Для вложенных пакета с помощью процедуры sp_executesql или exec() начинается анализ с помощью параметра QUOTED_IDENTIFIER сеанса.  Если внутри хранимой процедуры, синтаксический анализ запускается с помощью хранимой процедуры, параметр QUOTED_IDENTIFIER вложенных пакет.  Как вложенные пакетные анализируется все вхождения SET QUOTED_IDENTIFIER приведет к изменению поведения синтаксического анализа с этого момента на, но параметр QUOTED_IDENTIFIER сеанса не будут обновлены.  
  
 С помощью скобок, **[** и **]**, в качестве разделителей идентификаторов параметр QUOTED_IDENTIFIER не влияет.  
  
 Чтобы просмотреть текущее значение параметра для этого параметра, выполните следующий запрос.  
  
```  
DECLARE @QUOTED_IDENTIFIER VARCHAR(3) = 'OFF';  
IF ( (256 & @@OPTIONS) = 256 ) SET @QUOTED_IDENTIFIER = 'ON';  
SELECT @QUOTED_IDENTIFIER AS QUOTED_IDENTIFIER;  
  
```  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-the-quoted-identifier-setting-and-reserved-word-object-names"></a>A. Использование режима заключенных в кавычки идентификаторов и имен объектов, состоящих из зарезервированных слов  
 В следующем примере показано, что параметр `SET QUOTED_IDENTIFIER` должен иметь значение `ON`, а ключевые слова в именах таблиц должны быть заключены в двойные кавычки, чтобы создать и использовать объекты, содержащие в именах зарезервированные ключевые слова.  
  
```  
SET QUOTED_IDENTIFIER OFF  
GO  
-- An attempt to create a table with a reserved keyword as a name  
-- should fail.  
CREATE TABLE "select" ("identity" INT IDENTITY NOT NULL, "order" INT NOT NULL);  
GO  
  
SET QUOTED_IDENTIFIER ON;  
GO  
  
-- Will succeed.  
CREATE TABLE "select" ("identity" INT IDENTITY NOT NULL, "order" INT NOT NULL);  
GO  
  
SELECT "identity","order"   
FROM "select"  
ORDER BY "order";  
GO  
  
DROP TABLE "SELECT";  
GO  
  
SET QUOTED_IDENTIFIER OFF;  
GO  
```  
  
### <a name="b-using-the-quoted-identifier-setting-with-single-and-double-quotation-marks"></a>Б. Использование настроек заключенного в кавычки идентификатора с двойными и одинарными кавычками  
 В этом примере показано, как используются двойные и одинарные кавычки в строковых выражениях, если параметру `SET QUOTED_IDENTIFIER` присвоено значение `ON` и значение `OFF`.  
  
```  
SET QUOTED_IDENTIFIER OFF;  
GO  
USE AdventureWorks2012;  
IF EXISTS(SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
      WHERE TABLE_NAME = 'Test')  
   DROP TABLE dbo.Test;  
GO  
USE AdventureWorks2012;  
CREATE TABLE dbo.Test (ID INT, String VARCHAR(30)) ;  
GO  
  
-- Literal strings can be in single or double quotation marks.  
INSERT INTO dbo.Test VALUES (1, "'Text in single quotes'");  
INSERT INTO dbo.Test VALUES (2, '''Text in single quotes''');  
INSERT INTO dbo.Test VALUES (3, 'Text with 2 '''' single quotes');  
INSERT INTO dbo.Test VALUES (4, '"Text in double quotes"');  
INSERT INTO dbo.Test VALUES (5, """Text in double quotes""");  
INSERT INTO dbo.Test VALUES (6, "Text with 2 """" double quotes");  
GO  
  
SET QUOTED_IDENTIFIER ON;  
GO  
  
-- Strings inside double quotation marks are now treated   
-- as object names, so they cannot be used for literals.  
INSERT INTO dbo."Test" VALUES (7, 'Text with a single '' quote');  
GO  
  
-- Object identifiers do not have to be in double quotation marks  
-- if they are not reserved keywords.  
SELECT ID, String   
FROM dbo.Test;  
GO  
  
DROP TABLE dbo.Test;  
GO  
  
SET QUOTED_IDENTIFIER OFF;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ID          String 
 ----------- ------------------------------ 
 1           'Text in single quotes' 
 2           'Text in single quotes' 
 3           Text with 2 '' single quotes 
 4           "Text in double quotes" 
 5           "Text in double quotes" 
 6           Text with 2 "" double quotes 
 7           Text with a single ' quote
 ```  
  
## <a name="see-also"></a>См. также:  
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [CREATE DEFAULT (Transact-SQL)](../../t-sql/statements/create-default-transact-sql.md)   
 [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE RULE (Transact-SQL)](../../t-sql/statements/create-rule-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [CREATE VIEW (Transact-SQL)](../../t-sql/statements/create-view-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [процедура sp_rename &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)  
  
  
