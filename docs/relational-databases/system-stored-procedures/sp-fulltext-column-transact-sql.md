---
title: sp_fulltext_column (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_column_TSQL
- sp_fulltext_column
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_column
ms.assetid: a84cc45d-1b50-44af-85df-2ea033b8a6a9
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9e17a87a04c8c4286a66c6e7a0746f2d7de48d72
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124341"
---
# <a name="sp_fulltext_column-transact-sql"></a>sp_fulltext_column (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Определяет, должен ли конкретный столбец таблицы использоваться в полнотекстовом индексировании.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Используйте вместо него [инструкцию ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) .  
  
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
`[ @tabname = ] 'qualified_table_name'`Имя таблицы из одной или двух частей. Таблица должна существовать в текущей базе данных. Таблица должна содержать полнотекстовый индекс. *qualified_table_name* имеет тип **nvarchar (517)** и не имеет значения по умолчанию.  
  
`[ @colname = ] 'column_name'`Имя столбца в *qualified_table_name*. Столбец должен быть столбцом типа character, **varbinary (max)** или **Image** и не может быть вычисляемым столбцом. Аргумент *column_name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]может создавать полнотекстовые индексы текстовых данных, хранящихся в столбцах, имеющих тип данных **varbinary (max)** или **Image** . Изображения и рисунки не индексируются.  
  
`[ @action = ] 'action'`Действие, которое необходимо выполнить. *Action* имеет тип **varchar (20)**, не имеет значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**включить**|Добавляет *column_name* *qualified_table_name* в неактивный полнотекстовый индекс таблицы. Это действие активирует полнотекстовое индексирование столбца.|  
|**тени**|Удаляет *column_name* *qualified_table_name* из неактивного полнотекстового индекса таблицы.|  
  
`[ @language = ] 'language_term'`Язык данных, хранящихся в столбце. Список языков, входящих в состав, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]см. в разделе [sys. Fulltext_languages &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).  
  
> [!NOTE]  
>  Указывайте значение «Neutral», если столбец содержит данные на нескольких языках или на языке, который не поддерживается. Значение по умолчанию задается параметром конфигурации «default full-text language».  
  
`[ @type_colname = ] 'type_column_name'`Имя столбца в *qualified_table_name* , содержащего тип документа *column_name*. Этот столбец должен иметь **тип char**, **nchar**, **varchar**или **nvarchar**. Он используется только в том случае, если тип данных *column_name* имеет тип **varbinary (max)** или **Image**. Аргумент *type_column_name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Если полнотекстовый индекс активен, все выполняющиеся заполнения прекращаются. Более того, если для таблицы с полнотекстовым индексом включено отслеживание изменений, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удостоверится, что индекс актуален. Например, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прекратит текущее заполнение таблицы, удалит существующий индекс и начнет новое заполнение.  
  
 Если используется отслеживание изменений и нужно добавить или удалить столбец, сохранив полнотекстовый индекс, таблицу следует деактивировать, а затем добавить или удалить нужные столбцы. Эти действия закрепляют индекс. Таблица может быть активирована позже, когда имеет смысл начать заполнение.  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен быть членом предопределенной роли базы данных **db_ddladmin** или членом предопределенной роли базы данных **db_owner** или владельцем таблицы.  
  
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
  
## <a name="see-also"></a>См. также:  
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_help_fulltext_columns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-transact-sql.md)   
 [sp_help_fulltext_columns_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-cursor-transact-sql.md)   
 [sp_help_fulltext_tables &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-transact-sql.md)   
 [sp_help_fulltext_tables_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-cursor-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимые процедуры полнотекстового поиска и семантического поиска &#40;языке Transact-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  
