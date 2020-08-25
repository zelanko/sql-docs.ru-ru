---
description: AllowNullsEnum
title: Алловнуллсенум | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7eae546eebef72c7f006e46db8fbba56b4b8a7bc
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771533"
---
# <a name="allownullsenum"></a>AllowNullsEnum
Указывает, индексируются ли записи со значениями NULL.  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|**adIndexNullsAllow**|0|Индекс допускает записи, в которых ключевые столбцы имеют значение null. Если в ключевом столбце введено значение null, запись вставляется в индекс.|  
|**adIndexNullsDisallow**|1|По умолчанию. Индекс не допускает записи, в которых ключевые столбцы имеют значение null. Если в ключевом столбце указано значение null, возникнет ошибка.|  
|**adIndexNullsIgnore**|2|Индекс не вставляет записи, содержащие ключи null. Если в ключевом столбце введено значение null, запись пропускается и ошибка не возникает.|  
|**adIndexNullsIgnoreAny**|4|Индекс не вставляет записи, в которых некоторый ключевой столбец имеет значение null. Для индекса, имеющего ключ с несколькими столбцами, если в каком-либо столбце введено значение null, запись пропускается и ошибка не возникает.|  
  
## <a name="applies-to"></a>Применение  
 [Свойство IndexNulls (ADOX)](./indexnulls-property-adox.md)