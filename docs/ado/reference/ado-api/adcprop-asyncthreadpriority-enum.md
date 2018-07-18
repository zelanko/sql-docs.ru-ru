---
title: ADCPROP_ASYNCTHREADPRIORITY_ENUM | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM
helpviewer_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM [ADO]
ms.assetid: f0965617-17d8-41e0-98d0-f824274735a6
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7857e3b176191ba5b9c98a40c7f02abe666edec8
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275233"
---
# <a name="adcpropasyncthreadpriorityenum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
Для служб удаленных рабочих СТОЛОВ [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, указывающее приоритет выполнения асинхронного потока, который получает данные.  
  
 Использовать эти константы с **записей** »**приоритет потока фоновой**«динамические свойства, которое будет ссылаться в ADO для OLE DB динамических свойств индекса и описаны в [ Служба курсора для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) документации.  
  
|Константа|Значение|Описание|  
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
