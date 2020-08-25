---
description: StreamReadEnum
title: Стреамреаденум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamReadEnum
helpviewer_keywords:
- StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
author: rothja
ms.author: jroth
ms.openlocfilehash: c0a0e8d93742574e9a2975b99d15c18500684e60
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777183"
---
# <a name="streamreadenum"></a>StreamReadEnum
Указывает, следует ли считывать весь поток или следующую строку из объекта [потока](./stream-object-ado.md) .  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|По умолчанию. Считывает все байты из потока от текущей позицией до маркера [EOS](./eos-property.md) . Это единственное допустимое значение **стреамреаденум** с двоичными потоками ([тип](./type-property-ado-stream.md) — **адтипебинари**).|  
|**адреадлине**|-2|Считывает следующую строку из потока (назначается свойством [LineSeparator](./lineseparator-property-ado.md) ).|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Метод Read](./read-method.md)  
    :::column-end:::
    :::column:::
        [Метод ReadText](./readtext-method.md)  
    :::column-end:::
:::row-end:::