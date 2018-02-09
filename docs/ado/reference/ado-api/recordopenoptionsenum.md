---
title: "RecordOpenOptionsEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- RecordOpenOptionsEnum
helpviewer_keywords:
- RecordOpenOptionsEnum enumeration [ADO]
ms.assetid: 9028aba4-90fc-4dfc-88e4-fa8a7b6fedee
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 56caae53741a24727763868295ca92216557323c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="recordopenoptionsenum"></a>RecordOpenOptionsEnum
Задает параметры для открытия [записи](../../../ado/reference/ado-api/record-object-ado.md). Эти значения могут объединяться с помощью или.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adDelayFetchFields**|0x8000|Указывает, для поля, с которым связан поставщик **записи** не должны извлекаться изначально, но можно получить во время первой попытки получить доступ к полю. По умолчанию, указывает на отсутствие этот флаг выполняется для получения всех **записи** объекта поля.|  
|**adDelayFetchStream**|0x4000|Указывает поставщику, поток по умолчанию, связанный с **записи** не должны извлекаться изначально. По умолчанию, указывает на отсутствие этот флаг выполняется для получения потока по умолчанию, связанного с **записи** объекта.|  
|**adOpenAsync**|0x1000|Указывает, что **записи** объект открыт в асинхронном режиме.|  
|**adOpenExecuteCommand**|0x10000|Указывает, что исходная строка содержит текст команды, который должен быть выполнен. Это значение эквивалентно **adCmdText** параметр **Recordset.Open**.|  
|**adOpenRecordUnspecified**|-1|По умолчанию. Указывает, что параметры не указаны.|  
|**adOpenOutput**|0x800000|Указывает, что если источник указывает на узел, содержащий исполняемый скрипт (такие как. ASP-странице), затем открытый **записи** будет содержать результаты выполненный скрипт. Это значение допустимо только записями, не являющихся коллекциями.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Open (объект Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)
