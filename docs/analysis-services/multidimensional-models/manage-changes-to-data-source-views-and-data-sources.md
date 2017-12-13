---
title: "Управление изменениями для представления источников данных и источники данных | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying data sources
- modifying data source views
- data source views [Analysis Services], schema updates
- data sources [Analysis Services], schema updates
ms.assetid: 928c9f63-365a-43fd-9bbd-78828cc7e54d
caps.latest.revision: "25"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: eb5937621d3cb583f599bbcb28bdc635cd12f3a2
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="manage-changes-to-data-source-views-and-data-sources"></a>Управление изменениями в источниках данных и представлениях источников данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]При повторном запуске мастера формирования схем он повторно использует тот же источник данных и представление источника данных, которые он использовал при первоначальном формировании. При добавлении источника данных или представления источников данных мастер не использует их. При удалении оригинального источника данных или представления источников данных после первоначального формирования мастер необходимо запустить с самого начала. Все предыдущие настройки мастера также удаляются. Любые существующие объекты в основной базе данных, связанные с удаленным источником данных или представлением источника данных, при следующем запуске мастера формирования схем воспринимаются как объекты, созданные пользователем.  
  
 Если во время формирования представление источника данных не отражает реального состояния основной базы данных, мастер формирования схем может обнаружить ошибки при формировании схемы для базы данных предметной области. Например, если представление источника данных указывает, что тип данных столбца **int**, но тип данных этого столбца на самом деле **string**, мастер формирования схем устанавливает тип данных для внешнего ключа в **INT** для совпадения с представлением источника данных, а затем выдает сбой при создании связи, поскольку реальный тип данных **string**.  
  
 С другой стороны, при изменении строки соединения с источником данных на другую базу данных по сравнению с предыдущим формированием не возникает ошибки. Используется эта новая база данных, а в предыдущую базу данных не вносятся никакие изменения.  
  
## <a name="see-also"></a>См. также  
 [Основные сведения о добавочном создании](../../analysis-services/multidimensional-models/understanding-incremental-generation.md)  
  
  
