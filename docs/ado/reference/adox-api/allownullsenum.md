---
title: AllowNullsEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- AllowNullsEnum
helpviewer_keywords:
- AllowNullsEnum enumeration [ADOX]
ms.assetid: 6acf3689-1a7f-4379-9d7f-df452ccbac27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d1f4f5ce302c6f9e3e28b037c838d452f771114
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63206335"
---
# <a name="allownullsenum"></a>AllowNullsEnum
Указывает, проиндексировано ли записи со значениями null.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adIndexNullsAllow**|0|Индекс допускает операции, в которых ключевые столбцы имеют значение null. Если указано значение null в ключевом столбце, элемент вставляется в индекс.|  
|**adIndexNullsDisallow**|1|По умолчанию. Индекс не поддерживает операции, в которых ключевые столбцы имеют значение null. Если указано значение null в ключевом столбце, произойдет ошибка.|  
|**adIndexNullsIgnore**|2|Индекс не вставляются в записях, содержащих ключи null. Если указано значение null в ключевом столбце, операция игнорируется, и ошибка не возникает.|  
|**adIndexNullsIgnoreAny**|4|Индекс не вставлять записи, где некоторые ключевой столбец имеет значение null. Для индекса с несколькими столбцами ключа, если указанное значение null в некоторых столбцов учитывается операция, и ошибка не возникает.|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство IndexNulls (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
