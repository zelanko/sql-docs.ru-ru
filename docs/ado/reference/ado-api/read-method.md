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
manager: jroth
ms.openlocfilehash: f4594e4b85ad66b1ab11a2966bc7a0d79815db09
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702980"
---
# <a name="read-method"></a>Метод Read
Считывает указанное число байтов из двоичного файла [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>Параметры  
 *NumBytes*  
 Необязательный. Объект **Long** значение, указывающее количество байтов, считываемых из файла или [StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md) значение **adReadAll**, который используется по умолчанию.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Чтения** метод считывает указанное число байтов или весь поток, из **Stream** объекта и возвращает результирующие данные в виде **Variant**.  
  
## <a name="remarks"></a>Примечания  
 Если *NumBytes* остается больше, чем число байтов в **Stream**, возвращаются только оставшихся байтов. Считывание данных не заполняется в соответствии с длиной, определяемой *NumBytes*. Если ни одного байта, доступных для чтения, возвращается значение variant со значением null. **Чтение** не может использоваться для чтения в обратном направлении.  
  
> [!NOTE]
>  *NumBytes* всегда измеряет байт. Для текста **Stream** объектов ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeText**), используйте [ReadText](../../../ado/reference/ado-api/readtext-method.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод ReadText](../../../ado/reference/ado-api/readtext-method.md)
