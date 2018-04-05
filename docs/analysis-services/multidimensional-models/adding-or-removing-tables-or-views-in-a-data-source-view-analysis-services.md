---
title: Добавление или удаление таблиц или представлений в данных источника (службы Analysis Services) | Документы Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: fe054e5e7378c7b779164961aaa46f1c4e6377d5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a>Добавление или удаление таблиц или представлений в представлении источника данных (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]После создания представления источника данных (DSV) в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], может изменить его в конструкторе представлений источников данных, добавив или удалив таблицы и столбцы, включая таблицы и столбцы из другого источника данных.  
  
 Чтобы открыть представление источника данных (DSV) в конструкторе представлений источников данных, дважды щелкните DSV в обозревателе решений. После открытия представления источников данных для его изменения или расширения можно использовать команду **Добавить или удалить таблицы** на панели кнопок или в меню. Также можно использовать объекты диаграммы. Например, можно выбрать объект и нажать клавишу «Delete» на клавиатуре для удаления объекта.  
  
> [!WARNING]  
>  Будьте внимательны при удалении таблицы. При удалении таблицы удаляются все соответствующие столбцы и связи из представления источников данных (DSV), а все объекты, связанные с таблицей, становятся недействительными.  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a>Выбор таблиц и представлений для добавления или удаления  
 С помощью диалогового окна **Добавление или удаление таблиц** можно перемещать таблицы или представления между списками **Доступные объекты** и **Включенные объекты** . Список **Доступные объекты** изначально включает все таблицы или представления в первичном источнике данных, которые пока не включены в представление источника данных. Если первичный источник данных поддерживает функцию **OPENROWSET** , то в проект или базу данных также можно добавлять таблицы или представления из других источников данных.  
  
 При добавлении или удалении таблицы из представление источника данных (DSV) осуществляется добавление или удаление таблицы в текущую выбранную диаграмму в DSV. Дополнительные сведения о диаграммах см. в разделе [Работа с диаграммами в конструкторе представлений источника данных (службы Analysis Services)](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md).  
  
 После перемещения таблицы в список **Включенные объекты** в диалоговом окне **Добавление или удаление таблиц** можно добавить все связанные таблицы. При этой операции таблицы добавляются в соответствии с ограничениями внешних ключей в источнике данных, если такие ограничения существуют. При отсутствии ограничений внешних ключей можно использовать свойство **NameMatchingCriteria** представления источников данных для определения связей, указывая критерий для сопоставления имен столбцов в таблицах для формирования вероятных связей. Если для представления источников данных задано свойство **NameMatchingCriteria**, нажмите кнопку **Добавить связанные таблицы** , чтобы добавить таблицы из источника данных, имеющих совпадающие имена столбцов. Дополнительные сведения о задании свойства **NameMatchingCriteria** см. в разделе [Представления источников данных в многомерных моделях](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
> [!NOTE]  
>  Добавление или удаление объектов в представлении источника данных не влияет на базовый источник данных.  
  
## <a name="see-also"></a>См. также:  
 [Представления источников данных в многомерных моделях](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Работа с диаграммами в конструкторе представлений источника данных (службы Analysis Services)](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
