---
title: Разрешения модели
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5e42e54689b5b6a576a24fe57f2f9f4dcaccd1b8
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73728974"
---
# <a name="model-permissions-master-data-services"></a>Разрешения модели (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Разрешения модели применяются ко всем сущностям, явным и производным иерархиям и коллекциям, существующим в модели. Разрешения, назначенные для модели, можно переопределить для любого отдельного объекта.  
  
> [!NOTE]  
>  Если пользователь является администратором модели, то модель отображается во всех функциональных областях пользовательского интерфейса. В противном случае модель отображается только в функциональной области **Обозреватель**. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
|Разрешение|Описание|  
|----------------|-----------------|  
|**Чтение**|Пользователь может просматривать элементы, атрибуты, членство в иерархии или коллекциях.|  
|**Создать**|Пользователь может создавать элементы и назначать значения атрибутов во время создания.|  
|**Update**|Пользователь может обновлять элементы, атрибуты, членство в иерархии или коллекциях.|  
|**Удалить**|Пользователь может удалять элементы.|  
|**Запретить**|Запрет любого доступа к сущности.|  
|**Административный**|Административные разрешения для модели. Административные разрешения доступны только на уровне модели.|  
  
 Разрешения на чтение, создание, обновление и удаление можно использовать в различных комбинациях. Когда назначаются разрешения на создание, обновление и удаление, автоматически добавляется и разрешение на чтение.  
  
## <a name="see-also"></a>См. также статью  
 [Назначение разрешения для объекта модели (службы Master Data Services)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения объекта модели (службы Master Data Services)](../master-data-services/model-object-permissions-master-data-services.md)   
 [Разрешения сущности (службы Master Data Services)](../master-data-services/entity-permissions-master-data-services.md)   
 [Разрешения коллекции (службы Master Data Services)](../master-data-services/collection-permissions-master-data-services.md)  
  
  
