---
description: RecordTypeEnum
title: Рекордтипинум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: ded4106b770ff62edd4b79401885ee5ce3101798
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989665"
---
# <a name="recordtypeenum"></a>RecordTypeEnum
Указывает тип объекта [записи](./record-object-ado.md) .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adSimpleRecord**|0|Указывает на *простую* запись (не содержит дочерних узлов).|  
|**adCollectionRecord**|1|Указывает запись *коллекции* (содержит дочерние узлы).|  
|**adRecordUnknown**|-1|Указывает, что тип этой **записи** неизвестен.|  
|**adStructDoc**|2|Указывает Специальный тип записи *коллекции* , представляющий структурированные документы com.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применение  
 [Свойство RecordType (ADO)](./recordtype-property-ado.md)