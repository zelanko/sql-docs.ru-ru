---
description: Свойство LineSeparator (ADO)
title: Свойство LineSeparator (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 7bd1e14d5c7ebc84ea4736da08296eca0e02ea38
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990725"
---
# <a name="lineseparator-property-ado"></a>Свойство LineSeparator (ADO)
Указывает двоичный символ, используемый в качестве разделителя строк в объектах текстового [потока](./stream-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [линесепараторсенум](./lineseparatorsenum.md) , указывающее символ разделителя строки, используемый в **потоке**. Значение по умолчанию — **адкрлф**.  
  
## <a name="remarks"></a>Remarks  
 **LineSeparator** используется для интерпретации строк при считывании содержимого текстового **потока**. Строки можно пропустить с помощью метода [скиплине](./skipline-method.md) .  
  
 **LineSeparator** используется только с объектами **потока** текста ([тип](./type-property-ado-stream.md) — **адтипетекст**). Это свойство игнорируется, если **Type** имеет значение **адтипебинари**.  
  
## <a name="applies-to"></a>Применение  
 [Объект Stream (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Stream (ADO)](./stream-object-ado.md)