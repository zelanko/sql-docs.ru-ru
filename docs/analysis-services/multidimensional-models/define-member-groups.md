---
title: "Определение групп элементов | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "группы элементов [службы Analysis Services]"
  - "группирование элементов"
  - "DiscretizationMethod, свойство"
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
caps.latest.revision: 36
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Определение групп элементов
  Если атрибут содержит большое число элементов, можно сгруппировать их в контейнеры, уменьшая таким образом число элементов, которые будут видеть пользователи при просмотре иерархии данных. Также можно задать число контейнеров, по которым будут группироваться контейнеры, и установить схему именования контейнеров. Дополнительные сведения см. в разделе [Группирование элементов атрибутов (дискретизация)](../../analysis-services/multidimensional-models/group-attribute-members-discretization.md).  
  
 Элементы группируются путем установки свойства **DiscretizationMethod** , доступ к которому можно получить с помощью окна **Свойства** в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Когда создаются группы элементов, изменения не будут доступны пользователям до обработки измерения. Дополнительные сведения см. в разделе [Обработка многомерной модели (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
### Создание групп элементов  
  
1.  Откройте измерение, необходимое для работы. По умолчанию откроется вкладка **Структура измерения** .  
  
2.  В окне **Атрибуты** щелкните правой кнопкой мыши атрибут, элементы которого нужно сгруппировать, а затем выберите пункт **Свойства**.  
  
3.  В раскрывающемся списке рядом с полем **DiscretizationMethod** выберите метод группирования элементов. Дополнительные сведения о настройках **DiscretizationMethod** см. в разделе [Группирование элементов атрибутов (дискретизация)](../../analysis-services/multidimensional-models/group-attribute-members-discretization.md).  
  
  