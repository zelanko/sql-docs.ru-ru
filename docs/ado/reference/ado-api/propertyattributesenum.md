---
title: "PropertyAttributesEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: PropertyAttributesEnum
helpviewer_keywords: PropertyAttributesEnum enumeration [ADO]
ms.assetid: 96a01955-a6b4-4cbf-9c73-52bcd1e9fb25
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 853e63dcd520ab45a26f98091a3e48a816350d0b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
Задает атрибуты [свойство](../../../ado/reference/ado-api/property-object-ado.md) объекта.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adPropNotSupported**|0|Указывает, что свойство не поддерживается поставщиком.|  
|**adPropRequired**|1|Указывает, что пользователь должен указать значение для этого свойства до инициализации источника данных.|  
|**adPropOptional**|2|Указывает, что пользователю не требуется указывать значение для этого свойства до инициализации источника данных.|  
|**adPropRead**|512|Указывает, что пользователь может считывать свойства.|  
|**adPropWrite**|1024|Указывает, что пользователь может задать свойство.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.PropertyAttributes.NOTSUPPORTED|  
|AdoEnums.PropertyAttributes.REQUIRED|  
|AdoEnums.PropertyAttributes.OPTIONAL|  
|AdoEnums.PropertyAttributes.READ|  
|AdoEnums.PropertyAttributes.WRITE|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
