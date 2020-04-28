---
title: Метод Write | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_Write
- _Stream::Write
helpviewer_keywords:
- Write method [ADO]
ms.assetid: 02982e6a-ac5f-4af2-b82e-ce12534b84b2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 84e10e8edb6cca3c4e56ac1dd0106b3c641af872
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67945908"
---
# <a name="write-method"></a>Метод Write
Записывает двоичные данные в объект [потока](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>Параметры  
 *Двойной*  
 **Значение типа Variant** , содержащее массив байтов для записи.  
  
## <a name="remarks"></a>Remarks  
 Указанные байты записываются в объект **потока** без промежуточных пробелов между каждым байтом.  
  
 Текущей [позицией](../../../ado/reference/ado-api/position-property-ado.md) присваивается байт, следующий за записанными данными. Метод **Write** не усекает остальные данные в потоке. Если вы хотите усечь эти байты, вызовите [сетеос](../../../ado/reference/ado-api/seteos-method.md).  
  
 Если вы пишете после текущей позиции [EOS](../../../ado/reference/ado-api/eos-property.md) , [Размер](../../../ado/reference/ado-api/size-property-ado-stream.md) **потока** будет увеличен, чтобы вместить новые байты, а **EOS** перейдет к новому байтовому байту в **потоке**.  
  
> [!NOTE]
>  Метод **Write** используется с двоичными потоками ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) — **адтипебинари**). Для текстовых потоков (**Type** — **Адтипетекст**) используйте [WriteText](../../../ado/reference/ado-api/writetext-method.md).  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Метод WriteText](../../../ado/reference/ado-api/writetext-method.md)
