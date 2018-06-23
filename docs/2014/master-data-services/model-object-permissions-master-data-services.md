---
title: Разрешения объекта модели (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e0e6e04de7c7ed4a483585e6a4228682f0e3a354
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086919"
---
# <a name="model-object-permissions-master-data-services"></a>Разрешения объекта модели (службы Master Data Services)
  Разрешения объекта модели являются обязательными. Они определяют атрибуты, к которым пользователь может получить доступ в функциональной области **Обозреватель** пользовательского интерфейса.  
  
 Например, если пользователь имеет разрешение **Обновление** в сущности «Продукт», то пользователь может обновлять все атрибуты этой сущности. Если назначено разрешение **Обновление** для одного атрибута, то пользователь может обновлять только этот атрибут.  
  
 Для определения безопасности, назначенной каждому индивидуальному значению атрибута, разрешения объектов модели можно сочетать с разрешениями элементов иерархии, к которым пользователь может получить доступ.  
  
 Чтобы предоставить пользователю доступ к функциональной области, отличный от **Explorer**, пользователь должен быть администратором модели, что также требует назначения разрешений объекта модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
 Разрешения объекта модели назначаются в пользовательском интерфейсе [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] в функциональной области **Разрешения пользователей и групп** на вкладке **Модели**. На этой вкладке модель представлена в виде древовидной структуры. При назначении разрешения для объекта дерева это разрешение наследуют все объекты, находящиеся ниже данного узла. Чтобы переопределить наследование разрешений, нужно назначить разрешение отдельным объектам.  
  
 Можно назначить **только для чтения**, **обновление**, или **Deny** разрешения на объекты модели. Если на вкладке **Модели** не будут назначены никакие разрешения, то пользователь не сможет просматривать модели и данные в среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="best-practice"></a>Рекомендации  
 В общем случае следует назначить **обновление** разрешений на объект модели, а затем явно назначить разрешение объектам на нижнем уровне. Если объектам на нижнем уровне не назначить разрешение, то разрешения будут унаследованы, а пользователь станет администратором.  
  
## <a name="see-also"></a>См. также  
 [Назначение разрешения объекта модели &#40;службы Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения модели (службы Master Data Services)](../../2014/master-data-services/model-permissions-master-data-services.md)   
 [Разрешения функциональной области (службы Master Data Services)](../../2014/master-data-services/functional-area-permissions-master-data-services.md)   
 [Разрешения для элементов иерархии &#40;службы Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Способ определения разрешений &#40;службы Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  