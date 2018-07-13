---
title: Производные иерархии с явными ограничениями (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], derived hierarchies with explicit caps
- explicit hierarchies, derived hierarchies with explicit caps
- derived hierarchies, derived hierarchies with explicit caps
ms.assetid: 6a82ff66-c137-4757-99bb-787d189b4295
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: dde0270cd369c5074f966978370fd95db14df726
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203574"
---
# <a name="derived-hierarchies-with-explicit-caps-master-data-services"></a>Производные иерархии с явными ограничениями (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]использование уровней явной иерархии в качестве высших уровней производной иерархии называется «производной иерархией с явным ограничением».  
  
 Явная иерархия должна быть основана на той же сущности, что и сущность на вершине производной иерархии.  
  
 В пользовательском интерфейсе [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] такой тип иерархии можно создать, перетащив явную иерархию на вершину производной иерархии.  
  
 ![mds_conc_explicit_cap_UI_structure](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")  
  
## <a name="derived-hierarchy-with-explicit-cap-example"></a>Образец производной иерархии с явным ограничением  
 В данном примере элементы явной иерархии происходят из сущности «Подкатегория». В производной иерархии элементы высшего уровня также происходят из сущности «Подкатегория».  
  
 ![mds_conc_explicit_cap_UI_example](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")  
  
 При использовании явной иерархии на вершине производной иерархии производная иерархия становится неоднородной.  
  
## <a name="rules"></a>Правила  
  
-   В производной иерархии с явным ограничением не может быть больше одной явной иерархии.  
  
-   Одну и ту же явную иерархию можно использовать как ограничение для нескольких производных иерархий.  
  
-   Нельзя назначить разрешения на элементы иерархии производным иерархиям с явными ограничениями. Если назначить разрешение явной иерархии или производной иерархии индивидуально, то разрешение затронет обе иерархии.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание производной иерархии.|[Создание производной иерархии &#40;службы Master Data Services&#41;](create-a-derived-hierarchy-master-data-services.md)|  
|Создание явной иерархии.|[Создание явной иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|  
|Удаление существующей производной иерархии.|[Удаление производной иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|  
|||  
  
## <a name="related-content"></a>См. также  
  
-   [Производные иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
-   [Явные иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
