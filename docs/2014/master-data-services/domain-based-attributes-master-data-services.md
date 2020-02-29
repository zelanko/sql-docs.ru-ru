---
title: Атрибуты на основе домена (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], about domain-based attributes
- domain-based attributes [Master Data Services]
- attributes [Master Data Services], domain-based attributes
ms.assetid: df6f33ff-97f6-466c-af74-9780b2247473
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: db0e312fabc039de2554f00b7e9f33a7a76ec584
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176063"
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
 Связи между атрибутами на основе домена служат основой для производных иерархий. Дополнительные сведения см. в разделе [Производные иерархии (службы Master Data Services)](derived-hierarchies-master-data-services.md).

## <a name="related-tasks"></a>Связанные задачи

|Описание задачи|Раздел|
|----------------------|-----------|
|Создание нового атрибута на основе домена, источником для которого является существующая сущность.|[Создание атрибута на основе домена &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|
|Создание новой сущности.|[Создание сущности &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)|

## <a name="related-content"></a>См. также

-   [Производные иерархии &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md)

-   [Master Data Services &#40;атрибутов&#41;](../../2014/master-data-services/attributes-master-data-services.md)

-   [Сущности &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md)


