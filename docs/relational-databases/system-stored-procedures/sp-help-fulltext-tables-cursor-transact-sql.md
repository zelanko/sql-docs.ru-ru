---
title: "sp_help_fulltext_tables_cursor (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_tables_cursor
- sp_help_fulltext_tables_cursor_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_fulltext_tables_cursor
ms.assetid: 155791eb-8832-4596-8487-7fc70dfba5b9
caps.latest.revision: "25"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef0fa0c119c293e085d68124ee44dee378fb99d1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sphelpfulltexttablescursor-transact-sql"></a>sp_help_fulltext_tables_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Использует курсор для возврата списка таблиц, которые зарегистрированы для полнотекстового индексирования.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Используйте новую **sys.fulltext_indexes** представления каталога. Дополнительные сведения см. в разделе [sys.fulltext_indexes &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md).  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (от[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_fulltext_tables_cursor [ @cursor_return = ] @cursor_variable OUTPUT   
     [ , [ @fulltext_catalog_name = ] 'fulltext_catalog_name' ]   
     [ , [ @table_name = ] 'table_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@cursor_return=** ]  *@cursor_variable*  ВЫХОДНЫХ ДАННЫХ  
 Выходная переменная типа **курсор**. Этот курсор является динамическим, прокручиваемым и доступным только для чтения.  
  
 [  **@fulltext_catalog_name=** ] **"***fulltext_catalog_name***"**  
 Имя полнотекстового каталога. *fulltext_catalog_name* — **sysname**, значение по умолчанию NULL. Если *fulltext_catalog_name* опущен или имеет значение NULL, возвращаются все таблицы индексированных полнотекстового, связанные с базой данных. Если *fulltext_catalog_name* указан, но *table_name* опущен или имеет значение NULL, данные полнотекстового индекса извлекаются для каждого полнотекстового индексированного таблицы, связанной с этим каталогом. Если оба *fulltext_catalog_name* и *table_name* указано, возвращается строка, если *table_name* связан с *fulltext_catalog_name*; в противном случае возникает ошибка.  
  
 [  **@table_name=**] **"***table_name***"**  
 Одно- или двухкомпонентное имя таблицы, для которой запрашиваются полнотекстовые метаданные. *имя_таблицы* — **nvarchar(517)**, значение по умолчанию NULL. Если только *table_name* указано, только строки, относящиеся к *table_name* возвращается.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|Владелец таблицы. Это имя пользователя базы данных, создавшего таблицу.|  
|**ИМЯ_ТАБЛИЦЫ**|**sysname**|Имя таблицы.|  
|**FULLTEXT_KEY_INDEX_NAME**|**sysname**|Индекс, налагающий ограничение UNIQUE на столбец, помеченный как уникальный ключевой столбец.|  
|**FULLTEXT_KEY_COLID**|**int**|Идентификатор столбца уникального индекса, задаваемого параметром FULLTEXT_KEY_NAME.|  
|**FULLTEXT_INDEX_ACTIVE**|**int**|Указывает, можно ли использовать в запросах столбцы, помеченные для полнотекстового индексирования в этой таблице.<br /><br /> 0 = неактивно.<br /><br /> 1= активно.|  
|**FULLTEXT_CATALOG_NAME**|**sysname**|Полнотекстовый каталог, в котором хранятся данные полнотекстового индекса.|  
  
## <a name="permissions"></a>Permissions  
 По умолчанию разрешения на выполнение предоставлены членам роли **public** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как вернуть имена таблиц с полнотекстовым индексом, связанных с полнотекстовым каталогом `Cat_Desc`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @mycursor CURSOR;  
EXEC sp_help_fulltext_tables_cursor @mycursor OUTPUT, 'Cat_Desc';  
FETCH NEXT FROM @mycursor;  
WHILE (@@FETCH_STATUS <> -1)  
   BEGIN  
      FETCH NEXT FROM @mycursor;  
   END;  
CLOSE @mycursor;  
DEALLOCATE @mycursor;  
GO   
```  
  
## <a name="see-also"></a>См. также:  
 [INDEXPROPERTY (Transact-SQL)](../../t-sql/functions/indexproperty-transact-sql.md)   
 [OBJECTPROPERTY (Transact-SQL)](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_fulltext_table &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-fulltext-table-transact-sql.md)   
 [sp_help_fulltext_tables &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
