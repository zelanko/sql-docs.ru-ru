---
title: StreamWriteEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamWriteEnum
helpviewer_keywords:
- StreamWriteEnum enumeration [ADO]
ms.assetid: bdbf3405-a0bd-4f02-85d4-e3fe8da3f3f7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62b5718d87d9c5117d10ad4ba55cdc783948778a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282728"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Указывает, добавляется ли разделитель строки в [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|По умолчанию. Записывает указанную текстовую строку (заданные *данные* параметр) для **поток** объекта.|  
|**adWriteLine**|1|Записывает в текстовую строку и символ разделителя строки в **поток** объекта. Если [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) свойство не определено, то возвращается ошибка времени выполнения.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод WriteText](../../../ado/reference/ado-api/writetext-method.md)
