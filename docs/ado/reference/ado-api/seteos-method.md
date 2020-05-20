---
title: Метод Сетеос | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 9dbe2846674d760163fa9eb3ab78e07e68b80d0e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759900"
---
# <a name="seteos-method"></a>Метод SetEOS
Задает расположение, которое является концом потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Remarks  
 **Сетеос** обновляет значение свойства [EOS](../../../ado/reference/ado-api/eos-property.md) , делая текущей [позицией](../../../ado/reference/ado-api/position-property-ado.md) конец потока. Все байты или символы, следующие за текущей позицией, усекаются.  
  
 Поскольку [Write](../../../ado/reference/ado-api/write-method.md), [WriteText](../../../ado/reference/ado-api/writetext-method.md)и [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) не усекаются какие-либо лишние значения в существующих объектах **потока** , можно усечь эти байты или символы, установив новую точку конца потока с помощью **сетеос**.  
  
> [!CAUTION]
>  Если задать для **EOS** расположение до фактического конца потока, будут потеряны все данные после новой точки **EOS** .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
