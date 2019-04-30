---
title: StreamWriteEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamWriteEnum
helpviewer_keywords:
- StreamWriteEnum enumeration [ADO]
ms.assetid: bdbf3405-a0bd-4f02-85d4-e3fe8da3f3f7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d0f42561d7b324a13068c14d0fc7971d3d46d83b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63311774"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Указывает, добавляется ли разделитель строки в [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|По умолчанию. Записывает заданную текстовую строку (определяется *данных* параметр) для **Stream** объекта.|  
|**adWriteLine**|1|Записывает в текстовую строку и символ разделителя строки для **Stream** объекта. Если [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) свойство не определено, а затем возвращает ошибку времени выполнения.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Эти константы не имеют эквивалентов ADO и WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод WriteText](../../../ado/reference/ado-api/writetext-method.md)
