---
title: "Добавление или удаление пользовательскую иерархию | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- hierarchies [Analysis Services], adding
- removing hierarchies
- adding hierarchies
- deleting hierarchies
- hierarchies [Analysis Services], removing
ms.assetid: 953818b4-9543-4c01-bb20-1d45ec6dfb91
caps.latest.revision: 51
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b64b9cd9512b07a308574cd4cf398f8ae72a2460
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="user-defined-hierarchies---add-or-delete-a-user-defined-hierarchy"></a>Пользовательские иерархии - Добавление или удаление пользовательской иерархии
  Добавление пользовательской иерархии в измерение и ее удаление производится на вкладке **Структура измерения** конструктора измерений в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 При добавлении пользовательской иерархии она будет недоступна для пользователей до тех пор, пока ее экземпляр не будет создан в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и пока не выполнена обработка измерения. Дополнительные сведения см. в разделах [Базы данных многомерных моделей (службы SSAS)](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md) и [Обработка многомерной модели (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
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
 [Создание пользовательских иерархий](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)  
  
  

