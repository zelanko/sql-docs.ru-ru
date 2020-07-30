---
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
ms.openlocfilehash: 92c599665548c36b8349290b02d197393f707fbf
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243195"
---
# <a name="streamreadenum"></a>StreamReadEnum
Указывает, следует ли считывать весь поток или следующую строку из объекта [потока](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|По умолчанию. Считывает все байты из потока от текущей позицией до маркера [EOS](../../../ado/reference/ado-api/eos-property.md) . Это единственное допустимое значение **стреамреаденум** с двоичными потоками ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **адтипебинари**).|  
|**адреадлине**|–2|Считывает следующую строку из потока (назначается свойством [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) ).|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Метод Read](../../../ado/reference/ado-api/read-method.md)  
    :::column-end:::
    :::column:::
        [Метод ReadText](../../../ado/reference/ado-api/readtext-method.md)  
    :::column-end:::
:::row-end:::
