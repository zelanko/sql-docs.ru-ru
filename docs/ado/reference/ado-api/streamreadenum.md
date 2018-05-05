---
title: StreamReadEnum | Документы Microsoft
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
- StreamReadEnum
helpviewer_keywords:
- StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99a38cd3fb2fd58c021113fa99f5b3b52fbb865a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="streamreadenum"></a>StreamReadEnum
Указывает, должны ли считываться весь поток или следующую строку из [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|По умолчанию. Считывает все байты из потока, начиная с текущей позиции, начиная с [электрической ПЕРЕГРУЗКИ](../../../ado/reference/ado-api/eos-property.md) маркера. Это допустимо только **StreamReadEnum** значение с двоичные потоки ([тип](../../../ado/reference/ado-api/type-property-ado-stream.md) — **adTypeBinary**).|  
|**adReadLine**|-2|Считывает следующую строку из потока (обозначенный [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) свойство).|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Метод Read](../../../ado/reference/ado-api/read-method.md)|[Метод ReadText](../../../ado/reference/ado-api/readtext-method.md)|
