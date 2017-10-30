---
title: "Разрешения модели (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
caps.latest.revision: 6
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 4ae445565c9d115c0d8a7be32fd27dc80c50d19c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="model-permissions-master-data-services"></a>Разрешения модели (службы Master Data Services)
  Разрешения модели применяются ко всем сущностям, явным и производным иерархиям и коллекциям, существующим в модели. Разрешения, назначенные для модели, можно переопределить для любого отдельного объекта.  
  
> [!NOTE]  
>  Если пользователь является администратором модели, то модель отображается во всех функциональных областях пользовательского интерфейса. В противном случае модель отображается только в функциональной области **Обозреватель**. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
|Разрешение|Description|  
|----------------|-----------------|  
|**Чтение**|Пользователь может просматривать элементы, атрибуты, членство в иерархии или коллекциях.|  
|**Создание**|Пользователь может создавать элементы и назначать значения атрибутов во время создания.|  
|**Update**|Пользователь может обновлять элементы, атрибуты, членство в иерархии или коллекциях.|  
|**Delete**|Пользователь может удалять элементы.|  
|**Запретить**|Запрет любого доступа к сущности.|  
|**Административный**|Административные разрешения для модели. Административные разрешения доступны только на уровне модели.|  
  
 Разрешения на чтение, создание, обновление и удаление можно использовать в различных комбинациях. Когда назначаются разрешения на создание, обновление и удаление, автоматически добавляется и разрешение на чтение.  
  
## <a name="see-also"></a>См. также:  
 [Назначение разрешения для объекта модели (службы Master Data Services)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения объекта модели (службы Master Data Services)](../master-data-services/model-object-permissions-master-data-services.md)   
 [Разрешения сущности (службы Master Data Services)](../master-data-services/entity-permissions-master-data-services.md)   
 [Разрешения коллекции (службы Master Data Services)](../master-data-services/collection-permissions-master-data-services.md)  
  
  

