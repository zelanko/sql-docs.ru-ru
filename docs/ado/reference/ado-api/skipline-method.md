---
title: Метод SkipLine | Документы Microsoft
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
- _Stream::raw_SkipLine
- _Stream::SkipLine
helpviewer_keywords:
- Skipline method [ADO]
ms.assetid: 0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac4551bfe1859e49cfd88326b1223cbac3fc9a23
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="skipline-method"></a>Метод SkipLine
Пропускает один всей строки, при чтении текстового [поток](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>Замечания  
 Пропускаются все символы вплоть до следующего разделитель строк. По умолчанию [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) — **adCRLF**. При попытке пропустить [электрической ПЕРЕГРУЗКИ](../../../ado/reference/ado-api/eos-property.md), текущая позиция останется на **электрической ПЕРЕГРУЗКИ**.  
  
 **SkipLine** метод используется с текстовыми потоками ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeText**).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
