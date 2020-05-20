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
author: rothja
ms.author: jroth
ms.openlocfilehash: 8b47b68b8515ea80405d6083e37a767fb5a6d21e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82756555"
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
