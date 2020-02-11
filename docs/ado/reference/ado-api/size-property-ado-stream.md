---
title: Свойство Size (поток ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Size
helpviewer_keywords:
- Size property [ADO Stream]
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e52d05cdbc0fe0ca397c3a7b417fec72703b8e1d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67916919"
---
# <a name="size-property-ado-stream"></a>Свойство Size (объект Stream ADO)
Указывает размер потока в байтах.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает значение **типа Long** , указывающее размер потока в байтах. Значение по умолчанию — размер потока, или-1, если размер потока неизвестен.  
  
## <a name="remarks"></a>Remarks  
 **Размер** можно использовать только с объектами открытого [потока](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
> [!NOTE]
>  Любое количество битов может храниться в объекте **потока** , ограниченном только системными ресурсами. Если **поток** содержит больше разрядов, чем может быть представлено **длинным** значением, то **Размер** усекается и, следовательно, неточно представляет длину **потока**.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство Size (объект Parameter ADO)](../../../ado/reference/ado-api/size-property-ado-parameter.md)
