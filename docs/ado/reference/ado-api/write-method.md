---
title: "Напишите метод | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- _Stream::raw_Write
- _Stream::Write
helpviewer_keywords:
- Write method [ADO]
ms.assetid: 02982e6a-ac5f-4af2-b82e-ce12534b84b2
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6adf96fa3fd1135727a55a8c7e26351942f886c4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="write-method"></a>Write, метод
Записывает двоичные данные в [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>Параметры  
 *Буфер*  
 Объект **Variant** , содержащий массив байтов для записи.  
  
## <a name="remarks"></a>Замечания  
 Указанный байт **поток** объектом, не вмешиваясь пробелами каждого байта.  
  
 Текущий [позиции](../../../ado/reference/ado-api/position-property-ado.md) задано значение байт после записанные данные. **Записи** метод не приводит к усечению до конца данных в виде потока. Если нужно усечь эти байты, вызов [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Если записи за пределами текущего [электрической ПЕРЕГРУЗКИ](../../../ado/reference/ado-api/eos-property.md) положение, [размер](../../../ado/reference/ado-api/size-property-ado-stream.md) из **поток** будет возрастать содержать каких-либо новых байтов и **электрической ПЕРЕГРУЗКИ** переместит новый последний байт в **поток**.  
  
> [!NOTE]
>  **Записи** метод используется с двоичные потоки ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeBinary**). Для текстовыми потоками (**тип** — **adTypeText**), используйте [WriteText](../../../ado/reference/ado-api/writetext-method.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект потока (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Метод WriteText](../../../ado/reference/ado-api/writetext-method.md)

