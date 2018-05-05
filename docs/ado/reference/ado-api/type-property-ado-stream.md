---
title: Type-свойство (поток ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Type
- _Stream::get_Type
- _Stream::put_Type
helpviewer_keywords:
- Type property [ADO Stream]
ms.assetid: f6a17e8c-7a28-48d0-bded-76b9e0cf7639
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 97c244062e7b84da33ae8d437f0f09a1e3dfd302
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="type-property-ado-stream"></a>Свойство Type (поток ADO)
Указывает тип данных, содержащихся в [поток](../../../ado/reference/ado-api/stream-object-ado.md) (двоичный файл или текст).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md) значение, указывающее тип данных, содержащихся в **поток** объекта. Значение по умолчанию — **adTypeText**. Однако, если изначально двоичные данные записываются в новый, пустой **поток**, **тип** будет изменен на **adTypeBinary**.  
  
## <a name="remarks"></a>Замечания  
 **Тип** свойство является чтение и запись только в том случае, если текущее положение находится в начале **поток** ([позиции](../../../ado/reference/ado-api/position-property-ado.md) равно 0) и только для чтения в любом другом месте.  
  
 **Тип** свойство определяет, какие методы следует использовать для чтения и записи **поток**. Для текста **потоки**, используйте [ReadText](../../../ado/reference/ado-api/readtext-method.md) и [WriteText](../../../ado/reference/ado-api/writetext-method.md). Для двоичного файла **потоки**, используйте [чтения](../../../ado/reference/ado-api/read-method.md) и [записи](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство RecordType (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Свойство Type (ADO)](../../../ado/reference/ado-api/type-property-ado.md)
