---
title: Метод SkipLine | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SkipLine
- _Stream::SkipLine
helpviewer_keywords:
- Skipline method [ADO]
ms.assetid: 0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c8439f7d8fabc5675e43fca5bba006b22574b992
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931048"
---
# <a name="skipline-method"></a>Метод SkipLine
Пропускает один всей строки, при чтении текстового [Stream](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>Примечания  
 Пропускаются все символы вплоть до следующей строки используется разделитель строк. По умолчанию [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) — **adCRLF**. При попытке пропустить [EOS](../../../ado/reference/ado-api/eos-property.md), текущая позиция останется на уровне **EOS**.  
  
 **SkipLine** метод используется с текстовыми потоками ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeText**).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
