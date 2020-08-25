---
description: RecordOpenOptionsEnum
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
ms.openlocfilehash: 25d3c1fce0fd227a609da49d54bd55762fa1c4a2
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88772313"
---
# <a name="recordopenoptionsenum"></a>RecordOpenOptionsEnum
Задает параметры для открытия [записи](./record-object-ado.md). Эти значения можно комбинировать с помощью или.  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|**адделайфетчфиелдс**|0x8000|Указывает поставщику, что поля, связанные с **записью** , не должны извлекаться изначально, но могут быть получены при первой попытке доступа к полю. Поведение по умолчанию, обозначенное отсутствием этого флага, заключается в получении всех полей объекта **Record** .|  
|**adDelayFetchStream**|0x4000|Указывает поставщику, что поток по умолчанию, связанный с **записью** , не должен извлекаться изначально. Поведение по умолчанию, обозначенное отсутствием этого флага, заключается в получении потока по умолчанию, связанного с объектом **Record** .|  
|**adOpenAsync**|0x1000|Указывает, что объект **Record** открыт в асинхронном режиме.|  
|**adOpenExecuteCommand**|0x10000|Указывает, что исходная строка содержит текст команды, которая должна быть выполнена. Это значение эквивалентно параметру **адкмдтекст** в **наборе записей. Open**.|  
|**adOpenRecordUnspecified**|-1|По умолчанию. Указывает, что параметры не заданы.|  
|**адопенаутпут**|0x800000|Указывает, что, если источник указывает на узел, содержащий исполняемый сценарий (например,. ASP-страница), открытая **запись** будет содержать результаты выполненного скрипта. Это значение допустимо только для записей, не относящихся к коллекции.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применение  
 [Метод Open (объект Record ADO)](./open-method-ado-record.md)