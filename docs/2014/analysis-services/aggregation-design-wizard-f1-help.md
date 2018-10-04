---
title: Справка F1 мастера статистических схем | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Aggregation Design Wizard
ms.assetid: 39e23cf1-6405-4fb6-bc14-ba103314362d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9323f9b4fa6655fe72ae70457329c4ffc0d5dec2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150644"
---
# <a name="aggregation-design-wizard-f1-help"></a>Справка F1 мастера статистических схем
  Статистическая обработка повышает производительность, позволяя службам [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] извлекать предварительно вычисленные итоги напрямую из хранилища куба, не загружая данные из базового источника данных и не вычисляя их для каждого запроса.  
  
 Для создания таких схем может быть использован мастер статистических схем. Мастер помогает выполнять следующие этапы:  
  
-   Выбор стандартных или специальных настроек для хранилища и параметров кэша секции, группы мер или куба.  
  
-   Предоставление предполагаемого или фактического числа объектов, на которые ссылается секция, группа мер или куб.  
  
-   Определение статистических параметров и ограничений, чтобы оптимизировать хранилище и повысить производительность запросов, предоставляемых разработанными статистическими схемами.  
  
-   Сохранение и возможность обработки секции, группы мер или куба для создания определяемых статистических схем.  
  
 После использования мастера статистических схем можно использовать мастер оптимизации с учетом использования для проектирования статистических схем на основе вариантов использования пользователями и клиентскими приложениями, которые создают запросы к кубу.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Выбор секций для изменения &#40;мастер статистических схем&#41;](select-partitions-to-modify-aggregation-design-wizard.md)  
  
-   [Просмотр использования статистической обработки &#40;мастер статистических схем&#41;](review-aggregation-usage-aggregation-design-wizard.md)  
  
-   [Определение счетчиков объектов &#40;мастер статистических схем&#41;](specify-object-counts-aggregation-design-wizard.md)  
  
-   [Параметры статистической обработки &#40;мастер статистических схем&#41;](set-aggregation-options-aggregation-design-wizard.md)  
  
-   [Завершение работы мастера &#40;мастер статистических схем&#41;](completing-the-wizard-aggregation-design-wizard.md)  
  
## <a name="see-also"></a>См. также  
 [Агрегаты и статистические схемы](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)   
 [Кубы в многомерных моделях](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Справка F1 мастера оптимизации с учетом использования](usage-based-optimization-wizard-f1-help.md)   
 [Мастера служб Analysis Services &#40;многомерных данных&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
