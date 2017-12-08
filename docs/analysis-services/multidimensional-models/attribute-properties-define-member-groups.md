---
title: "Определение групп элементов | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 70a192c25c9271824bcf1ea74c7de68ce0b44651
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="attribute-properties---define-member-groups"></a>Атрибут свойства - определение групп элементов
  Если атрибут содержит большое число элементов, можно сгруппировать их в контейнеры, уменьшая таким образом число элементов, которые будут видеть пользователи при просмотре иерархии данных. Также можно задать число контейнеров, по которым будут группироваться контейнеры, и установить схему именования контейнеров. Дополнительные сведения см. в разделе [Группирование элементов атрибутов (дискретизация)](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md).  
  
 Элементы группируются путем установки свойства **DiscretizationMethod** , доступ к которому можно получить с помощью окна **Свойства** в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Когда создаются группы элементов, изменения не будут доступны пользователям до обработки измерения. Дополнительные сведения см. в разделе [Обработка многомерной модели (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-create-member-groups"></a>Создание групп элементов  
  
1.  Откройте измерение, необходимое для работы. По умолчанию откроется вкладка **Структура измерения** .  
  
2.  В окне **Атрибуты**щелкните правой кнопкой мыши атрибут, элементы которого нужно сгруппировать, а затем выберите пункт **Свойства**.  
  
3.  В раскрывающемся списке рядом с полем **DiscretizationMethod** выберите метод группирования элементов. Дополнительные сведения о настройках **DiscretizationMethod** см. в разделе [Группирование элементов атрибутов (дискретизация)](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md).  
  
  
