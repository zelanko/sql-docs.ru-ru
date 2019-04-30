---
title: Метод CopyTo (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_CopyTo
- _Stream::CopyTo
helpviewer_keywords:
- CopyTo method [ADO]
ms.assetid: b4aa5714-916b-48b8-8b09-cc2708379602
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01b2e7dc8b70c109fc6cf998cec2bbad1147692c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63308911"
---
# <a name="copyto-method-ado"></a>Метод CopyTo (ADO)
Копирует заданное число символов или байтов (в зависимости от [тип](../../../ado/reference/ado-api/type-property-ado-stream.md)) в [Stream](../../../ado/reference/ado-api/stream-object-ado.md) в другой **Stream** объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.CopyTo DestStream, NumChars  
```  
  
#### <a name="parameters"></a>Параметры  
 *destStream*  
 Значение переменной объекта, которое содержит ссылку на открытую **Stream** объекта. Текущий **Stream** копируется в место назначения **Stream** определяется *DestStream*. Назначение **Stream** уже должен быть открыт. Если это не так, возникает ошибка времени выполнения.  
  
> [!NOTE]
>  *DestStream* параметр не может быть прокси-объект **Stream** объекта, так как для этого необходим доступ к интерфейсу частный на **Stream** объект, который не может быть удаленной для клиент.  
  
 *число символов*  
 Необязательный. **Целое число** значение, указывающее количество байт или символов, копируемых из текущей позиции в источнике **Stream** в место назначения **Stream**. Значение по умолчанию — -1, которое указывает, что все символов или байтов, копируются из текущей позицией с целью [EOS](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Примечания  
 Этот метод копирует заданное число символов или байтов, начиная с текущей позиции, заданной параметром [позиции](../../../ado/reference/ado-api/position-property-ado.md) свойство. Если указанное число больше доступного числа байт до **EOS**, а затем только символов или байтов из текущей позицией с целью **EOS** копируются. Если значение *NumChars* равно -1, или этот параметр опущен, всех символов или байтов, начиная с текущей позиции копируются.  
  
 Если существуют символов или байтов в поток назначения, все содержимое после точки, где заканчивается копии остаются, а не усекаются. **Позиция** становится сразу после последнего байта копируются байт. Если вы хотите выполнить усечение эти байты, вызов [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 **CopyTo** следует использовать для копирования данных в целевой объект **Stream** того же типа как источник **Stream** (их **тип** параметры свойств являются оба **adTypeText** или оба **adTypeBinary**). Для текста **Stream** объектов, можно изменить [Charset](../../../ado/reference/ado-api/charset-property-ado.md) свойства назначения **Stream** для преобразования из одной кодировки в другую. Кроме того, текст **Stream** объектов может быть успешно скопирована в двоичный файл **Stream** объекты, но двоичный файл **Stream** не может копироваться объекты в текст **Stream**  объектов.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
