---
description: Свойство Type (объект Stream ADO)
title: Свойство Type (поток ADO) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5aebb29d8434c152c0a95f04a5eb083847cf9877
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777113"
---
# <a name="type-property-ado-stream"></a>Свойство Type (объект Stream ADO)
Указывает тип данных, содержащихся в [потоке](./stream-object-ado.md) (двоичный или текстовый).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [стреамтипинум](./streamtypeenum.md) , указывающее тип данных, содержащихся в объекте **потока** . Значение по умолчанию — **адтипетекст**. Однако, если двоичные данные изначально записываются в новый пустой **поток**, **Тип** изменится на **адтипебинари**.  
  
## <a name="remarks"></a>Remarks  
 Свойство **Type** доступно только для чтения и записи, если текущая координата находится в начале **потока** (значение[позиции](./position-property-ado.md) равно 0), а в любой другой позиции — только для чтения.  
  
 Свойство**Type** определяет, какие методы следует использовать для чтения и записи **потока**. Для текстовых **потоков**используйте [ReadText](./readtext-method.md) и [WriteText](./writetext-method.md). Для двоичных **потоков**используйте [Чтение](./read-method.md) и [запись](./write-method.md).  
  
## <a name="applies-to"></a>Применение  
 [Объект Stream (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство RecordType (ADO)](./recordtype-property-ado.md)   
 [Свойство Type (ADO)](./type-property-ado.md)