---
title: "Добавление или удаление таблиц или представлений в данных источника (службы Analysis Services) | Документы Microsoft"
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
f1_keywords:
- sql13.asvs.dsvdesigner.tablespane.f1
helpviewer_keywords:
- deleting tables
- tables [Analysis Services]
- removing tables
- adding tables
- data source views [Analysis Services], tables
- tables [Analysis Services], data source views
ms.assetid: 98307d04-6548-4d7d-9244-2371dd165249
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2b2f865766530f174cc3affe410679f1880e9813
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a>Добавление или удаление таблиц или представлений в представлении источника данных (службы Analysis Services)
  После создания представления источников данных (DSV) в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]можно изменить его в конструкторе представлений источников данных, добавляя или удаляя таблицы и столбцы, в том числе из других источников данных.  
  
 Чтобы открыть представление источника данных (DSV) в конструкторе представлений источников данных, дважды щелкните DSV в обозревателе решений. После открытия представления источников данных для его изменения или расширения можно использовать команду **Добавить или удалить таблицы** на панели кнопок или в меню. Также можно использовать объекты диаграммы. Например, можно выбрать объект и нажать клавишу «Delete» на клавиатуре для удаления объекта.  
  
> [!WARNING]  
>  Будьте внимательны при удалении таблицы. При удалении таблицы удаляются все соответствующие столбцы и связи из представления источников данных (DSV), а все объекты, связанные с таблицей, становятся недействительными.  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a>Выбор таблиц и представлений для добавления или удаления  
 С помощью диалогового окна **Добавление или удаление таблиц** можно перемещать таблицы или представления между списками **Доступные объекты** и **Включенные объекты** . Список **Доступные объекты** изначально включает все таблицы или представления в первичном источнике данных, которые пока не включены в представление источника данных. Если первичный источник данных поддерживает функцию **OPENROWSET** , то в проект или базу данных также можно добавлять таблицы или представления из других источников данных.  
  
 При добавлении или удалении таблицы из представление источника данных (DSV) осуществляется добавление или удаление таблицы в текущую выбранную диаграмму в DSV. Дополнительные сведения о диаграммах см. в разделе [Работа с диаграммами в конструкторе представлений источника данных (службы Analysis Services)](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md).  
  
 После перемещения таблицы в список **Включенные объекты** в диалоговом окне **Добавление или удаление таблиц** можно добавить все связанные таблицы. При этой операции таблицы добавляются в соответствии с ограничениями внешних ключей в источнике данных, если такие ограничения существуют. При отсутствии ограничений внешних ключей можно использовать свойство **NameMatchingCriteria** представления источников данных для определения связей, указывая критерий для сопоставления имен столбцов в таблицах для формирования вероятных связей. Если для представления источников данных задано свойство **NameMatchingCriteria**, нажмите кнопку **Добавить связанные таблицы** , чтобы добавить таблицы из источника данных, имеющих совпадающие имена столбцов. Дополнительные сведения о задании свойства **NameMatchingCriteria** см. в разделе [Представления источников данных в многомерных моделях](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
> [!NOTE]  
>  Добавление или удаление объектов в представлении источника данных не влияет на базовый источник данных.  
  
## <a name="see-also"></a>См. также  
 [Представления источников данных в многомерных моделях](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Работа с диаграммами в конструкторе представлений источника данных (службы Analysis Services)](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  

