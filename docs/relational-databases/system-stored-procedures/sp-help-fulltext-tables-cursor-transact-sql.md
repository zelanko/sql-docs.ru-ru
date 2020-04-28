---
title: sp_help_fulltext_tables_cursor (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_tables_cursor
- sp_help_fulltext_tables_cursor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_tables_cursor
ms.assetid: 155791eb-8832-4596-8487-7fc70dfba5b9
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8e4218f6a105f81997c37202421feb689cd3a074
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68055000"
---
# <a name="sp_help_fulltext_tables_cursor-transact-sql"></a>sp_help_fulltext_tables_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Использует курсор для возврата списка таблиц, которые зарегистрированы для полнотекстового индексирования.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого используйте новое представление каталога **sys. fulltext_indexes** . Дополнительные сведения см. в разделе [sys. fulltext_indexes &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_fulltext_tables_cursor [ @cursor_return = ] @cursor_variable OUTPUT   
     [ , [ @fulltext_catalog_name = ] 'fulltext_catalog_name' ]   
     [ , [ @table_name = ] 'table_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @cursor_return = ] @cursor_variable OUTPUT`Выходная переменная типа **cursor**. Этот курсор является динамическим, прокручиваемым и доступным только для чтения.  
  
`[ @fulltext_catalog_name = ] 'fulltext_catalog_name'`Имя полнотекстового каталога. Аргумент *fulltext_catalog_name* имеет тип **sysname**и значение по умолчанию NULL. Если параметр *fulltext_catalog_name* опущен или имеет значение null, возвращаются все таблицы с полнотекстовым индексом, связанные с базой данных. Если указано *fulltext_catalog_name* , но *table_name* ОПУЩЕНО или имеет значение null, сведения о полнотекстовом индексе извлекаются для каждой таблицы с полнотекстовым индексом, связанной с этим каталогом. Если указаны и *fulltext_catalog_name* , и *table_name* , то возвращается строка, если *table_name* связана с *fulltext_catalog_name*; в противном случае возникает ошибка.  
  
`[ @table_name = ] 'table_name'`Имя таблицы из одной или двух частей, для которой запрашиваются полнотекстовые метаданные. *table_name* имеет тип **nvarchar (517)** и значение по умолчанию NULL. Если указан только *table_name* , то возвращается только строка, соответствующая *table_name* .  
  
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
 [INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_fulltext_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-table-transact-sql.md)   
 [sp_help_fulltext_tables &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
