---
description: Метод SetEOS
title: Метод Сетеос | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SetEOS
- _Stream::SetEOS
helpviewer_keywords:
- SetEOS method [ADO]
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ebf47bdae6a879a3afe699be36081eb136b700e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989135"
---
# <a name="seteos-method"></a>Метод SetEOS
Задает расположение, которое является концом потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Remarks  
 **Сетеос** обновляет значение свойства [EOS](./eos-property.md) , делая текущей [позицией](./position-property-ado.md) конец потока. Все байты или символы, следующие за текущей позицией, усекаются.  
  
 Поскольку [Write](./write-method.md), [WriteText](./writetext-method.md)и [CopyTo](./copyto-method-ado.md) не усекаются какие-либо лишние значения в существующих объектах **потока** , можно усечь эти байты или символы, установив новую точку конца потока с помощью **сетеос**.  
  
> [!CAUTION]
>  Если задать для **EOS** расположение до фактического конца потока, будут потеряны все данные после новой точки **EOS** .  
  
## <a name="applies-to"></a>Применение  
 [Объект Stream (ADO)](./stream-object-ado.md)