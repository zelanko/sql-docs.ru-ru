---
title: Рекордопеноптионсенум | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4d97a8cdf2f77f323f0897d7977a2c6945b46b87
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761902"
---
# <a name="recordopenoptionsenum"></a>RecordOpenOptionsEnum
Задает параметры для открытия [записи](../../../ado/reference/ado-api/record-object-ado.md). Эти значения можно комбинировать с помощью или.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**адделайфетчфиелдс**|0x8000|Указывает поставщику, что поля, связанные с **записью** , не должны извлекаться изначально, но могут быть получены при первой попытке доступа к полю. Поведение по умолчанию, обозначенное отсутствием этого флага, заключается в получении всех полей объекта **Record** .|  
|**adDelayFetchStream**|0x4000|Указывает поставщику, что поток по умолчанию, связанный с **записью** , не должен извлекаться изначально. Поведение по умолчанию, обозначенное отсутствием этого флага, заключается в получении потока по умолчанию, связанного с объектом **Record** .|  
|**adOpenAsync**|0x1000|Указывает, что объект **Record** открыт в асинхронном режиме.|  
|**adOpenExecuteCommand**|0x10000|Указывает, что исходная строка содержит текст команды, которая должна быть выполнена. Это значение эквивалентно параметру **адкмдтекст** в **наборе записей. Open**.|  
|**adOpenRecordUnspecified**|-1|По умолчанию. Указывает, что параметры не заданы.|  
|**адопенаутпут**|0x800000|Указывает, что, если источник указывает на узел, содержащий исполняемый сценарий (например,. ASP-страница), открытая **запись** будет содержать результаты выполненного скрипта. Это значение допустимо только для записей, не относящихся к коллекции.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применяется к  
 [Метод Open (объект Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)
