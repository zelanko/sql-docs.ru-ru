---
title: "Установите свойство (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: _Stream::Position
helpviewer_keywords: Position property [ADO]
ms.assetid: daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 34f95df4ee5e4ab4ac5c4ce3934ceabe4dacc64f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="position-property-ado"></a>Свойства position (ADO)
Указывает текущую позицию внутри [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **длинные** значение, задающее смещение в байтах от начала текущей позиции в потоке. Значение по умолчанию — 0, представляющее первый байт в поток.  
  
## <a name="remarks"></a>Замечания  
 Можно переместить точку текущую позицию после конца потока. Если указать текущую позицию после конца потока, [размер](../../../ado/reference/ado-api/size-property-ado-stream.md) из **поток** объекта будет увеличено соответствующим образом. Все новые байты, добавляемые в этом случае будет иметь значение null.  
  
> [!NOTE]
>  **Позиция** всегда измеряет байт. Для текста потоков с использованием многобайтовых кодировок умножьте позицию размера символа для определения количества символов. Например для набора символов 2 байта, первый символ находится в положении 0, второй символ в позиции 2, третьего знака в позиции 4 и т. д.  
  
> [!NOTE]
>  Отрицательные значения не может использоваться для изменения текущего положения в **поток**. Можно использовать только положительные числа для **позиции**.  
  
> [!NOTE]
>  Для только для чтения **поток** объектов ADO не возвратит ошибку, если **позиции** задано значение больше **размер** из **поток**. Это не приводит к изменению размера **поток**, или измените **поток** содержимого каким-либо образом. Однако этого следует избегать, поскольку это приводит к бессмысленной **позиции**значение.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство Charset (ADO)](../../../ado/reference/ado-api/charset-property-ado.md)
