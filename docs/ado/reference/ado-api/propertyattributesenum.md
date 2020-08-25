---
description: PropertyAttributesEnum
title: Пропертяттрибутесенум | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 823505aae912c64c2fd7d3375b3426cb6428bcdd
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88772873"
---
# <a name="propertyattributesenum"></a>PropertyAttributesEnum
Задает атрибуты объекта [Property](./property-object-ado.md) .  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|**адпропнотсуппортед**|0|Указывает, что свойство не поддерживается поставщиком.|  
|**адпропрекуиред**|1|Указывает, что пользователь должен указать значение этого свойства перед инициализацией источника данных.|  
|**adPropOptional**|2|Указывает, что пользователю не нужно указывать значение этого свойства перед инициализацией источника данных.|  
|**адпропреад**|512|Указывает, что пользователь может прочитать свойство.|  
|**adPropWrite**|1024|Указывает, что пользователь может задать свойство.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. Пропертяттрибутес. NOTSUPPORTED|  
|AdoEnums.PropertyAttributes.REQUIRED|  
|Адоенумс. Пропертяттрибутес. необязательный|  
|Адоенумс. Пропертяттрибутес. READ|  
|Адоенумс. Пропертяттрибутес. WRITE|  
  
## <a name="applies-to"></a>Применение  
 [Свойство Attributes (ADO)](./attributes-property-ado.md)