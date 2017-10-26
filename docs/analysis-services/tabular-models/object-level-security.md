---
title: "Безопасность на уровне объекта табличной модели | Документы Microsoft"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: 
ms.assetid: 
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ed695cd15d9e0622ff28ed449395f0684b2cf9f1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="object-level-security"></a>Безопасность на уровне объекта

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Модель безопасности данных начинается с эффективной реализации [ролей](../../analysis-services/tabular-models/roles-ssas-tabular.md) и фильтры уровня строк для определения разрешений пользователя относительно данных и объектов модели данных. Начиная с табличными моделями 1400, можно также определить безопасность на уровне объектов, включая безопасность на уровне таблицы и безопасность на уровне столбцов в [объекта роли](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md).

## <a name="table-level-security"></a>Безопасность на уровне таблицы

С безопасностью на уровне таблицы можно не только ограничить доступ к данным таблицы, но также имена таблиц конфиденциальные, помогает предотвратить пользователей-злоумышленников обнаружения, если таблица существует. 

 Безопасность на уровне таблицы задается в метаданных на основе JSON в Model.bim [табличных языка скриптов модели (TMSL)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md), или [табличной модели объектов (TOM)](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md). Задать **metadataPermission** свойство **разрешений таблиц** класса в [объекта роли](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md) для **нет**.

В этом примере свойство metadataPermission класса разрешений таблиц для таблицы Product задано значение none:

```
"roles": [
  {
    "name": "Users",
    "description": "All allowed users to query the model",
    "modelPermission": "read",
    "tablePermissions": [
      {
        "name": "Product",
        "metadataPermission": "none"
      }
    ]
  }
```

## <a name="column-level-security"></a>Безопасность на уровне столбца

Аналогично безопасность на уровне таблицы с безопасностью на уровне столбцов можно не только ограничить доступ для данных столбца, но имена конфиденциальных столбцов, помогает предотвратить обнаружение столбец пользователей-злоумышленников.

 Безопасность на уровне столбца задается в метаданных на основе JSON в Model.bim [табличных языка скриптов модели (TMSL)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md), или [табличной модели объектов (TOM)](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md). Задать **metadataPermission** свойство **columnPermissions** класса в [объекта роли](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md) для **нет**.

В этом примере свойство metadataPermission класса columnPermissions для столбца в таблице Employees скорость базы задано значение none:

```
"roles": [
  {
    "name": "Users",
    "description": "All allowed users to query the model",
    "modelPermission": "read",
    "tablePermissions": [
      {
        "name": "Employee",
        "columnPermissions": [
          {
            "name": "Base Rate",
            "metadataPermission": "none"
          }
        ]
      }
    ]
  }
```

## <a name="restrictions"></a>Ограничения

*  Не удается установить защиту уровня таблицы для модели, если влекут за собой разрыв цепочки связей. Возникнет ошибка во время разработки.
 Например если существуют связи между таблицами A и B, а B и C, нельзя защитить таблицы б. Не находится под защитой таблицы Б, запроса в таблице А транзитной связей между таблицей A и B, а B и C. В этом случае можно настроить отдельные связи между таблицами A и B.

    ![Безопасность на уровне таблицы](../../analysis-services/tabular-models/media/ssas-ols.png)  


*  Безопасность на уровне строк и безопасности на уровне объекта нельзя использовать вместе с разными ролями, так как он может привести к непредусмотренного доступа к защищенным данным. Возникнет ошибка во время выполнения запроса для пользователей, являющихся членами комбинации ролей.

*  Динамические вычисления (меры, ключевые показатели эффективности, DetailRows) автоматически ограничен, если они ссылаются на защищенную таблицу или столбец. Отсутствует механизм для явного защита меры, его можно неявно защитить меры, обновив выражение для ссылки на защищенной таблицы или столбца.

*  Связи, которые ссылаются на столбцы защищенным работать при условии столбец находится в таблице не защищены.




## <a name="see-also"></a>См. также:  
[Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
[Объект роли (TMSL)](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)  
[Язык сценариев табличной модели (TMSL)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
[Табличная модель объектов (TOM)](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md).

  

