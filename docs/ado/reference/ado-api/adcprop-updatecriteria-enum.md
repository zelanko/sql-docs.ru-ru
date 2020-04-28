---
title: ADCPROP_UPDATECRITERIA_ENUM | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_UPDATECRITERIA_ENUM
helpviewer_keywords:
- ADCPROP_UPDATECRITERIA_ENUM [ADO]
ms.assetid: 33fd7b65-2ec8-4f62-91a7-630b5dab1aa2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 12d960e8fcd5e1f27ea8198ce52e080f6fddf7c2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67921415"
---
# <a name="adcprop_updatecriteria_enum"></a>ADCPROP_UPDATECRITERIA_ENUM
Указывает, какие поля могут использоваться для обнаружения конфликтов во время оптимистического обновления строки источника данных с объектом [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
 Используйте эти константы с динамическим свойством "**условие обновления**" **набора записей** , на которое есть ссылка в [индексе динамического свойства ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) и описанном в документации [службы курсоров Майкрософт для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**адкритериааллколс**|1|Обнаруживает конфликты, если какой бы то ни было столбец в строке источника данных был изменен.|  
|**адкритериакэй**|0|Обнаруживает конфликты, если ключевой столбец строки источника данных был изменен, то есть строка была удалена.|  
|**адкритериатиместамп**|3|Обнаруживает конфликты, если метка времени строки источника данных была изменена, что означает, что доступ к строке осуществлялся после получения **набора записей** .|  
|**адкритериаупдколс**|2|Обнаруживает конфликты, если какие либо столбцы в строке источника данных, соответствующие обновленным полям **набора записей** , были изменены.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|AdoEnums.AdcPropUpdateCriteria.ALLCOLS|  
|AdoEnums.AdcPropUpdateCriteria.KEY|  
|Адоенумс. Адкпропупдатекритериа. TIMESTAMP|  
|Адоенумс. Адкпропупдатекритериа. УПДКОЛС|
