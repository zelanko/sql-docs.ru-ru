---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 64b7d8fd3f2220562e3695d6e31c83261daa2e60
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947498"
---
# <a name="writetext-method"></a>Метод WriteText
Записывает указанную текстовую строку в объект [потока](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *Data*  
 **Строковое** значение, содержащее текст в символах для написания.  
  
 *Параметры*  
 Необязательный параметр. Значение [стреамвритинум](../../../ado/reference/ado-api/streamwriteenum.md) , указывающее, должен ли символ разделителя строки записываться в конце указанной строки.  
  
## <a name="remarks"></a>Remarks  
 Указанные строки записываются в объект **потока** без промежуточных пробелов или символов между строками.  
  
 Текущей [позиции](../../../ado/reference/ado-api/position-property-ado.md) присваивается символ, следующий за записанными данными. Метод **WriteText** не усекает остальные данные в потоке. Если вы хотите усечь эти символы, вызовите [сетеос](../../../ado/reference/ado-api/seteos-method.md).  
  
 Если вы пишете после текущей позиции [EOS](../../../ado/reference/ado-api/eos-property.md) , [Размер](../../../ado/reference/ado-api/size-property-ado-stream.md) **потока** будет увеличен, чтобы вместить новые символы, а **EOS** перейдет к новому байтовому байту в **потоке**.  
  
> [!NOTE]
>  Метод **WriteText** используется с потоками текста ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) — **адтипетекст**). Для двоичных потоков (**Type** — **Адтипебинари**) используйте [Write](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Метод Write](../../../ado/reference/ado-api/write-method.md)
