---
title: sp_indexoption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_indexoption
- sp_indexoption_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_indexoption
ms.assetid: 75f836be-d322-4a53-a45d-25bee6b42a52
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cc11f219d98e4b8018bc7d763345feb279790e13
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893239"
---
# <a name="sp_indexoption-transact-sql"></a>sp_indexoption (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Устанавливает блокирующие значения параметров для определенных пользователем кластеризованных и некластеризованных индексов или таблиц, не имеющих кластеризованного индекса.  
  
 Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] автоматически делает выбор уровня блокировки: страница, строка, таблица. Необязательно задавать эти параметры вручную. **sp_indexoption** предоставляется экспертным пользователям, знающим, что всегда подходит определенный тип блокировки.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]Вместо этого используйте [инструкцию ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_indexoption [ @IndexNamePattern = ] 'table_or_index_name'   
    , [ @OptionName = ] 'option_name'   
    , [ @OptionValue = ] 'value'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @IndexNamePattern = ] 'table_or_index_name'`Полное или неполное имя определяемой пользователем таблицы или индекса. *table_or_index_name* имеет тип **nvarchar (1035)** и не имеет значения по умолчанию. Кавычки требуются, только если указан уточненный индекс или таблица. Если указано полное имя таблицы, включая имя базы данных, в качестве последнего должно использоваться имя текущей базы данных. Если имя таблицы указано без индекса, то значение указанного аргумента устанавливается во все индексы этой таблицы и в саму таблицу, если не существует кластеризованных индексов.  
  
`[ @OptionName = ] 'option_name'`Имя параметра индекса. *option_name* имеет тип **varchar (35)** и не имеет значения по умолчанию. *option_name* может иметь одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**AllowRowLocks**|Если TRUE, то допустимы блокировки строк при доступе к индексу. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет, когда используются блокировки строки. Если FALSE, то блокировка строк не используется. Значение по умолчанию — TRUE.|  
|**AllowPageLocks**|Если TRUE, то допустимы блокировки страниц при доступе к индексу. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет, когда используются блокировки страниц. Если FALSE, то блокировка страниц не используется. Значение по умолчанию — TRUE.|  
|**DisAllowRowLocks**|Если TRUE, то блокировка строк не используется. Если FALSE, то допустимы блокировки строк при доступе к индексу. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет, когда используются блокировки строки.|  
|**DisAllowPageLocks**|Если TRUE, то блокировка страниц не используется. Если FALSE, то допустимы блокировки страниц при доступе к индексу. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет, когда используются блокировки страниц.|  
  
`[ @OptionValue = ] 'value'`Указывает, включен ли параметр *option_name* (true, on, yes или 1) или отключен (false, Off, No или 0). *значение* имеет тип **varchar (12)** и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или больше чем 0 (неуспешное завершение)  
  
## <a name="remarks"></a>Комментарии  
 XML-индексы не поддерживаются. Если указаны XML-индексы, или имя таблицы указано без имени индекса, и таблица содержит XML-индекс, то инструкция завершается ошибкой. Чтобы задать эти параметры, используйте [инструкцию ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) .  
  
 Чтобы отобразить текущие свойства блокировки строк и страниц, используйте [INDEXPROPERTY](../../t-sql/functions/indexproperty-transact-sql.md) или представление каталога [sys. indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) .  
  
-   Блокировки на уровне строк, страниц и таблиц разрешены при доступе к индексу, если **AllowRowLocks** = true или **DisAllowRowLocks** = false, а **AllowPageLocks** = true или **DisAllowPageLocks** = false. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] выбирает соответствующую блокировку и может повышать уровень с блокировки строки или страницы до блокировки таблицы.  
  
 Только блокировка на уровне таблицы разрешена при доступе к индексу, если **AllowRowLocks** = false или **DisAllowRowLocks** = true и **AllowPageLocks** = false или **DisAllowPageLocks** = true.  
  
 Если имя таблицы указано без индекса, то настройка применяется ко всем индексам этой таблицы. Если базовая таблица не имеет кластеризованного индекса (т.е. имеется куча), то настройки применяются следующим образом:  
  
-   Если для **AllowRowLocks** или **DisAllowRowLocks** задано значение true или false, то параметр применяется к куче и любым связанным некластеризованным индексам.  
  
-   Если параметр **AllowPageLocks** имеет значение true или **DISALLOWPAGELOCKS** имеет значение false, параметр применяется к куче и всем связанным некластеризованным индексам.  
  
-   Если параметр **AllowPageLocks** имеет значение false или **DISALLOWPAGELOCKS** имеет значение true, то этот параметр полностью применяется к некластеризованным индексам. Таким образом, все блокировки страниц не допускаются для некластеризованных индексов. В куче, для страницы недопустимы только совмещаемая (S), обновления (U) и монопольная (X) блокировки. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] может запросить намеренную блокировку страницы (IS, IU или IX) для внутренних целей.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение ALTER на таблицу.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-setting-an-option-on-a-specific-index"></a>A. Настройка параметра на указанный индекс  
 В следующем примере запрещена Блокировка страниц для `IX_Customer_TerritoryID` индекса в `Customer` таблице.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_indexoption N'Sales.Customer.IX_Customer_TerritoryID',  
    N'disallowpagelocks', TRUE;  
```  
  
### <a name="b-setting-an-option-on-all-indexes-on-a-table"></a>Б. Настройка параметра на все индексы таблицы  
 Следующий пример демонстрирует блокировки строк на все индексы, связанные с таблицей `Product`. Представление каталога `sys.indexes` запрашивается до и после выполнения процедуры `sp_indexoption` для демонстрации результата выполнения инструкции.  
  
```sql  
USE AdventureWorks2012;  
GO  
--Display the current row and page lock options for all indexes on the table.  
SELECT name, type_desc, allow_row_locks, allow_page_locks   
FROM sys.indexes  
WHERE object_id = OBJECT_ID(N'Production.Product');  
GO  
-- Set the disallowrowlocks option on the Product table.   
EXEC sp_indexoption N'Production.Product',  
    N'disallowrowlocks', TRUE;  
GO  
--Verify the row and page lock options for all indexes on the table.  
SELECT name, type_desc, allow_row_locks, allow_page_locks   
FROM sys.indexes  
WHERE object_id = OBJECT_ID(N'Production.Product');  
GO  
```  
  
### <a name="c-setting-an-option-on-a-table-with-no-clustered-index"></a>В. Настройка параметра на таблицу, не имеющую кластеризованного индекса  
 Следующий пример запрещает блокировки страниц на таблицу, не имеющую кластеризованного индекса (куча). `sys.indexes`Представление каталога запрашивается до и после `sp_indexoption` выполнения процедуры для отображения результатов выполнения инструкции.  
  
```sql  
USE AdventureWorks2012;  
GO  
--Display the current row and page lock options of the table.   
SELECT OBJECT_NAME (object_id) AS [Table], type_desc, allow_row_locks, allow_page_locks   
FROM sys.indexes  
WHERE OBJECT_NAME (object_id) = N'DatabaseLog';  
GO  
-- Set the disallowpagelocks option on the table.   
EXEC sp_indexoption DatabaseLog,  
    N'disallowpagelocks', TRUE;  
GO  
--Verify the row and page lock settings of the table.  
SELECT OBJECT_NAME (object_id) AS [Table], allow_row_locks, allow_page_locks   
FROM sys.indexes  
WHERE OBJECT_NAME (object_id) = N'DatabaseLog';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
  
