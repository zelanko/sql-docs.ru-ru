---
title: "После УСЕЧЕНИЯ таблицы (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TRUNCATE
- TRUNCATE TABLE
- TRUNCATE_TSQL
- TRUNCATE_TABLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- row removal [SQL Server], TRUNCATE TABLE statement
- table truncating [SQL Server]
- removing rows
- TRUNCATE TABLE statement
- deleting rows
- dropping rows
ms.assetid: 3d544eed-3993-4055-983d-ea334f8c5c58
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 71f05b47a4a070e5d797a6f9ff6b5f4d88e585c5
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="truncate-table-transact-sql"></a>TRUNCATE TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Удаляет все строки из таблицы или указанные секции таблицы, не записывая в журнал удаление отдельных строк. Инструкция TRUNCATE TABLE похожа на инструкцию DELETE без предложения WHERE, однако TRUNCATE TABLE выполняется быстрее и требует меньших ресурсов системы и журналов транзакций.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
TRUNCATE TABLE   
    [ { database_name .[ schema_name ] . | schema_name . } ]  
    table_name  
    [ WITH ( PARTITIONS ( { <partition_number_expression> | <range> }   
    [ , ...n ] ) ) ]  
[ ; ]  
  
<range> ::=  
<partition_number_expression> TO <partition_number_expression>  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
TRUNCATE TABLE [ { database_name . [ schema_name ] . | schema_name . ] table_name  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных.  
  
 *schema_name*  
 Имя схемы, которой принадлежит таблица.  
  
 *имя_таблицы*  
 Имя таблицы, которая должна быть усечена, или таблицы, из которой удаляются все строки. *имя_таблицы* должно быть литералом. *имя_таблицы* не может быть **OBJECT_ID()** функции или переменной.  
  
 С помощью (СЕКЦИИ ({ \< *выражение_номера_секции*> | \< *диапазон*>} [,.. .n]))  
**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 Указывает секции для усечения или секции, из которых удаляются все строки. Если таблица не секционирована, **СЕКЦИЙ с** аргумент выдаст ошибку. Если **СЕКЦИЙ с** не указано предложение, вся таблица будет усечено.  
  
 *\<выражение_номера_секции >* можно задать следующими способами: 
  
-   Указав номер секции, например:`WITH (PARTITIONS (2))`  
  
-   Указав номера нескольких секций, разделенных запятыми, например:`WITH (PARTITIONS (1, 5))`  
  
-   Укажите диапазоны и отдельные секции, например:`WITH (PARTITIONS (2, 4, 6 TO 8))`  
  
-   *\<диапазон >* можно указать как номера секций, разделенные словом **TO**, например:`WITH (PARTITIONS (6 TO 8))`  
  
 Для усечения секционированной таблицы, таблицы и индексы должны быть выровнены (секционировать на ту же функцию секционирования).  
  
## <a name="remarks"></a>Remarks  
 Инструкция TRUNCATE TABLE обладает следующими преимуществами по сравнению с инструкцией DELETE:  
  
-   Используется меньший объем журнала транзакций.  
  
     Инструкция DELETE производит удаление по одной строке и заносит в журнал транзакций запись для каждой удаляемой строки. Инструкция TRUNCATE TABLE удаляет данные, освобождая страницы данных, используемые для хранения данных таблиц, и в журнал транзакций записывает только данные об освобождении страниц.  
  
-   Обычно используется меньшее количество блокировок.  
  
     Если инструкция DELETE выполняется с блокировкой строк, для удаления блокируется каждая строка таблицы. Инструкция TRUNCATE TABLE всегда блокирует таблицу (включая блокировку схемы (SCH-M)) и страницу, но не каждую строку.  
  
-   В таблице остается нулевое количество страниц, без исключений.  
  
     После выполнения инструкции DELETE в таблице могут все еще оставаться пустые страницы. Например, чтобы освободить пустые страницы в куче, необходима, как минимум, монопольная блокировка таблицы (LCK_M_X). Если операция удаления не использует блокировку таблицы, таблица (куча) будет содержать множество пустых страниц. В индексах после операции удаления могут оказаться пустые страницы, хотя эти страницы будут быстро освобождены процессом фоновой очистки.  
  
 Инструкция TRUNCATE TABLE удаляет все строки таблицы, но структура таблицы и ее столбцы, ограничения, индексы и т. п. сохраняются. Чтобы удалить не только данные таблицы, но и ее определение, следует использовать инструкцию DROP TABLE.  
  
 Если таблица содержит столбец идентификаторов, счетчик этого столбца сбрасывается до начального значения, определенного для этого столбца. Если начальное значение не задано, используется значение по умолчанию, равное 1. Чтобы сохранить столбец идентификаторов, используйте инструкцию DELETE.  
  
## <a name="restrictions"></a>Ограничения  
 Инструкцию TRUNCATE TABLE нельзя использовать для таблиц, для которых выполняются следующие условия:  
  
-   На таблицу ссылается ограничение FOREIGN KEY. (Таблицу, имеющую внешний ключ, ссылающийся сам на себя, можно усечь.)  
  
-   Таблица является частью индексированного представления.  
  
-   Таблица опубликована с использованием репликации транзакций или репликации слиянием.  
  
 Для таблиц с какими-либо из этих характеристик следует использовать инструкцию DELETE.  
  
 Инструкция TRUNCATE TABLE не может активировать триггер, поскольку она не записывает в журнал удаление отдельных строк. Дополнительные сведения см. в разделе [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md). 
 
 В [!INCLUDE[sssdwfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[sspdw](../../includes/sspdw-md.md)]:

- Инструкция TRUNCATE TABLE нельзя использовать в инструкции ОПИСАНИЯ.

- Инструкция TRUNCATE TABLE не выполнена внутри транзакции.
  
## <a name="truncating-large-tables"></a>Усечение больших таблиц  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет возможность удалять или усекать таблицы, имеющие более чем 128 экстентов, без удержания одновременной блокировки всех кластеров страниц, необходимых для удаления.  
  
## <a name="permissions"></a>Разрешения  
 Минимально необходимым разрешением является ALTER на *table_name*. Разрешения по умолчанию для инструкции TRUNCATE TABLE распространяются на владельца таблицы, членов предопределенной роли сервера sysadmin, а также предопределенных ролей базы данных db_owner и db_ddladmin. Эти разрешения не передаются. Тем не менее инструкцию TRUNCATE TABLE можно встроить в модуль, например в хранимую процедуру, и предоставить соответствующие разрешения этому модулю с помощью предложения EXECUTE AS.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-truncate-a-table"></a>A. Усечение таблицы  
 В ходе выполнения следующего примера удаляются все данные таблицы `JobCandidate`. Инструкции `SELECT` включены до и после инструкции `TRUNCATE TABLE` для сравнения результатов.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT COUNT(*) AS BeforeTruncateCount   
FROM HumanResources.JobCandidate;  
GO  
TRUNCATE TABLE HumanResources.JobCandidate;  
GO  
SELECT COUNT(*) AS AfterTruncateCount   
FROM HumanResources.JobCandidate;  
GO  
```  
  
### <a name="b-truncate-table-partitions"></a>Б. Усечение секций таблицы  
  
**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 В следующем примере выполняется усечение указанных секций секционированной таблицы. Синтаксис `WITH (PARTITIONS (2, 4, 6 TO 8))` задает усечение секций с номерами 2, 4, 6, 7 и 8.  
  
```sql  
TRUNCATE TABLE PartitionTable1   
WITH (PARTITIONS (2, 4, 6 TO 8));  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [Свойство IDENTITY (Transact-SQL)](../../t-sql/statements/create-table-transact-sql-identity-property.md)  
  
  

