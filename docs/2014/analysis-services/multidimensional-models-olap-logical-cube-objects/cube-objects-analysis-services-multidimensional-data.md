---
title: Объекты Cube (Analysis Services-многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], objects
ms.assetid: 5cee362e-3f95-4467-bc6c-29b1518ecbf3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0e6dfb75be696ab26893e668b99dc36c7340f86c
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545318"
---
# <a name="cube-objects-analysis-services---multidimensional-data"></a>Объекты куба (службы Analysis Services — многомерные данные)
    
## <a name="introducing-cube-objects"></a>Знакомство с объектами куба  
 Простой <xref:Microsoft.AnalysisServices.Cube> объект состоит из следующих основных сведений, измерений и групп мер. Основная информация включает имя куба по умолчанию, меру куба, источник данных, режим хранения и др.  
  
 Коллекция Dimensions содержит фактический набор измерений из коллекции измерений базы данных, используемых в данном кубе. Все измерения должны быть определены в коллекции измерений базы данных, прежде чем на них можно будет ссылаться в кубе. Закрытые измерения недоступны в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Группы мер — это множество мер в кубе. Группа мер представляет собой коллекцию мер, которые имеют общее представление источника данных и общее множество измерений. Группа мер — это единица обработки мер; группы мер могут обрабатываться отдельно, а затем просматриваться.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|||  
|-|-|  
|Раздел||  
|[Действия (службы Analysis Services — многомерные данные)](../multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[Aggregations and Aggregation Designs](aggregations-and-aggregation-designs.md)||  
|[Вычисления](calculations.md)||  
|[Ячейки куба &#40;Analysis Services многомерных данных&#41;](cube-cells-analysis-services-multidimensional-data.md)||  
|[Свойства куба](cube-properties-multidimensional-model-programming.md)||  
|[Хранилище Куба &#40;Analysis Services многомерных данных&#41;](cube-storage-analysis-services-multidimensional-data.md)||  
|[Переводы куба](cube-translations.md)||  
|[Связи измерений](dimension-relationships.md)||  
|[Ключевые показатели эффективности в многомерных моделях](../multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[Меры и их группы](../multidimensional-models/measures-and-measure-groups.md)||  
|[Секции (службы Analysis Services — многомерные данные)](partitions-analysis-services-multidimensional-data.md)||  
|[Перспективы](perspectives.md)||  
  
  
