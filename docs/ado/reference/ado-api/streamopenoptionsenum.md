---
title: StreamOpenOptionsEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
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
ms.openlocfilehash: 2594a0a2095d49a0819b21967ee7e2a45c8337c1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
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
