---
title: PropertyAttributesEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PropertyAttributesEnum
helpviewer_keywords:
- PropertyAttributesEnum enumeration [ADO]
ms.assetid: 96a01955-a6b4-4cbf-9c73-52bcd1e9fb25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0bb38a73008d86144751ee324eb442bf711d65a5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47835972"
---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
Указывает атрибуты [свойство](../../../ado/reference/ado-api/property-object-ado.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adPropNotSupported**|0|Указывает, что свойство не поддерживается поставщиком.|  
|**adPropRequired**|1|Указывает, что пользователь должен указать значение для этого свойства перед инициализацией источника данных.|  
|**adPropOptional**|2|Указывает, что пользователю не нужно указать значение для этого свойства перед инициализацией источника данных.|  
|**adPropRead**|512|Указывает, что пользователь может считывать свойства.|  
|**adPropWrite**|1024|Указывает, что пользователь может задать свойство.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
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
