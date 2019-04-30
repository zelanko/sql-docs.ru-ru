---
title: StreamReadEnum | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26ccabf3e73a67c14e7201f26e4ebf739a6352cb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63311857"
---
# <a name="streamreadenum"></a>StreamReadEnum
Указывает, следует ли читать весь поток или следующая строка из [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|По умолчанию. Считывает все байты из потока, начиная с текущей позиции и более поздних версий [EOS](../../../ado/reference/ado-api/eos-property.md) маркера. Это единственное допустимое **StreamReadEnum** значение с двоичными потоками ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeBinary**).|  
|**adReadLine**|-2|Считывает следующую строку из потока (обозначенный [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) свойство).|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Эти константы не имеют эквивалентов ADO и WFC.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Метод Read](../../../ado/reference/ado-api/read-method.md)|[Метод ReadText](../../../ado/reference/ado-api/readtext-method.md)|
