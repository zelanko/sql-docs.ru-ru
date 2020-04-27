---
title: Метод Read | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 992631b8fb3864b6d7404f86d2f65de222f0b1c8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917408"
---
# <a name="read-method"></a>Метод Read
Считывает указанное число байтов из объекта двоичного [потока](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>Параметры  
 *нумбитес*  
 Необязательный параметр. Значение **типа Long** , указывающее количество байтов для чтения из файла или значения [стреамреаденум](../../../ado/reference/ado-api/streamreadenum.md) **адреадалл**, которое является значением по умолчанию.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод **Read** считывает указанное число байтов или весь поток из объекта **потока** и возвращает результирующие данные в виде **Variant**.  
  
## <a name="remarks"></a>Remarks  
 Если *нумбитес* больше числа байтов, остающихся в **потоке**, возвращаются только оставшиеся байты. Чтение данных не дополняется в соответствии с длиной, заданной параметром *нумбитес*. Если не осталось байтов для чтения, возвращается Variant со значением NULL. **Чтение** не может быть использовано для чтения в обратном направлении.  
  
> [!NOTE]
>  *Нумбитес* всегда измеряет байты. Для объектов текстового **потока** ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) — **адтипетекст**) используйте [ReadText](../../../ado/reference/ado-api/readtext-method.md).  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод ReadText](../../../ado/reference/ado-api/readtext-method.md)
