---
description: sp_help_fulltext_columns_cursor (Transact-SQL)
title: sp_help_fulltext_columns_cursor (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_columns_cursor
- sp_help_fulltext_columns_cursor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_columns_cursor
ms.assetid: 26054e76-53b7-4004-8d48-92ba3435e9d7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dff9f4ea5fb2eda11da2144114cde959197c3723
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469390"
---
# <a name="sp_help_fulltext_columns_cursor-transact-sql"></a>sp_help_fulltext_columns_cursor (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Использует курсор для возврата столбцов, назначенных для полнотекстового индексирования.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте представление каталога [sys. fulltext_index_columns](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_fulltext_columns_cursor [ @cursor_return = ] @cursor_variable OUTPUT   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @cursor_return = ] @cursor_variable OUTPUT` Выходная переменная типа **cursor**. Этот результирующий курсор является динамическим, прокручиваемым и только для чтения.  
  
`[ @table_name = ] 'table_name'` Имя таблицы из одной или двух частей, для которой запрашиваются сведения о полнотекстовом индексе. *table_name* имеет тип **nvarchar (517)** и значение по умолчанию NULL. Если аргумент *table_name* опущен, данные столбца полнотекстового индекса извлекаются для каждой таблицы с полнотекстовым индексом.  
  
`[ @column_name = ] 'column_name'` Имя столбца, для которого требуются метаданные полнотекстового индекса. *column_name* имеет тип **sysname** и значение по умолчанию NULL. Если параметр *column_name* опущен или имеет значение null, возвращаются сведения о полнотекстовом столбце для каждого столбца с полнотекстовым индексом для *table_name*. Если *table_name* также опущен или имеет значение null, возвращаются сведения о столбцах полнотекстового индекса для каждого столбца с полнотекстовым индексом для всех таблиц в базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|Владелец таблицы. Это имя пользователя базы данных, создавшего таблицу.|  
|**TABLE_ID**|**int**|Идентификатор таблицы.|  
|**TABLE_NAME**|**sysname**|Имя таблицы.|  
|**FULLTEXT_COLUMN_NAME**|**sysname**|Столбец таблицы с полнотекстовым индексом, предназначенной для индексирования.|  
|**FULLTEXT_COLID**|**int**|Идентификатор столбца с полнотекстовым индексом.|  
|**FULLTEXT_BLOBTP_COLNAME**|**sysname**|Столбец в таблице с полнотекстовым индексом, указывающий тип документа столбца с полнотекстовым индексом. Это значение применимо только в том случае, если столбец с полнотекстовым индексом является столбцом типа **varbinary (max)** или **Image** .|  
|**FULLTEXT_BLOBTP_COLID**|**int**|Идентификатор столбца типа документа. Это значение применимо только в том случае, если столбец с полнотекстовым индексом является столбцом типа **varbinary (max)** или **Image** .|  
|**FULLTEXT_LANGUAGE**|**sysname**|Язык, используемый для полнотекстового поиска в столбце.|  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения на выполнение предоставлены членам роли **public** .  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает сведения о столбцах, которые были назначены для полнотекстового индексирования во всех таблицах базы данных.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @mycursor CURSOR;  
EXEC sp_help_fulltext_columns_cursor @mycursor OUTPUT  
FETCH NEXT FROM @mycursor;  
WHILE (@@FETCH_STATUS <> -1)  
   BEGIN  
      FETCH NEXT FROM @mycursor;  
   END;  
CLOSE @mycursor;  
DEALLOCATE @mycursor;  
GO   
```  
  
## <a name="see-also"></a>См. также  
 [COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)   
 [sp_fulltext_column &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-column-transact-sql.md)   
 [sp_help_fulltext_columns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
