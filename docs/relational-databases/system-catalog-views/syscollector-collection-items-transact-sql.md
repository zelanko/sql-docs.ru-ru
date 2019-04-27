---
title: syscollector_collection_items (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_collection_items_TSQL
- syscollector_collection_items
dev_langs:
- TSQL
helpviewer_keywords:
- syscollector_collection_items view
- add data collector view
ms.assetid: a279ecd1-a59c-4315-9f08-bf221f00a465
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 53f978bf7914776e8596a89b0ee9b62770cd6866
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62760216"
---
# <a name="syscollectorcollectionitems-transact-sql"></a>syscollector_collection_items (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения об элементе из набора элементов сбора.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**collection_set_id**|**int**|Определяет набор элементов сбора. Не допускает значение NULL.|  
|**collection_item_id**|**int**|Определяет элемент в наборе сбора. Не допускает значение NULL.|  
|**collector_type_uid**|**uniqueidentifier**|Идентификатор GUID, который использовался для определения типа сборщика. Не допускает значение NULL.|  
|**name**|**nvarchar(4000)**|Имя набора элементов сбора. Допускает значение NULL.|  
|**Частота**|**int**|Частота сбора данных элементом сбора. Не допускает значение NULL.|  
|**parameters**|**xml**|Описывает параметризацию типа сборщика, связанную с элементом сбора. Схема XML для этого элемента сбора проверяется с помощью схемы XML (XSD) хранятся в **parameter_schema** для конкретного типа сборщика. Допускает значение NULL. Дополнительные сведения см. в разделе [syscollector_collector_types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md).|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для **dc_operator**, **dc_proxy**.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Представления сборщика данных (Transact-SQL)](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
