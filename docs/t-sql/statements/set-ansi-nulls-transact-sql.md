---
title: "SET ANSI_NULLS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_ANSI_NULLS_TSQL
- ANSI_NULLS
- SET ANSI_NULLS
- ANSI_NULLS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET ANSI_NULLS statement
- not equal to operator (<>)
- ANSI_NULLS option
- equals operator (=)
- null values [SQL Server], comparison operators
- comparison operators [SQL Server], null values
ms.assetid: aae263ef-a3c7-4dae-80c2-cc901e48c755
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 285803fe112cc0370b8af6049f48846c7ba55cab
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="set-ansinulls-transact-sql"></a>SET ANSI_NULLS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Задает совместимое со стандартом ISO поведение операторов сравнения «равно» (=) и «не равно» (<>) при их использовании со значениями NULL в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
> [!IMPORTANT]  
>  В будущей версии параметр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ANSI_NULLS всегда будет иметь значение ON, а приложения, явно присваивающие ему значение OFF, будут вызывать ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
  
SET ANSI_NULLS { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_NULLS ON;  
```  
  
## <a name="remarks"></a>Замечания  
 Если параметр SET ANSI_NULLS имеет значение ON, инструкция SELECT, использующая предложение WHERE *column_name* = **NULL** возвращает нуль строк, даже при наличии значений null в *column_name*. Инструкция SELECT, использующая предложение WHERE *column_name* <> **NULL** возвращает нуль строк, даже если существуют ненулевых значений в *column_name*.  
  
 Если SET ANSI_NULLS установлено в OFF, операторы «равно» (=) и «не равно» (<>) не следуют стандарту ISO. Инструкция SELECT, использующая предложение WHERE *column_name* = **NULL** возвращает строки, имеющие значения null в *column_name*. Инструкция SELECT, использующая предложение WHERE *column_name* <> **NULL** возвращает строки, которые содержат непустые значения в столбце. Кроме того, инструкция SELECT, использующая предложение WHERE *column_name* <> *XYZ_value* возвращает все строки, которые не являются *XYZ_value* и не являются НУЛЕВЫМИ.  
  
 Если SET ANSI_NULLS равняется ON, все сравнения со значением NULL возвращают значение UNKNOWN. Когда SET ANSI_NULLS равняется OFF, сравнение любых значений с NULL вернет TRUE только в том случае, если сравниваемое значение тоже NULL. Если параметр SET ANSI_NULLS не указан, применяется значение параметра ANSI_NULLS текущей базы данных. Дополнительные сведения о параметре базы данных см. в разделе [инструкции ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
 Директива SET ANSI_NULLS ON влияет только на сравнения, в которых в качестве одного из операндов используется NULL в виде переменной или литеральной константы. Если оба операнда представляют собой столбцы или составные выражения, эта настройка не влияет на результат сравнения.  
  
 Чтобы скрипт работал в соответствии с первоначальным замыслом, вне зависимости от параметра базы данных ANSI NULLS или настроек SET ANSI_NULLS, в сравнениях, которые могут содержать значения NULL, следует использовать выражения IS NULL и IS NOT NULL.  
  
 Значение SET ANSI_NULLS должно быть равно ON при выполнении распределенных запросов.  
  
 Значение SET ANSI_NULLS также должно быть ON при создании или изменении индексов вычисляемых столбцов или индексированных представлений. Если SET ANSI_NULLS равно OFF, то при работе с таблицами, содержащими индексы вычисляемых столбцов, а также при работе с индексированными представлениями инструкции CREATE, UPDATE, INSERT и DELETE завершатся неудачно. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создаст сообщение об ошибке с перечислением всех недопустимых аргументов инструкции SET. Также при вызове инструкции SELECT в случае, если значение SET ANSI_NULLS равно OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не обрабатывает значения индексов вычисляемых столбцов или представлений и произведет выборку, словно этих индексов не существовало.  
  
> [!NOTE]  
>  ANSI_NULLS является одним из семи параметров директивы SET, которые должны быть установлены определенным образом при работе с вычисляемыми столбцами или индексированными представлениями. Параметры ANSI_PADDING, ANSI_WARNINGS, ARITHABORT, QUOTED_IDENTIFIER и CONCAT_NULL_YIELDS_NULL должны иметь значение ON, а параметр NUMERIC_ROUNDABORT — значение OFF.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при соединении автоматически устанавливают параметр ANSI_NULLS ON. Этот параметр может быть настроен в источниках данных ODBC, в атрибутах соединения ODBC или свойствах соединения OLE DB, установленных в приложении перед подключением к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию значение SET ANSI_NULLS равно OFF.  
  
 Когда параметр SET ANSI_DEFAULTS имеет значение ON, режим SET ANSI_NULLS включен.  
  
 Установка значения SET ANSI_NULLS происходит во время запуска или выполнения, но не во время синтаксического анализа.  
  
 Чтобы просмотреть текущее значение параметра для этого параметра, выполните следующий запрос.  
  
```  
DECLARE @ANSI_NULLS VARCHAR(3) = 'OFF';  
IF ( (32 & @@OPTIONS) = 32 ) SET @ANSI_NULLS = 'ON';  
SELECT @ANSI_NULLS AS ANSI_NULLS;  
  
```  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 Следующий пример иллюстрирует использование операторов «равно» (`=`) и «не равно» (`<>`) для сравнения со значениями `NULL` и не NULL в таблице. В примере также показано, `IS NULL` не подвержены `SET ANSI_NULLS` параметр.  
  
```  
-- Create table t1 and insert values.  
CREATE TABLE dbo.t1 (a INT NULL);  
INSERT INTO dbo.t1 values (NULL),(0),(1);  
GO  
  
-- Print message and perform SELECT statements.  
PRINT 'Testing default setting';  
DECLARE @varname int;   
SET @varname = NULL;  
  
SELECT a  
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to ON and test.  
PRINT 'Testing ANSI_NULLS ON';  
SET ANSI_NULLS ON;  
GO  
DECLARE @varname int;  
SET @varname = NULL  
  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to OFF and test.  
PRINT 'Testing SET ANSI_NULLS OFF';  
SET ANSI_NULLS OFF;  
GO  
DECLARE @varname int;  
SET @varname = NULL;  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- Drop table t1.  
DROP TABLE dbo.t1;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sessionproperty-transact-sql.md)   
 [= &#40; Equals &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/equals-transact-sql.md)   
 [IF... ELSE &#40; Transact-SQL &#41;](../../t-sql/language-elements/if-else-transact-sql.md)   
 [&#60; &#62; &#40; Не равно &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/not-equal-to-transact-sql-traditional.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  
  
  

