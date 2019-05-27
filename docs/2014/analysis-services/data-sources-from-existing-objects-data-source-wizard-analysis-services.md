---
title: Источники данных из существующих объектов (мастер источников данных) (службы Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourcewizard.specifyobject.f1
ms.assetid: e6ef6dea-9db8-45c4-8959-f9febd7caf7b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5576e997023e5a00cdecc3c2079ce387c7062ebb
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66082378"
---
# <a name="data-sources-from-existing-objects-data-source-wizard-analysis-services"></a>Источники данных из существующих объектов (мастер источников данных) (службы Analysis Services)
  Используйте страницу **Источники данных из существующих объектов** для определения существующего источника данных или проекта, на котором будет основан новый источник данных.  
  
## <a name="options"></a>Параметры  
 **Создать источник данных на основе существующего источника данных в решении**  
 Выберите, если нужно создать новый источник данных на основе уже существующего источника данных в решении. Когда создается, обновляется или развертывается проект, использующий новый источник данных, новый источник данных получает настройки источника данных, определенного выбором этого параметра.  
  
 **Источник данных**  
 Из списка источников данных, сгруппированных по проектам, выберите источник данных, на основе которого нужно создать новый источник.  
  
 **Создать источник данных на основе проекта служб Analysis Services**  
 Выберите, чтобы создать новый источник данных со ссылкой на другой проект служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в текущем решении. Новый источник данных заимствует настройки из свойств `TargetServer` и `TargetDatabase` выбранного проекта. Когда создается, обновляется или развертывается проект, использующий новый источник данных, новый источник данных получает настройки источника данных, определенного выбором этого параметра.  
  
 **Проект**  
 Выберите проект, на который будет ссылаться новый источник данных.  
  
## <a name="see-also"></a>См. также  
 [Справка F1 мастера источников данных &#40;служб Analysis Services&#41;](data-source-wizard-f1-help-analysis-services.md)   
 [Источники данных в многомерных моделях](multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Источники данных, поддерживаемые &#40;многомерные службы SSAS&#41;](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
