---
title: sp_fulltext_table (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_fulltext_table_TSQL
- sp_fulltext_table
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_table
ms.assetid: a765f311-07fc-4af3-b74c-e9a027fbecce
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b6c759bd422ae815a284ae2cd14bc8b1861281ad
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37995611"
---
# <a name="spfulltexttable-transact-sql"></a>sp_fulltext_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Отмечает таблицу для полнотекстового индексирования или снимает эту отметку.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [CREATE FULLTEXT INDEX](../../t-sql/statements/create-fulltext-index-transact-sql.md), [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md), и [DROP FULLTEXT INDEX](../../t-sql/statements/drop-fulltext-index-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_fulltext_table   
   [ @tabname= ] 'qualified_table_name'           
   , [ @action= ] 'action'   
   [   
   , [ @ftcat= ] 'fulltext_catalog_name'           
   , [ @keyname= ] 'unique_index_name'   
   ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@tabname=**] **"***таблицы не собирались***"**  
 Имя таблицы, состоящее из одной или двух частей. Таблица должна существовать в текущей базе данных. *таблицы не собирались* — **nvarchar(517)**, не имеет значения по умолчанию.  
  
 [  **@action=**] **"***действие***"**  
 Действие, которое должно быть выполнено. *Действие* — **nvarchar(50)**, по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Создание**|Создает метаданные для полнотекстового индекса для таблицы, указанной *таблицы не собирались* и указывает, что данные полнотекстового индекса для этой таблицы должны находиться в *fulltext_catalog_name*. Это действие также определяет использование *unique_index_name* в качестве ключевого столбца полнотекстового поиска. Этот уникальный индекс уже должен существовать и быть определенным для одного из столбцов таблицы.<br /><br /> Полнотекстовый поиск по этой таблице не будет выполняться, пока полнотекстовый каталог не будет заполнен.|  
|**Drop**|Удаляет метаданные для полнотекстового индекса для *таблицы не собирались*. Если при этом производится полнотекстовое индексирование, оно автоматически прекращается перед удалением метаданных. Перед удалением полнотекстового индекса необязательно удалять столбцы.|  
|**Activate**|Активирует возможность данные полнотекстового индекса необходимо собирать для *таблицы не собирались*, после деактивации. Для активации в полнотекстовый индекс должен входить хотя бы один столбец.<br /><br /> Полнотекстовый индекс автоматически становится активным (для заполнения) как только добавляется первый столбец для индексирования. Если из индекса удален последний столбец, индекс становится неактивным. Если включено отслеживание изменений, неактивный индекс начинает новое заполнение.<br /><br /> Обратите внимание, что фактического заполнения полнотекстового индекса, но простая регистрация таблицы в полнотекстовый каталог в файловой системе, что строки из *таблицы не собирались* могут быть получены во время следующего полнотекстового индекса заполнение.|  
|**Деактивация**|Деактивирует полнотекстовый индекс для *таблицы не собирались* таким образом, чтобы данные полнотекстового индекса можно собирать больше не для *таблицы не собирались*. Метаданные полнотекстового индекса сохраняются, и индексирование может быть активировано снова.<br /><br /> Если включено отслеживание изменений, деактивация активного индекса закрепляет состояние индекса: любое текущее заполнение прекращается, и новые изменения в индекс не попадают.|  
|**start_change_tracking**|Начинает добавочное заполнение полнотекстового индекса. Если у таблицы нет отметки времени, начать полное заполнение полнотекстового индекса. Начать отслеживать изменения таблицы.<br /><br /> Отслеживание изменений для полнотекстового поиска не учитывает любые операции WRITETEXT или UPDATETEXT, выполняемые на индексированных столбцах полнотекстового поиска, которые имеют тип **изображение**, **текст**, или **ntext**.|  
|**stop_change_tracking**|Прекращает отслеживать изменения таблицы.|  
|**update_index**|Внести текущий набор изменений таблицы в полнотекстовый индекс.|  
|**start_background_updateindex**|Начинает внесение изменений таблицы в полнотекстовый индекс по мере их появления.|  
|**stop_background_updateindex**|Прекращает внесение изменений таблицы в полнотекстовый индекс по мере их появления.|  
|**start_full**|Выполняет полное заполнение полнотекстового индекса.|  
|**start_incremental**|Начинает добавочное заполнение полнотекстового индекса.|  
|**Остановить**|Прекращает добавочное заполнение.|  
  
 [ **@ftcat=**] **'***fulltext_catalog_name***'**  
 — Это имя допустимой, существующий полнотекстовый каталог для **создать** действие. Для всех других действий этот параметр должен быть равен NULL. *fulltext_catalog_name* — **sysname**, значение по умолчанию NULL.  
  
 [ **@keyname=**] **'***unique_index_name***'**  
 Является индексом допустимым один ключевой столбец, уникальным не допускающий значения NULL в *таблицы не собирались* для **создать** действие. Для всех других действий этот параметр должен быть равен NULL. *unique_index_name* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 После деактивации полнотекстового индекса для конкретной таблицы существующий полнотекстовый индекс остается до следующего полного заполнения; Тем не менее, этот индекс не используется из-за [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] блокирует запросы к деактивированным таблицам.  
  
 Если таблица активирована вновь, но индекс не заполняется снова, старый индекс доступен для запросов к остававшимся, но не новым столбцам, для которых включено полнотекстовое индексирование. Данные из удаленных столбцов используются в запросах поиска по всем столбцам полнотекстового индекса.  
  
 После таблицы был определен для полнотекстового индексирования, переключение полнотекстового уникального ключевого столбца из одного типа в другой, либо путем изменения типа данных этого столбца или изменения полнотекстового уникального ключа из одного столбца в другой, не начать новое полное заполнение может привести к сбою при последующем запросе и возвращает сообщение об ошибке: «преобразование в тип *data_type* не удалась для значения ключа полнотекстового поиска *key_value*.» Чтобы избежать этого, удалите определение полнотекстового поиска для этой таблицы с помощью **drop** действие **sp_fulltext_table** и переопределите его с помощью **sp_fulltext_table** и **sp_fulltext_column**.  
  
 Полнотекстовый ключевой столбец должен содержать значения размером не более 900 байт. Из соображений производительности рекомендуется делать размер ключевого столбца как можно меньшим.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера, **db_owner** и **db_ddladmin** предопределенной роли базы данных или пользователь с разрешениями ссылки на полнотекстовый каталог могут выполнение **sp_fulltext_table**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-enabling-a-table-for-full-text-indexing"></a>A. Включение полнотекстового индексирования таблицы  
 В следующем примере создаются метаданные полнотекстового индекса для таблицы `Document` базы данных `AdventureWorks`. `Cat_Desc` — полнотекстовый каталог. `PK_Document_DocumentID` — уникальный индекс по одиночному столбцу таблицы `Document`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_table 'Production.Document', 'create', 'Cat_Desc', 'PK_Document_DocumentID';  
--Add some columns  
EXEC sp_fulltext_column 'Production.Document','DocumentSummary','add';  
-- Activate the full-text index  
EXEC sp_fulltext_table 'Production.Document','activate';  
GO  
```  
  
### <a name="b-activating-and-propagating-track-changes"></a>Б. Активация отслеживания изменений и их внесение в индекс  
 В следующем примере будет начато отслеживание изменений таблицы и их внесение в полнотекстовый индекс по мере появления.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_table 'Production.Document', 'Start_change_tracking';  
EXEC sp_fulltext_table 'Production.Document', 'Start_background_updateindex';  
GO  
```  
  
### <a name="c-removing-a-full-text-index"></a>В. Удаление полнотекстового индекса  
 В этом примере удаляются метаданные полнотекстового индекса таблицы `Document` базы данных `AdventureWorks`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_table 'Production.Document', 'drop';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [INDEXPROPERTY (Transact-SQL)](../../t-sql/functions/indexproperty-transact-sql.md)   
 [OBJECTPROPERTY (Transact-SQL)](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_help_fulltext_tables &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-transact-sql.md)   
 [sp_help_fulltext_tables_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-cursor-transact-sql.md)   
 [sp_helpindex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Компонент Full-Text Search и семантический поиск хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  
