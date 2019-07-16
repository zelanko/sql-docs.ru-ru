---
title: Службы Analysis Services табличной модели безопасности на уровне объекта | Документация Майкрософт
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: d354aa64e8b6a1e98941011c30550a056f4c01c9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162793"
---
# <a name="object-level-security"></a>Безопасность на уровне объекта
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Обеспечение безопасности данных модели начинается с эффективного внедрения [ролей](../../analysis-services/tabular-models/roles-ssas-tabular.md) и фильтры на уровне строк для определения разрешений пользователя относительно данных и объектов модели данных. Начиная с табличными моделями 1400, можно также определить безопасность на уровне объекта, включая безопасность на уровне таблицы и безопасность на уровне столбца в [роли объекта](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl).

## <a name="table-level-security"></a>Безопасность на уровне таблицы

Безопасность на уровне таблицы можно не только ограничить доступ к данным таблиц, но также существует имена конфиденциальных таблиц, помогая не позволить злоумышленникам обнаружить, если для таблицы. 

 Безопасность на уровне таблицы задается в метаданных на основе JSON Model.bim [модели языка скриптов табличной (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference), или [табличной модели объектов (TOM)](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo). Задайте **metadataPermission** свойство **разрешений таблиц** в класс [роли объекта](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl) для **none**.

В этом примере свойство metadataPermission класса разрешений таблиц для таблицы Product имеет значение none для:

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

Аналогичную безопасность на уровне таблицы с помощью безопасности на уровне столбцов можно не только ограничить доступ к столбцу данных, но и имена конфиденциальных столбцов, помогает предотвратить обнаружение столбец пользователей-злоумышленников.

 Безопасность на уровне столбца задается в метаданных на основе JSON Model.bim [модели языка скриптов табличной (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference), или [табличной модели объектов (TOM)](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo). Задайте **metadataPermission** свойство **columnPermissions** в класс [роли объекта](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl) для **none**.

В этом примере свойство metadataPermission класса columnPermissions базовый тариф столбца в таблице Employees присваивается none:

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

*  Безопасность на уровне таблицы нельзя установить для модели, если это нарушает цепочки связей. Во время разработки, формируется ошибка.
 Например если существуют связи между таблицами A и B, а B и C, нельзя защитить таблицы б. Если таблицы Б является защищенным, подключение запроса таблицы объект невозможно связи между таблицей A и B, а B и C. В этом случае можно настроить отдельные связи между таблицами A и B.

    ![Безопасность на уровне таблицы](../../analysis-services/tabular-models/media/ssas-ols.png)  


*  Безопасность на уровне строк и безопасность на уровне объекта нельзя использовать вместе из различных ролей, так как он может привести к непредвиденным доступ к защищенным данным. Во время выполнения запроса для пользователей, которые являются членами сочетание ролей формируется ошибка.

*  Динамические вычисления (меры, ключевые показатели эффективности, DetailRows) автоматически ограничены, если они ссылаются на защищенную таблицу или столбец. Хотя отсутствует механизм явным образом защитить меры, это можно неявно защитить меры, обновив выражение, которое ссылается на защищенную таблицу или столбец.

*  Связи, которые ссылаются на защищенной столбец работать условии столбец находится в таблице, не защищен.




## <a name="see-also"></a>См. также  
[Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
[Объект Roles (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl)  
[Язык сценариев табличной модели (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference)  
[Табличная модель объектов (TOM)](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).

  
