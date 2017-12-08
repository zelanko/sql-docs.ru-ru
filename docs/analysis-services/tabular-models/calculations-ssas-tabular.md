---
title: "Вычисления (табличные службы SSAS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 738816e3-0e1d-44a5-8d1b-81068dce8ac0
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e65847285ccfd187c0dd58824a46d1dea1271a34
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="calculations-ssas-tabular"></a>Вычисления (табличные службы SSAS)
  После импорта данных в модель можно добавить вычисления для агрегации, фильтрации, расширения, объединения и защиты этих данных. В табличных моделях используется язык выражений анализа данных (DAX) — новый язык формул для создания пользовательских вычислений. В табличных моделях вычисления, которые можно создать с помощью формул DAX, используются в *вычисляемых столбцах*, *мерах*и *фильтрах строк*.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Основные сведения о DAX в табличных моделях (табличные службы SSAS)](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)|Описывает язык формул выражений анализа данных (DAX), используемый для создания вычислений для вычисляемых столбцов, мер и фильтров строк в табличных моделях.|  
|[Совместимость формул в режиме DirectQuery (службы SQL Server Analysis Services)](http://msdn.microsoft.com/en-us/981b6a68-434d-4db6-964e-d92f8eb3ee3e)|Описывает различия, перечисляет функции, неподдерживаемые в режиме DirectQuery, а также функции, которые поддерживаются, но могут возвратить отличающиеся результаты.|  
|[Справочник по выражениям анализа данных (DAX)](http://msdn.microsoft.com/en-us/70a82136-0926-4a91-bcb3-e18e82593b0d)|Этот раздел содержит подробное описание синтаксиса языка выражений анализа данных (DAX), операторов и функций.|  
  
> [!NOTE]  
>  В этом разделе не содержатся пошаговые примеры создания вычислений. Так как вычисления задаются в вычисляемых столбцах, мерах и фильтрах строк (в ролях), указания по созданию формул DAX приведены в связанных с этими элементами задачах. Дополнительные сведения см. в разделе [Создание вычисляемого столбца (табличные службы SSAS)](../../analysis-services/tabular-models/ssas-calculated-columns-create-a-calculated-column.md), [Создание мер и управление ими (табличные службы SSAS)](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md) и [Создание ролей и управление ими (табличные службы SSAS)](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md).  
  
> [!NOTE]  
>  Хотя выражения DAX могут использоваться для осуществления запросов к табличной модели служб, тематика этого раздела связана именно с использованием формул DAX при создании вычислений.  
  
  
