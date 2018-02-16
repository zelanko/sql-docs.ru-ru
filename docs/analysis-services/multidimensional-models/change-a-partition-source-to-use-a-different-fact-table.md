---
title: "Смена источника секции на другую таблицу фактов | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fact tables [Analysis Services]
- partitions [Analysis Services], fact tables
ms.assetid: 5508312f-8e46-4802-9362-6688ca03d098
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ded060a7f5451e7bf0907f40da78d9fb9e95b8dc
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="change-a-partition-source-to-use-a-different-fact-table"></a>Смена источника секции на другую таблицу фактов
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
При создании секции для куба можно использовать различные таблицы фактов. Таблицы могут принадлежать представлению отдельного источника данных, представлениям различных источников данных или различным источникам данных. Представление источника данных также может содержать различные таблицы из нескольких источников данных.  
  
 Все таблицы фактов и измерения для секций куба должны иметь такую же структуру, как таблица фактов и измерения куба. Например, различные таблицы фактов могут иметь одинаковую структуру, но содержать данные за разные годы или для разных линий продукции.  
  
 Укажите таблицу фактов на странице **Определение исходных сведений** мастера секционирования. На этой странице в группе «Источник секции» в списке **Поиск в**укажите источник данных или представление источника данных, в котором требуется выполнить поиск. Затем нажмите кнопку **Найти таблицы**и в разделе **Доступные таблицы**выберите нужные таблицы.  
  
 Если используются различные таблицы фактов, то убедитесь, что данные в секциях не дублируются. Например, если одна таблица фактов содержит транзакции только за 2012 год и другая — за 2013, то эти таблицы содержат независимые данные. Таблицы фактов для отдельных линий продукции или отдельных географических областей также являются независимыми.  
  
 Можно, но не рекомендуется, использовать различные таблицы фактов с дублирующимися данными. В этом случае необходимо использовать фильтры в секциях, чтобы гарантировать, что данные, используемые одной секцией, не используются другой. Дополнительные сведения см. в разделе [Create and Manage a Local Partition &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md).  
  
## <a name="see-also"></a>См. также  
 [Создание и управление локальной секции &#40; Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
  
