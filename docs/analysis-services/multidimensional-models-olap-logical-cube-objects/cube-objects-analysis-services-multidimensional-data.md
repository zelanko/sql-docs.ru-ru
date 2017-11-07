---
title: "Объекты (службы Analysis Services — многомерные данные) куба | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- cubes [Analysis Services], objects
ms.assetid: 5cee362e-3f95-4467-bc6c-29b1518ecbf3
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 018739c4f8da237c1a90a101b96888a8583349be
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="cube-objects-analysis-services---multidimensional-data"></a>Объекты куба (службы Analysis Services — многомерные данные)
    
## <a name="introducing-cube-objects"></a>Знакомство с объектами куба  
 Простой <xref:Microsoft.AnalysisServices.Cube> состоит из значений: основной информации, измерений и групп мер. Основная информация включает имя куба по умолчанию, меру куба, источник данных, режим хранения и др.  
  
 Коллекция Dimensions содержит фактический набор измерений из коллекции измерений базы данных, используемых в данном кубе. Все измерения должны быть определены в коллекции измерений базы данных, прежде чем на них можно будет ссылаться в кубе. Закрытые измерения доступны не в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Группы мер — это множество мер в кубе. Группа мер представляет собой коллекцию мер, которые имеют общее представление источника данных и общее множество измерений. Группа мер — это единица обработки мер; группы мер могут обрабатываться отдельно, а затем просматриваться.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|||  
|-|-|  
|Раздел||  
|[Действия (службы Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[Агрегаты и статистические схемы](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)||  
|[Вычисления](../../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)||  
|[Ячейки куба &#40; Analysis Services — многомерные данные &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-cells-analysis-services-multidimensional-data.md)||  
|[Свойства куба - многомерной модели программирования](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-properties-multidimensional-model-programming.md)||  
|[Хранилище куба &#40; Analysis Services — многомерные данные &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)||  
|[Переводы куба](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)||  
|[Связей измерений](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)||  
|[Ключевые показатели эффективности в многомерных моделях](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[Меры и группы мер](../../analysis-services/multidimensional-models/measures-and-measure-groups.md)||  
|[Секции (службы Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)||  
|[Перспективы](../../analysis-services/multidimensional-models-olap-logical-cube-objects/perspectives.md)||  
  
  

