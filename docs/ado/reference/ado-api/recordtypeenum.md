---
title: "RecordTypeEnum | Документы Microsoft"
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
f1_keywords: RecordTypeEnum
helpviewer_keywords: RecordTypeEnum enumeration [ADO]
ms.assetid: f557e537-015d-4ba7-8a41-a6f00b366a91
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e6be2573bbb29379d89eaa26057f00818a31d0da
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="recordtypeenum"></a>RecordTypeEnum
Указывает тип [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adSimpleRecord**|0|Указывает *простой* записи (не содержат дочерние узлы).|  
|**adCollectionRecord**|1|Указывает *коллекции* записи (содержит дочерние узлы).|  
|**adRecordUnknown**|-1|Указывает, что тип этого **записи** неизвестно.|  
|**adStructDoc**|2|Указывает специальный вид *коллекции* запись, которая представляет COM структурированных документов.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство RecordType (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)
