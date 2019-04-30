---
title: RecordCreateOptionsEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordCreateOptionsEnum
helpviewer_keywords:
- RecordCreateOptionsEnum enumeration [ADO]
ms.assetid: 6d746670-0850-4065-9cd4-168dea1d3ea9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8574da628c4bc1af800635ed9228e074817adae9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63239974"
---
# <a name="recordcreateoptionsenum"></a>RecordCreateOptionsEnum
Указывает ли существующий **записи** должен быть открыт или новый **записи** для [записи](../../../ado/reference/ado-api/record-object-ado.md) объект [откройте](../../../ado/reference/ado-api/open-method-ado-record.md) метод. Значения могут объединяться с помощью оператора.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adCreateCollection**|0x2000|Создает новый **записи** на узел, указанный в *источника* параметра вместо использования открытии существующего **записи**. Если источник указывает на существующий узел, то возникает ошибка времени выполнения, если не **adCreateCollection** объединяется с **adOpenIfExists** или **adCreateOverwrite**.|  
|**adCreateNonCollection**|0|Создает новый **записи** типа [adSimpleRecord](../../../ado/reference/ado-api/recordtypeenum.md).|  
|**adCreateOverwrite**|0x4000000|Изменяет флаги создания **adCreateCollection**, **adCreateNonCollection**, и **adCreateStructDoc**. При или использовать с это значение и одно из значений флаг создания, в том случае, если URL-адрес источника указывает на существующий узел или **записи**, то существующий **записи** является перезаписан, а новый, он будет создан на его месте. Это значение не может быть использовано вместе с **adOpenIfExists**.|  
|**adCreateStructDoc**|0x80000000|Создает новый **записи** типа [adStructDoc](../../../ado/reference/ado-api/recordtypeenum.md), вместо открытия существующего **записи**.|  
|**adFailIfNotExists**|-1|По умолчанию. Приводит к ошибке времени выполнения, если *источника* указывает на несуществующий узел.|  
|**adOpenIfExists**|0x2000000|Изменяет флаги создания **adCreateCollection**, **adCreateNonCollection**, и **adCreateStructDoc**. Когда или использовать с это значение и одно из значений флаг создания, в том случае, если URL-адрес источника указывает на существующий узел или **записи** объекта, то поставщик должен открыть существующий **записи** вместо создания нового одно. Это значение не может быть использовано вместе с **adCreateOverwrite**.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Эти константы не имеют эквивалентов ADO и WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Open (объект Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)
