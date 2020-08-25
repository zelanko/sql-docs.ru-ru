---
description: Метод WriteText
title: Метод WriteText | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_WriteText
- _Stream::WriteText
helpviewer_keywords:
- WriteText method [ADO]
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 9a4e42733013a7ea756924199d05a93ae08e0c08
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776833"
---
# <a name="writetext-method"></a>Метод WriteText
Записывает указанную текстовую строку в объект [потока](./stream-object-ado.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *Данные*  
 **Строковое** значение, содержащее текст в символах для написания.  
  
 *Параметры*  
 Необязательный элемент. Значение [стреамвритинум](./streamwriteenum.md) , указывающее, должен ли символ разделителя строки записываться в конце указанной строки.  
  
## <a name="remarks"></a>Remarks  
 Указанные строки записываются в объект **потока** без промежуточных пробелов или символов между строками.  
  
 Текущей [позиции](./position-property-ado.md) присваивается символ, следующий за записанными данными. Метод **WriteText** не усекает остальные данные в потоке. Если вы хотите усечь эти символы, вызовите [сетеос](./seteos-method.md).  
  
 Если вы пишете после текущей позиции [EOS](./eos-property.md) , [Размер](./size-property-ado-stream.md) **потока** будет увеличен, чтобы вместить новые символы, а **EOS** перейдет к новому байтовому байту в **потоке**.  
  
> [!NOTE]
>  Метод **WriteText** используется с потоками текста ([Type](./type-property-ado-stream.md) — **адтипетекст**). Для двоичных потоков (**Type** — **Адтипебинари**) используйте [Write](./write-method.md).  
  
## <a name="applies-to"></a>Применение  
 [Объект Stream (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Write](./write-method.md)