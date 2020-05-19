---
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
ms.openlocfilehash: 9248dcabb4c52ceceb6e4876b034480415e77963
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82754820"
---
# <a name="lineseparator-property-ado"></a>Свойство LineSeparator (ADO)
Указывает двоичный символ, используемый в качестве разделителя строк в объектах текстового [потока](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [линесепараторсенум](../../../ado/reference/ado-api/lineseparatorsenum.md) , указывающее символ разделителя строки, используемый в **потоке**. Значение по умолчанию — **адкрлф**.  
  
## <a name="remarks"></a>Примечания  
 **LineSeparator** используется для интерпретации строк при считывании содержимого текстового **потока**. Строки можно пропустить с помощью метода [скиплине](../../../ado/reference/ado-api/skipline-method.md) .  
  
 **LineSeparator** используется только с объектами **потока** текста ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **адтипетекст**). Это свойство игнорируется, если **Type** имеет значение **адтипебинари**.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
