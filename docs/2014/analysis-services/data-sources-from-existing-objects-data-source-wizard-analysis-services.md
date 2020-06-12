---
title: Источники данных из существующих объектов (мастер источников данных) (Analysis Services) | Документация Майкрософт
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
ms.openlocfilehash: d5884cd7315ce7d2ab88a38900f9bb8b5ae22508
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528980"
---
# <a name="data-sources-from-existing-objects-data-source-wizard-analysis-services"></a>Источники данных из существующих объектов (мастер источников данных) (службы Analysis Services)
  Используйте страницу **Источники данных из существующих объектов** для определения существующего источника данных или проекта, на котором будет основан новый источник данных.  
  
## <a name="options"></a>Варианты  
 **Создать источник данных, основанный на существующем источнике данных из вашего решения**  
 Выберите, если нужно создать новый источник данных на основе уже существующего источника данных в решении. Когда создается, обновляется или развертывается проект, использующий новый источник данных, новый источник данных получает настройки источника данных, определенного выбором этого параметра.  
  
 **Источник данных**  
 Из списка источников данных, сгруппированных по проектам, выберите источник данных, на основе которого нужно создать новый источник.  
  
 **Создать источник данных на основе проекта служб Analysis Services**  
 Выберите, чтобы создать новый источник данных, ссылающийся на другой [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] проект в текущем решении. Новый источник данных заимствует настройки из свойств `TargetServer` и `TargetDatabase` выбранного проекта. Когда создается, обновляется или развертывается проект, использующий новый источник данных, новый источник данных получает настройки источника данных, определенного выбором этого параметра.  
  
 **Project**  
 Выберите проект, на который будет ссылаться новый источник данных.  
  
## <a name="see-also"></a>См. также:  
 [Справка F1 мастера источников данных &#40;Analysis Services&#41;](data-source-wizard-f1-help-analysis-services.md)   
 [Источники данных в многомерных моделях](multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Поддерживаемые источники данных &#40;многомерные&#41;SSAS](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
