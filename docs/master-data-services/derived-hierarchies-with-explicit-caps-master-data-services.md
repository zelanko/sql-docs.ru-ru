---
title: "Производные иерархии с явными ограничениями (службы Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "иерархии [службы Master Data Services], производные иерархии с явными ограничениями"
  - "явные иерархии, производные иерархии с явными ограничениями"
  - "производные иерархии, производные иерархии с явными ограничениями"
ms.assetid: 6a82ff66-c137-4757-99bb-787d189b4295
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Производные иерархии с явными ограничениями (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]использование уровней явной иерархии в качестве высших уровней производной иерархии называется «производной иерархией с явным ограничением».  
  
 Явная иерархия должна быть основана на той же сущности, что и сущность на вершине производной иерархии.  
  
 В пользовательском интерфейсе [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] такой тип иерархии можно создать, перетащив явную иерархию на вершину производной иерархии.  
  
 ![mds_conc_explicit_cap_UI_structure](../master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")  
  
## Образец производной иерархии с явным ограничением  
 В данном примере элементы явной иерархии происходят из сущности «Подкатегория». В производной иерархии элементы высшего уровня также происходят из сущности «Подкатегория».  
  
 ![mds_conc_explicit_cap_UI_example](../master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")  
  
 При использовании явной иерархии на вершине производной иерархии производная иерархия становится неоднородной.  
  
## Правила  
  
-   В производной иерархии с явным ограничением не может быть больше одной явной иерархии.  
  
-   Одну и ту же явную иерархию можно использовать как ограничение для нескольких производных иерархий.  
  
-   Нельзя назначить разрешения на элементы иерархии производным иерархиям с явными ограничениями. Если назначить разрешение явной иерархии или производной иерархии индивидуально, то разрешение затронет обе иерархии.  
  
## Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание производной иерархии.|[Создание производной иерархии (службы Master Data Services)](../master-data-services/create-a-derived-hierarchy-master-data-services.md)|  
|Создание явной иерархии.|[Создание явной иерархии (службы Master Data Services)](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)|  
|Удаление существующей производной иерархии.|[Удаление производной иерархии (службы Master Data Services)](../master-data-services/delete-a-derived-hierarchy-master-data-services.md)|  
|||  
  
## См. также  
  
-   [Производные иерархии (службы Master Data Services)](../master-data-services/derived-hierarchies-master-data-services.md)  
  
-   [Явные иерархии (службы Master Data Services)](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
  