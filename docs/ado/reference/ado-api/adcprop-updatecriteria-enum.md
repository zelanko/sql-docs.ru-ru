---
title: ADCPROP_UPDATECRITERIA_ENUM | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_UPDATECRITERIA_ENUM
helpviewer_keywords:
- ADCPROP_UPDATECRITERIA_ENUM [ADO]
ms.assetid: 33fd7b65-2ec8-4f62-91a7-630b5dab1aa2
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a95040a932e35d96a7b2a384da1a910ada118349
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="adcpropupdatecriteriaenum"></a>ADCPROP_UPDATECRITERIA_ENUM
Указывает, какие поля можно использовать для обнаружения конфликтов во время обновления оптимистичного строки источника данных с [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
 Использовать эти константы с **записей** »**условию обновления**«динамические свойства, на которую ссылается [индекс динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) и описаны в [ Служба курсора для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) документации.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adCriteriaAllCols**|1|Обнаруживает конфликты, если был изменен любой столбец строки источника данных.|  
|**adCriteriaKey**|0|Обнаруживает конфликты, если ключевой столбец данных источника строк было изменено, это означает, что строка была удалена.|  
|**adCriteriaTimeStamp**|3|Обнаруживает конфликты, если метка времени данные источника строк было изменено, означающее, что строки уже был осуществлен после **записей** был получен.|  
|**adCriteriaUpdCols**|2|Обнаруживает конфликты, если любой из столбцов источника данных, строки соответствуют полям обновленные **записей** были изменены.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.AdcPropUpdateCriteria.ALLCOLS|  
|AdoEnums.AdcPropUpdateCriteria.KEY|  
|AdoEnums.AdcPropUpdateCriteria.TIMESTAMP|  
|AdoEnums.AdcPropUpdateCriteria.UPDCOLS|
