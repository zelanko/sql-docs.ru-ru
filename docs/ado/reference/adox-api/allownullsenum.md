---
title: "AllowNullsEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- AllowNullsEnum
helpviewer_keywords:
- AllowNullsEnum enumeration [ADOX]
ms.assetid: 6acf3689-1a7f-4379-9d7f-df452ccbac27
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2b9bb610e1b3f4a31e29ddee31e569c34528e243
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
