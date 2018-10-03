---
title: Атрибуты на основе домена (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], about domain-based attributes
- domain-based attributes [Master Data Services]
- attributes [Master Data Services], domain-based attributes
ms.assetid: df6f33ff-97f6-466c-af74-9780b2247473
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 026860df0d1acdc5c2c6a563c8e96cb504a2e4db
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083224"
---
# <a name="domain-based-attributes-master-data-services"></a>Атрибуты на основе домена (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]атрибут на основе домена — это атрибут, значения которого заполняются элементами другой сущности. Атрибут на основе домена можно представить как ограниченный список. Атрибуты на основе домена не позволяют пользователям вводить недопустимые значения атрибутов. Для задания значения атрибута пользователь должен выбрать его из списка.  
  
## <a name="domain-based-attribute-example"></a>Пример атрибута на основе домена  
 На следующем рисунке сущность Product имеет атрибут на основе домена с именем Subcategory. Атрибут «Подкатегория» заполняется значениями из сущности «Подкатегория».  
  
 Сущность «Подкатегория» имеет атрибут на основе домена с именем «Категория». Атрибут «Категория» заполняется значениями из сущности «Категория».  
  
 ![Атрибуты на основе домена в сущности](../../2014/master-data-services/media/mds-conc-domain-based-attribute-conceptual.gif "Атрибуты на основе домена в сущности")  
  
## <a name="use-same-entity-for-multiple-domain-based-attributes"></a>Использование одной и той же сущности для нескольких атрибутов на основе домена  
 Одну и ту же сущность можно использовать в качестве атрибута на основе домена для нескольких других сущностей. Например, можно создать сущность "ИндикаторДаНет" со следующими элементами: "Да", "Нет" и "Может быть". Можно создать атрибут «ВНаличии» на основе домена и использовать сущность «ИндикаторДаНет» как источник. Также можно создать другой атрибут на основе домена под названием Approved и использовать сущность YesNoIndicator в качестве источника. Каждый раз, когда пользователи должны выбирать из списка членов сущности «ИндикаторДаНет», можно использовать сущность как атрибут на основе домена.  
  
## <a name="domain-based-attributes-form-derived-hierarchies"></a>Атрибуты на основе домена формируют производные иерархии  
 Связи между атрибутами на основе домена служат основой для производных иерархий. Дополнительные сведения см. в разделе [Derived Hierarchies &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Создание нового атрибута на основе домена, источником для которого является существующая сущность.|[Создание атрибута на основе домена &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|Создание новой сущности.|[Создать сущность &#40;службы Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Производные иерархии &#40;службы Master Data Services&#41;](derived-hierarchies-master-data-services.md)  
  
-   [Атрибуты &#40;службы Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
-   [Сущности (службы Master Data Services)](../../2014/master-data-services/entities-master-data-services.md)  
  
  
