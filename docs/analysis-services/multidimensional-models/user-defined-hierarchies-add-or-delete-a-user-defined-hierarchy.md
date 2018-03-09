---
title: "Добавление или удаление пользовательскую иерархию | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- hierarchies [Analysis Services], adding
- removing hierarchies
- adding hierarchies
- deleting hierarchies
- hierarchies [Analysis Services], removing
ms.assetid: 953818b4-9543-4c01-bb20-1d45ec6dfb91
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a36cc61a153f559edc00c5b50cbd354abdfe7912
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="user-defined-hierarchies---add-or-delete-a-user-defined-hierarchy"></a>Пользовательские иерархии - Добавление или удаление пользовательской иерархии
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Добавление пользовательской иерархии в измерение и ее удаление производится на вкладке **Структура измерения** конструктора измерений в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 При добавлении пользовательской иерархии она будет недоступна для пользователей до тех пор, пока ее экземпляр не будет создан в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и пока не выполнена обработка измерения. Дополнительные сведения см. в разделе [многомерных баз данных модели ](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md) и [обработка многомерной модели &#40; Службы Analysis Services &#41; ](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-add-a-user-defined-hierarchy-to-a-dimension"></a>Добавление пользовательской иерархии к измерению  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте соответствующий проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , а затем откройте нужное измерение.  
  
     Измерение открывается в конструкторе измерений на вкладке **Структура измерения** .  
  
2.  Перетащите атрибут, который хотите использовать в пользовательской иерархии, из панели **Атрибуты** на панель **Иерархии** .  
  
3.  Перетащите дополнительные атрибуты, чтобы сформировать уровни в пользовательской иерархии.  
  
     Порядок, в котором атрибуты перечислены в иерархии, имеет значение. Например, в иерархии времени годы должны находиться выше дней.  
  
4.  При необходимости можно переупорядочить уровни в пользовательской иерархии, перетащив их на соответствующие позиции.  
  
5.  При необходимости измените свойства пользовательской иерархии или ее уровней.  
  
     Например, можно указать имя для пользовательской иерархии, переименовать один или несколько ее уровней и определить пользовательское имя для уровня «Все». Дополнительные сведения см. в разделах [Свойства пользовательской иерархии](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)и [Свойства уровня — пользовательские иерархии](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md).  
  
    > [!NOTE]  
    >  По умолчанию пользовательская иерархия — это просто путь детализации данных для пользователей. Но если между уровнями имеются связи, производительность запросов может быть увеличена путем настройки связей атрибутов между уровнями. Дополнительные сведения см. в разделах [Связи атрибутов](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) и [Определение связей атрибутов](../../analysis-services/multidimensional-models/attribute-relationships-define.md).  
  
### <a name="to-remove-a-user-defined-hierarchy-from-a-dimension"></a>Удаление пользовательской иерархии из измерения  
  
-   На панели **Иерархии** вкладки **Структура измерения** выберите пользовательскую иерархию, которую хотите удалить. На панели инструментов щелкните **Удалить**.  
  
     — или —  
  
-   На панели **Иерархия** щелкните правой кнопкой мыши пользовательскую иерархию, которую необходимо удалить, и выберите **Удалить**.  
  
     — или —  
  
-   Удалите иерархию из области конструктора с помощью мыши.  
  
## <a name="see-also"></a>См. также  
 [Пользовательские иерархии](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [Создание определяемых пользователем иерархий](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)  
  
  
