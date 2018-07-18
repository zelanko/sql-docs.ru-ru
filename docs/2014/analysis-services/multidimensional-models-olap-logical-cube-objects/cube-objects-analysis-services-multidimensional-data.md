---
title: Объекты (службы Analysis Services — многомерные данные) куба | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], objects
ms.assetid: 5cee362e-3f95-4467-bc6c-29b1518ecbf3
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d722b34679ccef20a939fc505e735886e7f16d1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282226"
---
# <a name="cube-objects-analysis-services---multidimensional-data"></a>Объекты куба (службы Analysis Services — многомерные данные)
    
## <a name="introducing-cube-objects"></a>Знакомство с объектами куба  
 Простой <xref:Microsoft.AnalysisServices.Cube> представляет собой объект: основные сведения, измерениями и группами мер. Основная информация включает имя куба по умолчанию, меру куба, источник данных, режим хранения и др.  
  
 Коллекция Dimensions содержит фактический набор измерений из коллекции измерений базы данных, используемых в данном кубе. Все измерения должны быть определены в коллекции измерений базы данных, прежде чем на них можно будет ссылаться в кубе. Закрытые измерения недоступны в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Группы мер — это множество мер в кубе. Группа мер представляет собой коллекцию мер, которые имеют общее представление источника данных и общее множество измерений. Группа мер — это единица обработки мер; группы мер могут обрабатываться отдельно, а затем просматриваться.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|||  
|-|-|  
|Раздел||  
|[Действия &#40;службы Analysis Services — многомерные данные&#41;](../multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[Агрегаты и статистические схемы](aggregations-and-aggregation-designs.md)||  
|[Вычисления](calculations.md)||  
|[Ячеек куба &#40;службы Analysis Services — многомерные данные&#41;](cube-cells-analysis-services-multidimensional-data.md)||  
|[Свойства куба](cube-properties-multidimensional-model-programming.md)||  
|[Хранилище куба &#40;службы Analysis Services — многомерные данные&#41;](cube-storage-analysis-services-multidimensional-data.md)||  
|[Переводы куба](cube-translations.md)||  
|[Связи измерений](dimension-relationships.md)||  
|[Ключевые показатели эффективности &#40;ключевые показатели эффективности&#41; в многомерных моделях](../multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[Меры и их группы](../multidimensional-models/measures-and-measure-groups.md)||  
|[Секции &#40;службы Analysis Services — многомерные данные&#41;](partitions-analysis-services-multidimensional-data.md)||  
|[Перспективы](perspectives.md)||  
  
  
