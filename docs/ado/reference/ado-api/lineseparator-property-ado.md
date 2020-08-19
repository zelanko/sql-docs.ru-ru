---
description: Свойство LineSeparator (ADO)
title: Свойство LineSeparator (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
author: rothja
ms.author: jroth
ms.openlocfilehash: e3571f6a01fc60377380c0dcc40c870dfc71276a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443376"
---
# <a name="lineseparator-property-ado"></a>Свойство LineSeparator (ADO)
Указывает двоичный символ, используемый в качестве разделителя строк в объектах текстового [потока](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [линесепараторсенум](../../../ado/reference/ado-api/lineseparatorsenum.md) , указывающее символ разделителя строки, используемый в **потоке**. Значение по умолчанию — **адкрлф**.  
  
## <a name="remarks"></a>Remarks  
 **LineSeparator** используется для интерпретации строк при считывании содержимого текстового **потока**. Строки можно пропустить с помощью метода [скиплине](../../../ado/reference/ado-api/skipline-method.md) .  
  
 **LineSeparator** используется только с объектами **потока** текста ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **адтипетекст**). Это свойство игнорируется, если **Type** имеет значение **адтипебинари**.  
  
## <a name="applies-to"></a>Применение  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
