---
title: Метод SetEOS | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 027468926d444b25e60ede18bbfb26ff7cedf729
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711411"
---
# <a name="seteos-method"></a>Метод SetEOS
Задает позиции, которая конец потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Примечания  
 **SetEOS** обновляет значение [EOS](../../../ado/reference/ado-api/eos-property.md) свойство, сделав текущего [позиции](../../../ado/reference/ado-api/position-property-ado.md) конец потока. Любой байт или символов после текущей позиции, усекаются.  
  
 Так как [записи](../../../ado/reference/ado-api/write-method.md), [WriteText](../../../ado/reference/ado-api/writetext-method.md), и [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) не приводит к усечению любые дополнительные значения в существующих **Stream** объекты, их можно было усечь байт или символов, задав новое положение окончания потока с **SetEOS**.  
  
> [!CAUTION]
>  Если задать **EOS** на позицию перед Фактическое окончание потока, все данные будут утеряны после создания нового **EOS** позиции.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
