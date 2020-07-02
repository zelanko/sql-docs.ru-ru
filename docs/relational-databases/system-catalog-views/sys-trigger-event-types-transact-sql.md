---
title: sys. trigger_event_types (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trigger_event_types_TSQL
- sys.trigger_event_types_TSQL
- sys.trigger_event_types
- trigger_event_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trigger_event_types catalog view
ms.assetid: 054aed54-7151-4760-934a-149fa434f1ae
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e84c7c7161d88120eccd204c2e24bed508abba7d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85771611"
---
# <a name="systrigger_event_types-transact-sql"></a>sys.trigger_event_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Возвращает по одной строке на каждое событие или группу событий, по которым срабатывает триггер.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**type**|**int**|Тип события или группы событий, который вызывает срабатывание триггера.|  
|**type_name**|**nvarchar (64)**|Имя события или группы событий. Это можно указать в предложении FOR инструкции [CREATE TRIGGER](../../t-sql/statements/create-trigger-transact-sql.md) .|  
|**parent_type**|**int**|Тип группы событий, являющейся родителем для события или группы событий.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
