---
title: Свойство (ADO) положения | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: 7b777179ad83250d9707f7717b5833bbbff4fec7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703410"
---
# <a name="position-property-ado"></a>Свойство Position (ADO)
Указывает текущую позицию внутри [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **Long** значение, указывающее смещение в байтах от начала текущей позиции потока. Значение по умолчанию — 0, которое представляет первый байт в потоке.  
  
## <a name="remarks"></a>Примечания  
 Точку можно переместить текущую позицию после конца потока. Если указать текущую позицию за концом потока, [размер](../../../ado/reference/ado-api/size-property-ado-stream.md) из **Stream** объекта увеличивается соответствующим образом. Любой новый байты, добавляемые в этом случае будет иметь значение null.  
  
> [!NOTE]
>  **Позиция** всегда измеряет байт. Для текстовых потоков с помощью многобайтовые кодировки умножьте положение размер символа для определения количества символов. Например для набора двухбайтовых символов, первый символ находится в позиции 0, второй символ в позиции 2, третий знак в позиции 4 и т. д.  
  
> [!NOTE]
>  Отрицательные значения не может использоваться для изменения текущей позиции в **Stream**. Можно использовать только положительные числа для **позиции**.  
  
> [!NOTE]
>  Для только для чтения **Stream** объектов ADO не возвратит ошибку, если **позиции** присваивается значение больше, чем **размер** из **Stream**. Это не приводит к изменению размера **Stream**, или alter **Stream** содержимое любым способом. Тем не менее, это следует избегать, поскольку это приводит к бессмысленной **позиции**значение.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Charset (ADO)](../../../ado/reference/ado-api/charset-property-ado.md)
