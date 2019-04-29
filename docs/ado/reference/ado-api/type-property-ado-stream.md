---
title: Введите свойства (ADO Stream) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Type
- _Stream::get_Type
- _Stream::put_Type
helpviewer_keywords:
- Type property [ADO Stream]
ms.assetid: f6a17e8c-7a28-48d0-bded-76b9e0cf7639
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e4df670c5fe6ca42015e7e85445dafde47738f1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63042633"
---
# <a name="type-property-ado-stream"></a>Свойство Type (объект Stream ADO)
Указывает тип данных, содержащихся в [Stream](../../../ado/reference/ado-api/stream-object-ado.md) (двоичные или текстовые).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md) значение, указывающее тип данных, содержащихся в **Stream** объекта. Значение по умолчанию — **adTypeText**. Тем не менее, если изначально двоичные данные записываются в новый, пустой **Stream**, **тип** будет изменен на **adTypeBinary**.  
  
## <a name="remarks"></a>Примечания  
 **Тип** свойство доступно для чтения/записи только в том случае, если текущая позиция находится в начале **Stream** ([позиции](../../../ado/reference/ado-api/position-property-ado.md) равно 0) и только для чтения в любом другом месте.  
  
 **Тип** свойство определяет, какие методы следует использовать для чтения и записи **Stream**. Для текста **потоки**, использовать [ReadText](../../../ado/reference/ado-api/readtext-method.md) и [WriteText](../../../ado/reference/ado-api/writetext-method.md). Для двоичного файла **потоки**, использовать [чтения](../../../ado/reference/ado-api/read-method.md) и [записи](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство RecordType (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Свойство Type (ADO)](../../../ado/reference/ado-api/type-property-ado.md)
