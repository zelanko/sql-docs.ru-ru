---
title: RecordTypeEnum | Документы Microsoft
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
- RecordTypeEnum
helpviewer_keywords:
- RecordTypeEnum enumeration [ADO]
ms.assetid: f557e537-015d-4ba7-8a41-a6f00b366a91
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1f84fecc2ecac03ba6d8a18588d2f0163930b701
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="recordtypeenum"></a>RecordTypeEnum
Указывает тип [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adSimpleRecord**|0|Указывает *простой* записи (не содержат дочерние узлы).|  
|**adCollectionRecord**|1|Указывает *коллекции* записи (содержит дочерние узлы).|  
|**adRecordUnknown**|-1|Указывает, что тип этого **записи** неизвестно.|  
|**adStructDoc**|2|Указывает специальный вид *коллекции* запись, которая представляет COM структурированных документов.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство RecordType (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)
