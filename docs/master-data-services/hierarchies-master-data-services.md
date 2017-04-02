---
title: "Иерархии (службы основных данных) | Microsoft Docs"
ms.custom: ""
ms.date: "04/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "иерархии [службы Master Data Services]"
  - "иерархии [службы Master Data Services], об иерархиях"
ms.assetid: 70dbb1fc-ead7-45be-9552-a45e3ccd8d21
caps.latest.revision: 11
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 11
---
# Иерархии (службы основных данных)
  Иерархия в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]— древовидная структура, которую можно использовать:  
  
-   для группировки схожих элементов с целью систематизации;  
  
-   объединения и сведения элементов для отчетов или анализа.  
  
## Что содержится в иерархиях  
 Каждая иерархия содержит элементы из одной или нескольких сущностей. При добавлении, изменении или удалении элемента все иерархии обновляются. Это гарантирует, что данные будут точными во всех иерархиях. Иерархии также гарантируют, что каждый элемент будет учитываться ровно один раз.  
  
 Если необходимо создать группирование подмножества элементов, рассмотрите возможность использования коллекции. Дополнительные сведения см. в разделе [Коллекции (службы Master Data Services)](../master-data-services/collections-master-data-services.md).  
  
## Виды иерархий  
 Можно создавать разные иерархии для просмотра и систематизации элементов разными способами. Можно создавать:  
  
-   Неоднородные иерархии из единой сущности, которые называются явными иерархиями. Дополнительные сведения см. в разделе [Явные иерархии (службы Master Data Services)](../master-data-services/explicit-hierarchies-master-data-services.md).  
  
-   Иерархии на основе уровней, состоящие из многих сущностей и основанные на существующих связях между сущностями и их атрибутами, которые называются производными иерархиями. Дополнительные сведения см. в разделе [Производные иерархии (службы Master Data Services)](../master-data-services/derived-hierarchies-master-data-services.md).  
  
> [!NOTE]  
>  Все элементы в иерархии должны быть в одной модели.  
  
## Иерархии не являются классификациями  
 Иерархия отличается от классификации. В классификации элементы упорядочены в соответствии с несколькими атрибутами одновременно, а в иерархии — только по одному атрибуту. Классификации может включать один элемент несколько раз, а иерархия имеет только одно вхождение элемента.  
  
 Например, один велосипед может быть упомянут в классификации дважды: один раз, потому что его цвет красный, и один раз, потому что его размер равен 38. В иерархии велосипед включен только один раз, поэтому нужно определить, в соответствии с чем он будет отображаться: с цветом или размером.  
  
## Пример иерархии  
 В следующем примере в иерархии элементы продуктов группируются по элементам подкатегории.  
  
 ![Пример иерархии, сгруппированной по подкатегории](../master-data-services/media/mds-conc-hierarchy.gif "Пример иерархии, сгруппированной по подкатегории")  
  
## Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание явной иерархии.|[Создание явной иерархии (службы Master Data Services)](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)|  
|Создание производной иерархии.|[Создание производной иерархии (службы Master Data Services)](../master-data-services/create-a-derived-hierarchy-master-data-services.md)|  
|Скрытие или удаление уровней в существующей производной иерархии.|[Скрытие или удаление уровней в производной иерархии (службы Master Data Services)](../master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|  
  
## См. также  
  
-   [Явные иерархии (службы Master Data Services)](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [Производные иерархии (службы Master Data Services)](../master-data-services/derived-hierarchies-master-data-services.md)  
  
-   [Рекурсивные иерархии (службы Master Data Services)](../master-data-services/recursive-hierarchies-master-data-services.md)  
  
-   [Производные иерархии с явными ограничениями (службы Master Data Services)](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)  
  
-   [Коллекции (службы Master Data Services)](../master-data-services/collections-master-data-services.md)  
  
  