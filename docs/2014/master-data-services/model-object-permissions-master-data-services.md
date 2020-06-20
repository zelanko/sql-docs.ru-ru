---
title: Разрешения объекта модели (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 754920cac0a832ac5ae1ff8959e710815d68fd70
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971194"
---
# <a name="model-object-permissions-master-data-services"></a>Разрешения объекта модели (службы Master Data Services)
  Разрешения объекта модели являются обязательными. Они определяют атрибуты, к которым пользователь может получить доступ в функциональной области **Обозреватель** пользовательского интерфейса.  
  
 Например, если пользователь имеет разрешение **Обновление** в сущности «Продукт», то пользователь может обновлять все атрибуты этой сущности. Если назначено разрешение **Обновление** для одного атрибута, то пользователь может обновлять только этот атрибут.  
  
 Для определения безопасности, назначенной каждому индивидуальному значению атрибута, разрешения объектов модели можно сочетать с разрешениями элементов иерархии, к которым пользователь может получить доступ.  
  
 Чтобы предоставить пользователю доступ к функциональной области, отличной от **Explorer**, пользователь должен быть администратором модели, который также включает в себя назначение разрешений на объекты модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
 Разрешения объекта модели назначаются в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] пользовательском интерфейсе в функциональной области **разрешения пользователей и групп** на вкладке **модели** . На этой вкладке Модель представлена в виде древовидной структуры. При назначении разрешения для объекта дерева это разрешение наследуют все объекты, находящиеся ниже данного узла. Чтобы переопределить наследование разрешений, нужно назначить разрешение отдельным объектам.  
  
 Разрешение на доступ к объектам модели можно назначить **только для чтения**, **обновления**или **запрета** . Если на вкладке **Модели** не будут назначены никакие разрешения, то пользователь не сможет просматривать модели и данные в среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="best-practice"></a>Рекомендации  
 В общем случае следует назначить разрешение **Update** объекту модели, а затем явным образом назначить разрешение для объектов под ним. Если объектам на нижнем уровне не назначить разрешение, то разрешения будут унаследованы, а пользователь станет администратором.  
  
## <a name="see-also"></a>См. также:  
 [Назначение разрешений объекта модели &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения модели &#40;Master Data Services&#41;](../../2014/master-data-services/model-permissions-master-data-services.md)   
 [Разрешения функциональной области &#40;Master Data Services&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md)   
 [Разрешения элемента иерархии &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Способ определения разрешений (службы Master Data Services)](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
