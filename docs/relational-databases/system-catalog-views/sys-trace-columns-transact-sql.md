---
title: "sys.trace_columns (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.trace_columns
- trace_columns
- trace_columns_TSQL
- sys.trace_columns_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.trace_columns catalog view
ms.assetid: 5c48eb09-9e9b-45dd-b151-ca39b026ece5
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7405b51d9071238a237a11ef7c0ceef78e2e7119
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="systracecolumns-transact-sql"></a>sys.trace_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sys.trace_columns** представление каталога содержит список всех столбцов событий трассировки. Эти столбцы не изменяются для этой версии компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
 Полный список поддерживаемых событий трассировки см. в разделе [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте представления каталога расширенных событий.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**trace_column_id**|**smallint**|Уникальный идентификатор этого столбца.|  
|**name**|**nvarchar(128)**|Уникальное имя этого столбца. Этот аргумент не локализуется.|  
|**Функция TYPE_NAME**|**nvarchar(128)**|Имя типа данных этого столбца.|  
|**max_size**|**int**|Максимальный размер данных этого столбца, в байтах.|  
|**is_filterable**|**bit**|Указывает на то, может ли столбец использоваться в спецификации фильтра.<br /><br /> 0 = false.<br /><br /> 1 = true;|  
|**is_repeatable**|**bit**|Указывает на то, может ли на столбец выполняться ссылка в данных «повторяемых столбцов».<br /><br /> 0 = false.<br /><br /> 1 = true;|  
|**is_repeated_base**|**bit**|Указывает на то, используется ли этот столбец как уникальный ключ для ссылки на повторяемые данные.<br /><br /> 0 = false.<br /><br /> 1 = true;|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.traces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys.trace_categories &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys.trace_events &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [sys.trace_event_bindings &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys.trace_subclass_values &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
