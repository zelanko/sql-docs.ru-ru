---
title: "StreamReadEnum | Документы Microsoft"
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
f1_keywords: StreamReadEnum
helpviewer_keywords: StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3d70ab8ad7ecae932688c652667d4d0d2a303239
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="streamreadenum"></a>StreamReadEnum
Указывает, должны ли считываться весь поток или следующую строку из [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|По умолчанию. Считывает все байты из потока, начиная с текущей позиции, начиная с [электрической ПЕРЕГРУЗКИ](../../../ado/reference/ado-api/eos-property.md) маркера. Это допустимо только **StreamReadEnum** значение с двоичные потоки ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeBinary**).|  
|**adReadLine**|-2|Считывает следующую строку из потока (обозначенный [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) свойство).|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Метод Read](../../../ado/reference/ado-api/read-method.md)|[Метод ReadText](../../../ado/reference/ado-api/readtext-method.md)|
