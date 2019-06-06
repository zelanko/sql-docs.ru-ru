---
title: RecordOpenOptionsEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordOpenOptionsEnum
helpviewer_keywords:
- RecordOpenOptionsEnum enumeration [ADO]
ms.assetid: 9028aba4-90fc-4dfc-88e4-fa8a7b6fedee
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c0ed637d8e77ef7fc152f994da81db010fa80900
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66712161"
---
# <a name="recordopenoptionsenum"></a>RecordOpenOptionsEnum
Указывает параметры для открытия [записи](../../../ado/reference/ado-api/record-object-ado.md). Эти значения могут объединяться с помощью или.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adDelayFetchFields**|0x8000|Указывает поставщику, поля, с которым связан **записи** не должны извлекаться изначально, но могут быть получены во первая попытка получить доступ к полю. По умолчанию, указывает на отсутствие этот флаг задается для извлечения всех **записи** объекта поля.|  
|**adDelayFetchStream**|0x4000|Указывает поставщику, который по умолчанию поток, связанный с **записи** не должны извлекаться изначально. По умолчанию, указывает на отсутствие этот флаг задается для получения потока по умолчанию, связанные с **записи** объекта.|  
|**adOpenAsync**|0x1000|Указывает, что **записи** объект открыт в асинхронном режиме.|  
|**adOpenExecuteCommand**|0x10000|Указывает, что исходная строка содержит текст команды, который должен быть выполнен. Это значение эквивалентно **adCmdText** параметр **Recordset.Open**.|  
|**adOpenRecordUnspecified**|-1|По умолчанию. Указывает, что параметры не указаны.|  
|**adOpenOutput**|0x800000|Указывает, что, если источник указывает на узел, содержащий исполняемый сценарий (такие как. ASP-странице), затем открытый **записи** будет содержать результаты выполненного сценария. Это значение допустимо только записями, не являющихся коллекциями.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Эти константы не имеют эквивалентов ADO и WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Open (объект Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)
