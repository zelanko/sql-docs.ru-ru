---
title: Объекты (службы Analysis Services — многомерные данные) куба | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cada8410f608816272b159c66196fb761e510abe
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="cube-objects-analysis-services---multidimensional-data"></a>Объекты куба (службы Analysis Services — многомерные данные)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
    
## <a name="introducing-cube-objects"></a>Знакомство с объектами куба  
 Простой <xref:Microsoft.AnalysisServices.Cube> состоит из значений: основной информации, измерений и групп мер. Основная информация включает имя куба по умолчанию, меру куба, источник данных, режим хранения и др.  
  
 Коллекция Dimensions содержит фактический набор измерений из коллекции измерений базы данных, используемых в данном кубе. Все измерения должны быть определены в коллекции измерений базы данных, прежде чем на них можно будет ссылаться в кубе. Закрытые измерения доступны не в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Группы мер — это множество мер в кубе. Группа мер представляет собой коллекцию мер, которые имеют общее представление источника данных и общее множество измерений. Группа мер — это единица обработки мер; группы мер могут обрабатываться отдельно, а затем просматриваться.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|||  
|-|-|  
|Раздел||  
|[Действия & #40; Analysis Services — многомерные данные & #41;](../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[Агрегаты и статистические схемы](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)||  
|[Вычисления](../../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)||  
|[Ячейки куба & #40; Analysis Services — многомерные данные & #41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-cells-analysis-services-multidimensional-data.md)||  
|[Свойства куба — программирование многомерной модели](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-properties-multidimensional-model-programming.md)||  
|[Хранилище куба & #40; Analysis Services — многомерные данные & #41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)||  
|[Переводы куба](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)||  
|[Связей измерений](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)||  
|[Ключевые показатели эффективности & #40; Ключевые показатели эффективности & #41; в многомерных моделях](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[Меры и группы мер](../../analysis-services/multidimensional-models/measures-and-measure-groups.md)||  
|[Секций & #40; Analysis Services — многомерные данные & #41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)||  
|[Перспективы](../../analysis-services/multidimensional-models-olap-logical-cube-objects/perspectives.md)||  
  
  
