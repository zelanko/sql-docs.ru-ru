---
title: Хранилище измерений | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], storage
- storing data [Analysis Services]
- storage [Analysis Services], dimensions
- relational OLAP
- multidimensional OLAP
- MOLAP
- storing data [Analysis Services], dimensions
- ROLAP
ms.assetid: 8d74b932-2174-4e1f-8414-636455880b6a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ce5bf2a376712d603be3099f7ccefa0e6b799219
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62728497"
---
# <a name="dimension-storage"></a>Хранение измерений
  Измерения в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают два режима хранения:  
  
-   Реляционный OLAP (ROLAP)  
  
-   Многомерный OLAP (MOLAP)  
  
 Режим хранения определяет место и форму данных измерения. MOLAP — режим хранения измерений по умолчанию. **См. также:**[режимы хранения секций и обработка](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
## <a name="molap"></a>MOLAP  
 Данные для измерения в режиме MOLAP хранятся в многомерной структуре в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Эта многомерная структура создается и заполняется при обработке измерения. Измерения MOLAP обеспечивают более высокую производительность, чем измерения ROLAP.  
  
## <a name="rolap"></a>ROLAP  
 Данные для измерения, использующего режим ROLAP, фактически хранятся в таблицах, используемых для определения измерения. Режим хранения ROLAP можно использовать для крупных измерений без дублирования больших объемов данных, однако, это приведет к потере производительности запроса. Измерения основаны непосредственно на таблицах в представлении источника данных, используемого для определения измерения, поэтому режим хранения ROLAP также может поддерживать OLAP реального времени.  
  
> [!IMPORTANT]  
>  Если измерение использует режим хранения ROLAP и при этом входит в состав куба, использующего режим хранения MOLAP, все изменения схемы в исходной таблице должны сопровождаться немедленной обработкой куба. В противном случае может возникнуть несогласованность результатов при запросах к кубу. **См**. также[в статье Автоматизация Analysis Services административных задач с помощью служб SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md).  
  
## <a name="see-also"></a>См. также  
 [Режимы хранения и обработка секции](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  
