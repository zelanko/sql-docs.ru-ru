---
description: StreamWriteEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 343e5fd45a32e45cda342ab01feb64f379054486
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777163"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
Указывает, добавляется ли разделитель строк к строке, записанной в объект [потока](./stream-object-ado.md) .  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|По умолчанию. Записывает указанную текстовую строку (заданную параметром *данных* ) в объект **потока** .|  
|**adWriteLine**|1|Записывает текстовую строку и символ разделителя строки в объект **потока** . Если свойство [LineSeparator](./lineseparator-property-ado.md) не определено, то возвращается ошибка времени выполнения.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применение  
 [Метод WriteText](./writetext-method.md)