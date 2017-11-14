---
title: "RecordCreateOptionsEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- RecordCreateOptionsEnum
helpviewer_keywords:
- RecordCreateOptionsEnum enumeration [ADO]
ms.assetid: 6d746670-0850-4065-9cd4-168dea1d3ea9
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f108d977c278d9f86ca47853e07c7960ee574b8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="recordcreateoptionsenum"></a>RecordCreateOptionsEnum
Указывает существующую **запись** должен быть открыт или новый **запись** для [запись](../../../ado/reference/ado-api/record-object-ado.md) объекта [откройте](../../../ado/reference/ado-api/open-method-ado-record.md) метод. Значения могут быть объединены с помощью оператора.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adCreateCollection**|0x2000|Создает новый **запись** на узел, указанный в *источника* параметра вместо открытия существующего **записи**. Если источник указывает на существующий узел, то возникает ошибка времени выполнения, если не **adCreateCollection** вместе с **adOpenIfExists** или **adCreateOverwrite**.|  
|**adCreateNonCollection**|0|Создает новый **запись** типа [adSimpleRecord](../../../ado/reference/ado-api/recordtypeenum.md).|  
|**adCreateOverwrite**|0x4000000|Изменяет флаги создания **adCreateCollection**, **adCreateNonCollection**, и **adCreateStructDoc**. При или используется это значение и одно из значений флага для создания, если исходный URL-адрес указывает на существующий узел или **запись**, а затем существующих **записи** является перезаписаны, а один на его месте создается новый. Это значение не может использоваться вместе с **adOpenIfExists**.|  
|**adCreateStructDoc**|0x80000000|Создает новый **запись** типа [adStructDoc](../../../ado/reference/ado-api/recordtypeenum.md), вместо открытия существующего **записи**.|  
|**adFailIfNotExists**|-1|По умолчанию. Приводит к ошибке времени выполнения, если *источника* указывает на несуществующий узла.|  
|**adOpenIfExists**|0x2000000|Изменяет флаги создания **adCreateCollection**, **adCreateNonCollection**, и **adCreateStructDoc**. Когда или используется это значение и одно из значений флага для создания, если исходный URL-адрес указывает на существующий узел или **запись** объекта, то поставщик должен открыть существующий **записи** вместо создания нового одно. Это значение не может использоваться вместе с **adCreateOverwrite**.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Open (ADO запись)](../../../ado/reference/ado-api/open-method-ado-record.md)

