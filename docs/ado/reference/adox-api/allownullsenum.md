---
title: "AllowNullsEnum | Документы Microsoft"
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
f1_keywords: AllowNullsEnum
helpviewer_keywords: AllowNullsEnum enumeration [ADOX]
ms.assetid: 6acf3689-1a7f-4379-9d7f-df452ccbac27
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d8dd42fbac84831c2b31247ee5b5279c97ba2ba5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="allownullsenum"></a>AllowNullsEnum
Указывает, проиндексировано ли записи со значениями null.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adIndexNullsAllow**|0|Индекс разрешает операции, в которых ключевые столбцы имеют значение null. Если указано значение null в ключевом столбце, элемент вставляется в индекс.|  
|**adIndexNullsDisallow**|1|По умолчанию. Индекс не допускает записи, в которых ключевые столбцы имеют значение null. Если указано значение null в ключевом столбце, произойдет ошибка.|  
|**adIndexNullsIgnore**|2|Индекс не вставляются в записях, содержащих ключи null. Если указано значение null в ключевом столбце, операция игнорируется, и ошибка не возникает.|  
|**adIndexNullsIgnoreAny**|4|Индекс не вставить записи, где некоторые ключевой столбец имеет значение null. Наличие нескольких столбцов индекса ключа значение null, введенное в какого-либо столбца операция игнорируется и ошибка не возникает.|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство IndexNulls (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
