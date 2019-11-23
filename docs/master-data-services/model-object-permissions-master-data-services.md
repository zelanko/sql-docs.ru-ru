---
title: Разрешения объекта модели
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0243df5cd71ed667219b3e4e1b4a8ff6d1115f25
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727981"
---
# <a name="model-object-permissions-master-data-services"></a>Разрешения объекта модели (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Разрешения объекта модели являются обязательными. Они определяют атрибуты, к которым пользователь может получить доступ в функциональной области **Обозреватель** пользовательского интерфейса.  
  
 Например, если пользователь имеет разрешение **Обновление** в сущности «Продукт», то пользователь может обновлять все атрибуты этой сущности. Если назначено разрешение **Обновление** для одного атрибута, то пользователь может обновлять только этот атрибут.  
  
 Для определения безопасности, назначенной каждому индивидуальному значению атрибута, разрешения объектов модели можно сочетать с разрешениями элементов иерархии, к которым пользователь может получить доступ.  
  
 Чтобы предоставить пользователю доступ для администрирования модели в функциональной области, отличной от **обозревателя**, пользователь должен быть администратором модели, что также требует назначения разрешений администратора для модели объекта. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
 Разрешения на объекты модели назначаются в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] пользовательском интерфейсе (UI) в функциональной области **разрешения пользователей и групп** на вкладке **модели** . На этой вкладке Модель представлена в виде древовидной структуры. При назначении разрешения для объекта дерева это разрешение наследуют все объекты, находящиеся ниже данного узла. Чтобы переопределить наследование разрешений, нужно назначить разрешение отдельным объектам.  
  
 Объектам модели можно назначить сочетание из разрешений на чтение, создание, обновление и удаление, а также запретить их. Если на вкладке **Модели** не будут назначены никакие разрешения, то пользователь не сможет просматривать модели и данные в среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="best-practice"></a>Рекомендации  
 Как правило, рекомендуется назначить разрешение **Все** объекту модели, а затем явно назначить разрешение объектам на нижнем уровне.  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись блога [Security Improvements](https://go.microsoft.com/fwlink/p/?LinkId=615376)(Улучшения безопасности) на портале msdn.com.  
  
## <a name="see-also"></a>См. также статью  
 [Назначение разрешения для объекта модели (службы Master Data Services)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения модели (службы Master Data Services)](../master-data-services/model-permissions-master-data-services.md)   
 [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md)   
 [Разрешения на элементы иерархии (службы Master Data Services)](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Способ определения разрешений (службы Master Data Services)](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
