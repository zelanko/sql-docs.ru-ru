---
description: Метод Read
title: Метод Read | Документация Майкрософт
ms.prod: sql
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Stream::raw_Read
- _Stream::Read
helpviewer_keywords:
- Read method [ADO]
ms.assetid: 838502de-80f1-4eeb-8838-dd3d9403e567
author: rothja
ms.author: jroth
ms.openlocfilehash: 7c2b2b1579beb967ec75b5a0b32532b846640b01
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88772723"
---
# <a name="read-method"></a>Метод Read
Считывает указанное число байтов из объекта двоичного [потока](./stream-object-ado.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>Параметры  
 *нумбитес*  
 Необязательный элемент. Значение **типа Long** , указывающее количество байтов для чтения из файла или значения [стреамреаденум](./streamreadenum.md) **адреадалл**, которое является значением по умолчанию.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод **Read** считывает указанное число байтов или весь поток из объекта **потока** и возвращает результирующие данные в виде **Variant**.  
  
## <a name="remarks"></a>Remarks  
 Если *нумбитес* больше числа байтов, остающихся в **потоке**, возвращаются только оставшиеся байты. Чтение данных не дополняется в соответствии с длиной, заданной параметром *нумбитес*. Если не осталось байтов для чтения, возвращается Variant со значением NULL. **Чтение** не может быть использовано для чтения в обратном направлении.  
  
> [!NOTE]
>  *Нумбитес* всегда измеряет байты. Для объектов текстового **потока** ([Type](./type-property-ado-stream.md) — **адтипетекст**) используйте [ReadText](./readtext-method.md).  
  
## <a name="applies-to"></a>Применение  
 [Объект Stream (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод ReadText](./readtext-method.md)