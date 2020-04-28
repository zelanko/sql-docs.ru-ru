---
title: Свойство "позиционирование" (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Position
helpviewer_keywords:
- Position property [ADO]
ms.assetid: daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dba8636f07b88f1c05d465b844376c6ef3e61240
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931658"
---
# <a name="position-property-ado"></a>Свойство Position (ADO)
Указывает текущую точку в объекте [потока](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Long** , указывающее смещение (в байтах) текущей позиции от начала потока. Значение по умолчанию — 0, представляющее первый байт в потоке.  
  
## <a name="remarks"></a>Remarks  
 Текущую позицию можно переместить в точку после конца потока. Если указать текущую точку после конца потока, [Размер](../../../ado/reference/ado-api/size-property-ado-stream.md) объекта **потока** будет увеличиваться соответствующим образом. Все новые байты, добавленные таким образом, будут иметь значение null.  
  
> [!NOTE]
>  **Расположение** всегда измеряет байты. Для текстовых потоков, использующих многобайтовые кодировки, умножьте позиции на размер символов, чтобы определить номер символа. Например, для кодировки с двумя байтами первый символ находится в позиции 0, второй символ в позиции 2, третий символ в позиции 4 и т. д.  
  
> [!NOTE]
>  Отрицательные значения нельзя использовать для изменения текущей позицией в **потоке**. Для **позиций**можно использовать только положительные числа.  
  
> [!NOTE]
>  Для объектов **потока** , доступного только для чтения, ADO не возвращает ошибку **, если параметру value задано** значение, **Size** превышающее размер **потока**. Это не изменяет размер **потока**или не изменяет содержимое **потока** каким бы то ни было. Однако это следует избегать, так как оно приводит **к бессмысленному**значению.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство Charset (ADO)](../../../ado/reference/ado-api/charset-property-ado.md)
