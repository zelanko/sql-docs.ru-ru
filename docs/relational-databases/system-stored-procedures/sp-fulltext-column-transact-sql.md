---
title: sp_fulltext_column (Transact-SQL) | Документы Microsoft
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
- sp_fulltext_column_TSQL
- sp_fulltext_column
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_column
ms.assetid: a84cc45d-1b50-44af-85df-2ea033b8a6a9
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6c1a53e05eef89584526846c3f3d3c6324164a94
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33259584"
---
# <a name="spfulltextcolumn-transact-sql"></a>sp_fulltext_column (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Определяет, должен ли конкретный столбец таблицы использоваться в полнотекстовом индексировании.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) вместо него.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_fulltext_column [ @tabname= ] 'qualified_table_name' ,   
     [ @colname= ] 'column_name' ,   
     [ @action= ] 'action'   
     [ , [ @language= ] 'language_term' ]   
     [ , [ @type_colname= ] 'type_column_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@tabname=** ] **"***таблицы не собирались***"**  
 Имя таблицы, состоящее из одной или двух частей. Таблица должна существовать в текущей базе данных. Таблица должна содержать полнотекстовый индекс. *таблицы не собирались* — **nvarchar(517)**, и не имеет значения по умолчанию.  
  
 [  **@colname=** ] **"***column_name***"**  
 Имя столбца в *таблицы не собирались*. Столбец должен иметь символьный тип, **varbinary(max)** или **изображения** столбца и не может быть вычисляемым столбцом. *column_name* — **sysname**, не имеет значения по умолчанию.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно создавать полнотекстовые индексы текстовых данных, хранящихся в столбцах, которые имеют **varbinary(max)** или **изображения** тип данных. Изображения и рисунки не индексируются.  
  
 [  **@action=** ] **"***действия***"**  
 Действие, которое должно быть выполнено. *Действие* — **varchar(20)**, не имеет значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**add**|Добавляет *column_name* из *таблицы не собирались* для неактивного полнотекстового индекса таблицы. Это действие активирует полнотекстовое индексирование столбца.|  
|**DROP**|Удаляет *column_name* из *таблицы не собирались* из неактивного полнотекстового индекса таблицы.|  
  
 [  **@language=** ] **"***language_term***"**  
 Язык данных, хранящихся в столбце. Список языков, включенных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в разделе [sys.fulltext_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).  
  
> [!NOTE]  
>  Указывайте значение «Neutral», если столбец содержит данные на нескольких языках или на языке, который не поддерживается. Значение по умолчанию задается параметром конфигурации «default full-text language».  
  
 [  **@type_colname =** ] **"***type_column_name***"**  
 Имя столбца в *таблицы не собирались* , содержащего тип документа *column_name*. Этот столбец должен быть **char**, **nchar**, **varchar**, или **nvarchar**. Оно используется, только если тип данных столбца *column_name* относится к типу **varbinary(max)** или **изображения**. *type_column_name* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Если полнотекстовый индекс активен, все выполняющиеся заполнения прекращаются. Более того, если для таблицы с полнотекстовым индексом включено отслеживание изменений, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удостоверится, что индекс актуален. Например, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прекратит текущее заполнение таблицы, удалит существующий индекс и начнет новое заполнение.  
  
 Если используется отслеживание изменений и нужно добавить или удалить столбец, сохранив полнотекстовый индекс, таблицу следует деактивировать, а затем добавить или удалить нужные столбцы. Эти действия закрепляют индекс. Таблица может быть активирована позже, когда имеет смысл начать заполнение.  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен быть членом **db_ddladmin** предопределенной роли базы данных или членом **db_owner** фиксированной роли базы данных, а также владелец таблицы.  
  
## <a name="examples"></a>Примеры  
 В следующем примере столбец `DocumentSummary` таблицы `Document` будет добавлен в полнотекстовый индекс этой таблицы.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_column 'Production.Document', DocumentSummary, 'add';  
GO  
```  
  
 В следующем примере подразумевается, что для таблицы `spanishTbl` создан полнотекстовый индекс. Чтобы добавить столбец `spanishCol` к этому индексу, выполните следующую хранимую процедуру:  
  
```  
EXEC sp_fulltext_column 'spanishTbl', 'spanishCol', 'add', 0xC0A;  
GO  
```  
  
 При выполнении такого запроса:  
  
```  
SELECT *   
FROM spanishTbl   
WHERE CONTAINS(spanishCol, 'formsof(inflectional, trabajar)')  
```  
  
 Результирующий набор будет включать в себя строки с различными формами слова `trabajar` («работать»), например `trabajo`, `trabajamos` и `trabajan`.  
  
> [!NOTE]  
>  Все столбцы, перечисленные в одной функции предложения полнотекстового запроса, должны быть на одном языке.  
  
## <a name="see-also"></a>См. также  
 [OBJECTPROPERTY (Transact-SQL)](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_help_fulltext_columns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-transact-sql.md)   
 [sp_help_fulltext_columns_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-cursor-transact-sql.md)   
 [sp_help_fulltext_tables &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-transact-sql.md)   
 [sp_help_fulltext_tables_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-cursor-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Компонент Full-Text Search и семантический поиск хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  
