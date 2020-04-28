---
title: Метод Скиплине | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931048"
---
# <a name="skipline-method"></a>Метод SkipLine
Пропускает одну целую строку при чтении текстового [потока](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>Remarks  
 Все символы до и включительно разделитель следующей строки пропускаются. По умолчанию [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) имеет значение **адкрлф**. Если вы попытаетесь пропустить предыдущие [EOS](../../../ado/reference/ado-api/eos-property.md), текущее расположение останется в **EOS**.  
  
 Метод **скиплине** используется с текстовыми потоками ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **адтипетекст**).  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
