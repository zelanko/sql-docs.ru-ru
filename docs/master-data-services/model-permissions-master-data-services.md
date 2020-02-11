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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728974"
---
# <a name="model-permissions-master-data-services"></a>Разрешения модели (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Разрешения модели применяются ко всем сущностям, явным и производным иерархиям и коллекциям, существующим в модели. Разрешения, назначенные для модели, можно переопределить для любого отдельного объекта.  
  
> [!NOTE]  
>  Если пользователь является администратором модели, то модель отображается во всех функциональных областях пользовательского интерфейса. В противном случае модель отображается только в функциональной области **Обозреватель** . Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
|Разрешение|Description|  
|----------------|-----------------|  
|**Чтение**|Пользователь может просматривать элементы, атрибуты, членство в иерархии или коллекциях.|  
|**Создания**|Пользователь может создавать элементы и назначать значения атрибутов во время создания.|  
|**Обновляют**|Пользователь может обновлять элементы, атрибуты, членство в иерархии или коллекциях.|  
|**Удаление**|Пользователь может удалять элементы.|  
|**Запретить**|Запрет любого доступа к сущности.|  
|**Группы**|Административные разрешения для модели. Административные разрешения доступны только на уровне модели.|  
  
 Разрешения на чтение, создание, обновление и удаление можно использовать в различных комбинациях. Когда назначаются разрешения на создание, обновление и удаление, автоматически добавляется и разрешение на чтение.  
  
## <a name="see-also"></a>См. также:  
 [Назначение разрешений объекта модели &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Разрешения сущности &#40;Master Data Services&#41;](../master-data-services/entity-permissions-master-data-services.md)   
 [Разрешения коллекции &#40;Master Data Services&#41;](../master-data-services/collection-permissions-master-data-services.md)  
  
  
