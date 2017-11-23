---
title: "Метод WriteText | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::raw_WriteText
- _Stream::WriteText
helpviewer_keywords: WriteText method [ADO]
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 489e91a0ca9dcaa6c2ca59bba3117c2c409c9799
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="writetext-method"></a>Метод WriteText
Записывает указанную текстовую строку в [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *Данные*  
 Объект **строка** значение, содержащее текст в символов для записи.  
  
 *Параметры*  
 Необязательно. Объект [StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md) значение, указывающее, является ли символ-разделитель строки должно быть написано в конце указанной строки.  
  
## <a name="remarks"></a>Замечания  
 Указанные строки записываются в **поток** объекта без промежуточных пробелов и символов между каждой строки.  
  
 Текущий [позиции](../../../ado/reference/ado-api/position-property-ado.md) равно символ, следующий записанные данные. **WriteText** метод не приводит к усечению до конца данных в виде потока. Если нужно усечь эти символы, вызовите [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Если записи за пределами текущего [электрической ПЕРЕГРУЗКИ](../../../ado/reference/ado-api/eos-property.md) положение, [размер](../../../ado/reference/ado-api/size-property-ado-stream.md) из **поток** будет увеличиваться до любых новых символов, и **электрической ПЕРЕГРУЗКИ** будет перемещен в новый получения последнего байта в **поток**.  
  
> [!NOTE]
>  **WriteText** метод используется с текстовыми потоками ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeText**). Для двоичных потоков (**тип** — **adTypeBinary**), используйте [записи](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Метод Write](../../../ado/reference/ado-api/write-method.md)
