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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67947498"
---
# <a name="writetext-method"></a>Метод WriteText
Записывает указанную текстовую строку для [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *Data*  
 Объект **строка** значение, содержащее текст записываемых символов.  
  
 *Параметры*  
 Необязательный. Объект [StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md) значение, указывающее ли символ разделителя строки должны записываться в конце указанной строки.  
  
## <a name="remarks"></a>Примечания  
 Указанные строки записываются в **Stream** объекта без промежуточных пробелов или символов между каждой строкой.  
  
 Текущий [позиции](../../../ado/reference/ado-api/position-property-ado.md) устанавливается на символ, следующий записанные данные. **WriteText** метод не вызывает усечение до конца данных в потоке. Для усечения такие символы следует вызвать [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Если записи в за пределами текущего [EOS](../../../ado/reference/ado-api/eos-property.md) позиции, [размер](../../../ado/reference/ado-api/size-property-ado-stream.md) из **Stream** будет увеличено до любых новых символов, и **EOS** будет перемещен в новый последний байт в **Stream**.  
  
> [!NOTE]
>  **WriteText** метод используется с текстовыми потоками ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeText**). Для двоичных потоков (**тип** — **adTypeBinary**), используйте [записи](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Write](../../../ado/reference/ado-api/write-method.md)
