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
manager: craigg
ms.openlocfilehash: a3b50db388151de1f5b99d8d9a3f48904e6d7c2c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679892"
---
# <a name="writetext-method"></a>Метод WriteText
Записывает указанную текстовую строку для [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *Данные*  
 Объект **строка** значение, содержащее текст записываемых символов.  
  
 *Параметры*  
 Необязательный параметр. Объект [StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md) значение, указывающее ли символ разделителя строки должны записываться в конце указанной строки.  
  
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
