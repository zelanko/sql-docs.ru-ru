---
title: "Кубы в многомерных моделях | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLAP objects [Analysis Services], cubes
- cubes [Analysis Services], about cubes
- cubes [Analysis Services]
- OLAP [Analysis Services], cubes
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 0b51afe2909197369128b50f70d7afa44a977b34
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="cubes-in-multidimensional-models"></a>Кубы в многомерных моделях
  Куб является многомерной структурой, содержащей сведения для анализа. Главными составными элементами куба являются измерения и меры. Измерения определяют структуру куба, используемую для срезов данных, а меры предоставляют статистически вычисленные числовые значения, представляющие интерес для конечного пользователя. В качестве логической структуры куб позволяет клиентскому приложению получать значения мер в виде ячеек куба, определенных для всех возможных суммарных значений. Ячейка куба определяется пересечением элементов измерения и содержит статистически вычисляемые значения мер в этом конкретном пересечении.  
  
## <a name="benefits-of-using-cubes"></a>Преимущества использования кубов  
 Куб представляет собой единое место, где хранятся все связанные данные для анализа.  
  
## <a name="components-of-cubes"></a>Компоненты кубов  
 Из чего состоит куб:  
  
|Элемент|Description|  
|-------------|-----------------|  
|Измерения|[Измерения в многомерных моделях](../../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)|  
|Меры и их группы|[Создание мер и групп мер в многомерных моделях](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|  
|Секции|[Секции в многомерных моделях](../../analysis-services/multidimensional-models/partitions-in-multidimensional-models.md)|  
|Перспективы|[Перспективы в многомерных моделях](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)|  
|Иерархии|[Создание пользовательских иерархий](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)|  
|Действия|[Действия в многомерных моделях](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)|  
|Ключевые показатели эффективности (KPI)|[Ключевые показатели эффективности в многомерных моделях](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)|  
|вычисления|[Вычисления в многомерных моделях](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|  
|Переводы|[Переводы в многомерных моделях (службы Analysis Services)](../../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Создание куба с помощью мастера кубов](../../analysis-services/multidimensional-models/create-a-cube-using-the-cube-wizard.md)|Описывает использование мастера кубов для определения куба, измерений, атрибутов измерения и пользовательских иерархий.|  
|[Создание мер и групп мер в многомерных моделях](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|Описывает процесс определения групп мер.|  
|[Вычисления в многомерных моделях](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|Описывает определение и настройку вычисления в скрипте многомерных выражений.|  
|[Действия в многомерных моделях](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)|Описывает определение и настройку действия.|  
|[Перспективы в многомерных моделях](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)|Описывает определение и настройку перспективы.|  
|[Определение хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|Описывает работу с хранимыми процедурами.|  
  
  
