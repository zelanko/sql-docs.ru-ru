---
title: ADCPROP_UPDATECRITERIA_ENUM | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
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
ms.workload: Inactive
ms.openlocfilehash: 7bdd24f437d1bc0712e0e0222a8e99e999b1f3a1
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
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
