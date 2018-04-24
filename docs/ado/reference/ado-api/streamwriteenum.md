---
title: StreamWriteEnum | Документы Microsoft
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
- StreamWriteEnum
helpviewer_keywords:
- StreamWriteEnum enumeration [ADO]
ms.assetid: bdbf3405-a0bd-4f02-85d4-e3fe8da3f3f7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 37435758716d914b868e785eaaf72243de8ebbc6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
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
