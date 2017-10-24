---
title: "ADCPROP_ASYNCTHREADPRIORITY_ENUM | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM
helpviewer_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM [ADO]
ms.assetid: f0965617-17d8-41e0-98d0-f824274735a6
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cf0f8e2f68eccceecbbe7fe3b2c17039b55d2887
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="adcpropasyncthreadpriorityenum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
Для служб удаленных рабочих СТОЛОВ [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, указывающее приоритет выполнения асинхронного потока, который получает данные.  
  
 Использовать эти константы с **записей** »**приоритет потока фоновой**«динамические свойства, которое будет ссылаться в ADO для OLE DB динамических свойств индекса и описаны в [ Служба курсора для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) документации.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adPriorityAboveNormal**|4|Задает приоритет между обычным и высокий.|  
|**adPriorityBelowNormal**|2|Задает приоритет между наименьшим и обычной.|  
|**adPriorityHighest**|5|Задает приоритет наибольшее возможное.|  
|**AdPriorityLowest**|1|Задает приоритет до наименьшего возможного.|  
|**adPriorityNormal**|3|Задает приоритет normal.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.AdcPropAsyncThreadPriority.ABOVENORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.BELOWNORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.HIGHEST|  
|AdoEnums.AdcPropAsyncThreadPriority.LOWEST|  
|AdoEnums.AdcPropAsyncThreadPriority.NORMAL|

