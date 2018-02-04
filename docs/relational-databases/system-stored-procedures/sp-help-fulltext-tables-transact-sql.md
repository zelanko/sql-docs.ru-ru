---
title: "sp_help_fulltext_tables (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_tables
- sp_help_fulltext_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_tables
ms.assetid: 86e24a5f-a869-43f6-b83e-c52b7b01b5ff
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5398d465c2368ae216e05aa3232c5c2dcd1790f8
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sphelpfulltexttables-transact-sql"></a>sp_help_fulltext_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает список таблиц, зарегистрированных для полнотекстового индексирования.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте **sys.fulltext_indexes** представления каталога. Дополнительные сведения см. в разделе [sys.fulltext_indexes &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_fulltext_tables [ [ @fulltext_catalog_name = ] 'fulltext_catalog_name' ]   
     [ , [ @table_name = ] 'table_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@fulltext_catalog_name=**] **'***fulltext_catalog_name***'**  
 Имя полнотекстового каталога. *fulltext_catalog_name* — **sysname**, значение по умолчанию NULL. Если *fulltext_catalog_name* опущен или имеет значение NULL, возвращаются все таблицы индексированных полнотекстового, связанные с базой данных. Если *fulltext_catalog_name* указан, но *table_name* опущен или имеет значение NULL, данные полнотекстового индекса извлекаются для каждого полнотекстового индексированного таблицы, связанной с этим каталогом. Если оба *fulltext_catalog_name* и *table_name* указано, возвращается строка, если *table_name* связан с *fulltext_catalog_name*; в противном случае возникает ошибка.  
  
 [ **@table_name=**] **'***table_name***'**  
 Одно- или двухкомпонентное имя таблицы, для которой запрашиваются полнотекстовые метаданные. *имя_таблицы* — **nvarchar(517)**, значение по умолчанию NULL. Если только *table_name* указано, только строки, относящиеся к *table_name* возвращается.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|Владелец таблицы. Это имя пользователя базы данных, создавшего таблицу.|  
|**TABLE_NAME**|**sysname**|Имя таблицы.|  
|**FULLTEXT_KEY_INDEX_NAME**|**sysname**|Индекс, налагающий ограничение UNIQUE на столбец, помеченный как уникальный ключевой столбец.|  
|**FULLTEXT_KEY_COLID**|**int**|Идентификатор столбца уникального индекса, задаваемого параметром FULLTEXT_KEY_NAME.|  
|**FULLTEXT_INDEX_ACTIVE**|**int**|Указывает, можно ли использовать в запросах столбцы, помеченные для полнотекстового индексирования в этой таблице.<br /><br /> 0 = неактивно.<br /><br /> 1= активно.|  
|**FULLTEXT_CATALOG_NAME**|**sysname**|Полнотекстовый каталог, в котором хранятся данные полнотекстового индекса.|  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения на выполнение предоставлены членам роли **public** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как вернуть имена таблиц с полнотекстовым индексом, связанных с полнотекстовым каталогом `Cat_Desc`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_help_fulltext_tables 'Cat_Desc';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [INDEXPROPERTY (Transact-SQL)](../../t-sql/functions/indexproperty-transact-sql.md)   
 [OBJECTPROPERTY (Transact-SQL)](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_fulltext_table &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-fulltext-table-transact-sql.md)   
 [sp_help_fulltext_tables_cursor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-cursor-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
