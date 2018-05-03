---
title: StreamOpenOptionsEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamOpenOptionsEnum
helpviewer_keywords:
- StreamOpenOptionsEnum enumeration [ADO]
ms.assetid: 85b6c57f-47ed-46ba-bd92-07882ae9e9d2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ca4119ac853ec6586c65f8648440ddf02fabb4a4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Задает параметры для открытия [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта. Значения могут быть объединены с операцией или.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|Открывает **поток** объекта в асинхронном режиме.|  
|**adOpenStreamFromRecord**|4|Определяет содержимое *источника* параметр должен быть уже открытого [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта. Поведение по умолчанию — обрабатывать *источника* как URL-адрес, указывающий на узел в структуре дерева. Открытие потока по умолчанию, связанные с этим узлом.|  
|**adOpenStreamUnspecified**|-1|По умолчанию. Указывает открывающей **поток** объекта с параметрами по умолчанию.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Open (объект Stream ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)
