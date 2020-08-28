---
description: Метод SkipLine
title: Метод Скиплине | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 840c0111aca8b202fd081d3f0250d17fd43e5bbb
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989055"
---
# <a name="skipline-method"></a>Метод SkipLine
Пропускает одну целую строку при чтении текстового [потока](./stream-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>Remarks  
 Все символы до и включительно разделитель следующей строки пропускаются. По умолчанию [LineSeparator](./lineseparator-property-ado.md) имеет значение **адкрлф**. Если вы попытаетесь пропустить предыдущие [EOS](./eos-property.md), текущее расположение останется в **EOS**.  
  
 Метод **скиплине** используется с текстовыми потоками ([тип](./type-property-ado-stream.md) — **адтипетекст**).  
  
## <a name="applies-to"></a>Применение  
 [Объект Stream (ADO)](./stream-object-ado.md)