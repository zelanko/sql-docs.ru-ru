---
title: "RecordTypeEnum | Документы Microsoft"
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
- RecordTypeEnum
helpviewer_keywords:
- RecordTypeEnum enumeration [ADO]
ms.assetid: f557e537-015d-4ba7-8a41-a6f00b366a91
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9bc1723621796d349d393826ff948e9dd295bbaf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
