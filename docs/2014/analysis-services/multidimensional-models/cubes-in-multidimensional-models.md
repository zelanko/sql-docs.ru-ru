---
title: Кубы в многомерных моделях | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- OLAP objects [Analysis Services], cubes
- cubes [Analysis Services], about cubes
- cubes [Analysis Services]
- OLAP [Analysis Services], cubes
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4c32903245da975c9a62d6b7600abbe074b19bc2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095124"
---
# <a name="cubes-in-multidimensional-models"></a>Кубы в многомерных моделях
  Куб является многомерной структурой, содержащей сведения для анализа. Главными составными элементами куба являются измерения и меры. Измерения определяют структуру куба, используемую для срезов данных, а меры предоставляют статистически вычисленные числовые значения, представляющие интерес для конечного пользователя. В качестве логической структуры куб позволяет клиентскому приложению получать значения мер в виде ячеек куба, определенных для всех возможных суммарных значений. Ячейка куба определяется пересечением элементов измерения и содержит статистически вычисляемые значения мер в этом конкретном пересечении.  
  
## <a name="benefits-of-using-cubes"></a>Преимущества использования кубов  
 Куб представляет собой единое место, где хранятся все связанные данные для анализа.  
  
## <a name="components-of-cubes"></a>Компоненты кубов  
 Из чего состоит куб:  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Измерения|[Измерения в многомерных моделях](dimensions-in-multidimensional-models.md)|  
|Меры и их группы|[Создание меры и группы мер в многомерных моделях](create-measures-and-measure-groups-in-multidimensional-models.md)|  
|Секции|[Секции в многомерных моделях](partitions-in-multidimensional-models.md)|  
|перспективами|[Перспективы в многомерных моделях](perspectives-in-multidimensional-models.md)|  
|Иерархии|[Создание определяемых пользователем иерархий](user-defined-hierarchies-create.md)|  
|Действия|[Действия в многомерных моделях](actions-in-multidimensional-models.md)|  
|Ключевые показатели эффективности (KPI)|[Ключевые показатели эффективности &#40;ключевые показатели эффективности&#41; в многомерных моделях](key-performance-indicators-kpis-in-multidimensional-models.md)|  
|Вычисления|[Вычисления в многомерных моделях](calculations-in-multidimensional-models.md)|  
|Translations|[Переводы в многомерных моделях](translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Создание куба с помощью мастера кубов](create-a-cube-using-the-cube-wizard.md)|Описывает использование мастера кубов для определения куба, измерений, атрибутов измерения и пользовательских иерархий.|  
|[Создание меры и группы мер в многомерных моделях](create-measures-and-measure-groups-in-multidimensional-models.md)|Описывает процесс определения групп мер.|  
|[Вычисления в многомерных моделях](calculations-in-multidimensional-models.md)|Описывает определение и настройку вычисления в скрипте многомерных выражений.|  
|[Действия в многомерных моделях](actions-in-multidimensional-models.md)|Описывает определение и настройку действия.|  
|[Перспективы в многомерных моделях](perspectives-in-multidimensional-models.md)|Описывает определение и настройку перспективы.|  
|[Определение хранимых процедур](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|Описывает работу с хранимыми процедурами.|  
  
  