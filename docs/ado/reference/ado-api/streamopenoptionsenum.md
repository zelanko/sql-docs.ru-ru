---
title: StreamOpenOptionsEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamOpenOptionsEnum
helpviewer_keywords:
- StreamOpenOptionsEnum enumeration [ADO]
ms.assetid: 85b6c57f-47ed-46ba-bd92-07882ae9e9d2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1e7e685e9d3f23d4d1c3317e24f63d7bdac23db
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63180741"
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Указывает параметры для открытия [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта. Значения могут объединяться с помощью операции или.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|Открывает **Stream** объекта в асинхронном режиме.|  
|**adOpenStreamFromRecord**|4|Определяет содержимое *источника* параметр будет уже открытого [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта. Поведение по умолчанию — обрабатывать *источника* как URL-адрес, указывающий непосредственно к узлу в виде древовидной структуры. Открытие потока по умолчанию, связанные с этим узлом.|  
|**adOpenStreamUnspecified**|-1|По умолчанию. Указывает, открывающий **Stream** объекта с параметрами по умолчанию.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Эти константы не имеют эквивалентов ADO и WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Open (объект Stream ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)
