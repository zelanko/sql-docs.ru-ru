---
title: "CopyTo-метод (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::raw_CopyTo
- _Stream::CopyTo
helpviewer_keywords:
- CopyTo method [ADO]
ms.assetid: b4aa5714-916b-48b8-8b09-cc2708379602
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e929ff331d1bc99aac75018fa28e0da200f7f529
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="copyto-method-ado"></a>CopyTo-метод (ADO)
Копирует заданное число символов или байтов (в зависимости от [тип](../../../ado/reference/ado-api/type-property-ado-stream.md)) в [поток](../../../ado/reference/ado-api/stream-object-ado.md) в другой **поток** объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.CopyTo DestStream, NumChars  
```  
  
#### <a name="parameters"></a>Параметры  
 *DestStream*  
 Значение объекта переменной, содержит ссылку на открытый **поток** объекта. Текущий **поток** скопирован в место назначения **поток** заданные *DestStream*. Назначение **поток** уже должен быть открыт. Если нет, то во время выполнения возникает ошибка.  
  
> [!NOTE]
>  *DestStream* параметр не может быть прокси-объект **поток** объекта, так как для этого необходим доступ к частный **поток** объект, который не может быть удаленной для клиент.  
  
 *NumChars*  
 Необязательно. **Целое** значение, указывающее количество байт или символов, копируемых из текущей позиции в источнике **поток** в место назначения **поток**. Значение по умолчанию — 1, что указывает, что всех символов или байтов, копируются из текущей позицией с целью [электрической ПЕРЕГРУЗКИ](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Remarks  
 Этот метод копирует заданное число символов или байтов, начиная с текущей позиции, указанной параметром [позиции](../../../ado/reference/ado-api/position-property-ado.md) свойство. Если заданное число больше, чем количество доступных байтов до **электрической ПЕРЕГРУЗКИ**, а затем только символов или байтов, начиная с текущей позиции для **электрической ПЕРЕГРУЗКИ** копируются. Если значение *NumChars* – 1, или этот параметр опущен, всех символов или байтов, начиная с текущей позиции, копируются.  
  
 Если существуют символов или байтов в поток назначения, все содержимое после точки, где заканчивается копии остаются, а не усекаются. **Позиция** становится сразу после получения последнего байта копируются байт. Если нужно усечь эти байты, вызов [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 **CopyTo** следует использовать для копирования данных в назначение **поток** того же типа, как источник **поток** (их **тип** заданы оба Свойства**adTypeText** или оба **adTypeBinary**). Для текста **поток** объектов, можно изменить [Charset](../../../ado/reference/ado-api/charset-property-ado.md) значение свойства назначения **поток** для преобразования из одной кодировки в другую. Кроме того, текст **поток** объекты можно успешно скопированы в двоичное **поток** объектов, но двоичный файл **поток** объекты нельзя скопировать в текстовый **потока**  объектов.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
