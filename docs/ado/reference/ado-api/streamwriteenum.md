---
title: Стреамвритинум | Документация Майкрософт
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
ms.openlocfilehash: 4cc9de1481cc683bddafe2f92959977319600f6a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67928634"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Указывает, добавляется ли разделитель строк к строке, записанной в объект [потока](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|По умолчанию. Записывает указанную текстовую строку (заданную параметром *данных* ) в объект **потока** .|  
|**adWriteLine**|1|Записывает текстовую строку и символ разделителя строки в объект **потока** . Если свойство [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) не определено, то возвращается ошибка времени выполнения.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применяется к  
 [Метод WriteText](../../../ado/reference/ado-api/writetext-method.md)
