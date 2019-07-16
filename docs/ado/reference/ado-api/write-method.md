---
title: Написать метод | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67945908"
---
# <a name="write-method"></a>Метод Write
Записывает двоичные данные в [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>Параметры  
 *буфер*  
 Объект **Variant** , содержащий массив байтов для записи.  
  
## <a name="remarks"></a>Примечания  
 Указанные байты записываются **Stream** объектом, не вмешиваясь пробелами каждый байт.  
  
 Текущий [позиции](../../../ado/reference/ado-api/position-property-ado.md) присваивается байт, следующий записанные данные. **Записи** метод не вызывает усечение до конца данных в потоке. Если вы хотите выполнить усечение эти байты, вызов [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 При написании за текущий [EOS](../../../ado/reference/ado-api/eos-property.md) позиции, [размер](../../../ado/reference/ado-api/size-property-ado-stream.md) из **Stream** будет увеличено до содержат все новые байты и **EOS** будут перемещены новый последний байт в **Stream**.  
  
> [!NOTE]
>  **Записи** метод используется с двоичными потоками ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeBinary**). Для текстовых потоков (**тип** — **adTypeText**), используйте [WriteText](../../../ado/reference/ado-api/writetext-method.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод WriteText](../../../ado/reference/ado-api/writetext-method.md)
