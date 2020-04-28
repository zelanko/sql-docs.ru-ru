---
title: Рекордтипинум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordTypeEnum
helpviewer_keywords:
- RecordTypeEnum enumeration [ADO]
ms.assetid: f557e537-015d-4ba7-8a41-a6f00b366a91
author: MightyPen
ms.author: genemi
ms.openlocfilehash: df70838b7986993459df4f37af8b7043626a5d7b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931267"
---
# <a name="recordtypeenum"></a>RecordTypeEnum
Указывает тип объекта [записи](../../../ado/reference/ado-api/record-object-ado.md) .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adSimpleRecord**|0|Указывает на *простую* запись (не содержит дочерних узлов).|  
|**adCollectionRecord**|1|Указывает запись *коллекции* (содержит дочерние узлы).|  
|**adRecordUnknown**|-1|Указывает, что тип этой **записи** неизвестен.|  
|**adStructDoc**|2|Указывает Специальный тип записи *коллекции* , представляющий структурированные документы com.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применяется к  
 [Свойство RecordType (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)
