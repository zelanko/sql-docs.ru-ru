---
description: syscollector_collection_items (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: dd2655b1d2c53af8443f0c35a09a221ef5d87724
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89539508"
---
# <a name="syscollector_collection_items-transact-sql"></a>syscollector_collection_items (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает сведения об элементе из набора элементов сбора.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**collection_set_id**|**int**|Определяет набор элементов сбора. Не допускает значение NULL.|  
|**collection_item_id**|**int**|Определяет элемент в наборе сбора. Не допускает значение NULL.|  
|**collector_type_uid**|**uniqueidentifier**|Идентификатор GUID, который использовался для определения типа сборщика. Не допускает значение NULL.|  
|**name**|**nvarchar(4000)**|Имя набора элементов сбора. Допускает значение NULL.|  
|**импульс**|**int**|Частота сбора данных элементом сбора. Не допускает значение NULL.|  
|**parameters**|**xml**|Описывает параметризацию типа сборщика, связанную с элементом сбора. XML-схема для этого элемента сбора проверяется с помощью XML-схемы (XSD), хранящейся в **parameter_schema** для конкретного типа сборщика. Допускает значение NULL. Дополнительные сведения см. в разделе [syscollector_collector_types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md).|  
  
## <a name="permissions"></a>Разрешения  
 Требуется SELECT для **dc_operator**, **dc_proxy**.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Представления сборщика данных (Transact-SQL)](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
