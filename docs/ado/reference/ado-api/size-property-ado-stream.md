---
description: Свойство Size (объект Stream ADO)
title: Свойство Size (поток ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: dc2f09b6c5f6fd784ab5c4ca29a7596b838e38fb
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989105"
---
# <a name="size-property-ado-stream"></a>Свойство Size (объект Stream ADO)
Указывает размер потока в байтах.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает значение **типа Long** , указывающее размер потока в байтах. Значение по умолчанию — размер потока, или-1, если размер потока неизвестен.  
  
## <a name="remarks"></a>Remarks  
 **Размер** можно использовать только с объектами открытого [потока](./stream-object-ado.md) .  
  
> [!NOTE]
>  Любое количество битов может храниться в объекте **потока** , ограниченном только системными ресурсами. Если **поток** содержит больше разрядов, чем может быть представлено **длинным** значением, то **Размер** усекается и, следовательно, неточно представляет длину **потока**.  
  
## <a name="applies-to"></a>Применение  
 [Объект Stream (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Size (объект Parameter ADO)](./size-property-ado-parameter.md)