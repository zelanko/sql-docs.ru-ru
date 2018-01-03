---
title: "Метод SetEOS | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::raw_SetEOS
- _Stream::SetEOS
helpviewer_keywords: SetEOS method [ADO]
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 82a80499aff8dbe5344847b34dc6f969eb16ccdc
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="seteos-method"></a>Метод SetEOS
Задает позицию конца потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Remarks  
 **SetEOS** обновляет значение [электрической ПЕРЕГРУЗКИ](../../../ado/reference/ado-api/eos-property.md) свойства, делая текущего [позиции](../../../ado/reference/ado-api/position-property-ado.md) конец потока. Любой байт или символов после текущей позиции, усекаются.  
  
 Поскольку [записи](../../../ado/reference/ado-api/write-method.md), [WriteText](../../../ado/reference/ado-api/writetext-method.md), и [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) не приводит к усечению любые дополнительные значения в существующих **поток** объекты, их можно усечь байт или символов, задав новое положение конец потока с **SetEOS**.  
  
> [!CAUTION]
>  Если задать **электрической ПЕРЕГРУЗКИ** позицию перед Фактическое окончание потока, все данные будут утеряны после создания нового **электрической ПЕРЕГРУЗКИ** позиции.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
