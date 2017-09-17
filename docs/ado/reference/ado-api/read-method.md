---
title: "Метод чтения | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Stream::raw_Read
- _Stream::Read
helpviewer_keywords:
- Read method [ADO]
ms.assetid: 838502de-80f1-4eeb-8838-dd3d9403e567
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 23eeee5244ccb92159c2afbc3ffb55fb586ff2f9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="read-method"></a>Read, метод
Считывает указанное число байтов из двоичного файла [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>Параметры  
 *NumBytes*  
 Необязательно. Объект **длинные** значение, указывающее количество байтов, считываемых из файла или [StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md) значение **adReadAll**, используемого по умолчанию.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Чтения** метод считывает указанное число байтов или всего потока из **поток** объекта и возвращает результирующие данные в виде **Variant**.  
  
## <a name="remarks"></a>Замечания  
 Если *NumBytes* остается больше числа байт в **поток**, возвращаются только оставшихся байтов. Считывание данных не заполняется в соответствии с длиной, определяемой *NumBytes*. Если ни один байт для чтения, возвращается значение variant со значением null. **Чтение** не может использоваться для чтения в обратном направлении.  
  
> [!NOTE]
>  *NumBytes* всегда измеряет байт. Для текста **поток** объектов ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeText**), используйте [ReadText](../../../ado/reference/ado-api/readtext-method.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект потока (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Метод ReadText](../../../ado/reference/ado-api/readtext-method.md)
