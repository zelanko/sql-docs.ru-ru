---
title: sys. trace_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.trace_columns
- trace_columns
- trace_columns_TSQL
- sys.trace_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_columns catalog view
ms.assetid: 5c48eb09-9e9b-45dd-b151-ca39b026ece5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bda45d55505356594f23a8bb1ece2e95153206a7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022652"
---
# <a name="systrace_columns-transact-sql"></a>sys.trace_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Представление каталога **sys. trace_columns** содержит список всех столбцов событий трассировки. Эти столбцы не изменяются для этой версии компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
 Полный список поддерживаемых событий трассировки см. в разделе [Справочник по классам событий SQL Server](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте представления каталога расширенных событий.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**trace_column_id**|**smallint**|Уникальный идентификатор этого столбца.|  
|**name**|**nvarchar(128**|Уникальное имя этого столбца. Этот аргумент не локализуется.|  
|**type_name**|**nvarchar(128**|Имя типа данных этого столбца.|  
|**max_size**|**int**|Максимальный размер данных этого столбца, в байтах.|  
|**is_filterable**|**bit**|Указывает на то, может ли столбец использоваться в спецификации фильтра.<br /><br /> 0 = false.<br /><br /> 1 = true;|  
|**is_repeatable**|**bit**|Указывает на то, может ли на столбец выполняться ссылка в данных «повторяемых столбцов».<br /><br /> 0 = false.<br /><br /> 1 = true;|  
|**is_repeated_base**|**bit**|Указывает на то, используется ли этот столбец как уникальный ключ для ссылки на повторяемые данные.<br /><br /> 0 = false.<br /><br /> 1 = true;|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys. traces &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys. trace_categories &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys. trace_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [sys. trace_event_bindings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys. trace_subclass_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
