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
ms.openlocfilehash: 36e2b4cacd6636b2580aff1d8c27ea5a3a444906
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813255"
---
# <a name="model-permissions-master-data-services"></a>Разрешения модели (службы Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Разрешения модели применяются ко всем сущностям, явным и производным иерархиям и коллекциям, существующим в модели. Разрешения, назначенные для модели, можно переопределить для любого отдельного объекта.  
  
> [!NOTE]  
>  Если пользователь является администратором модели, то модель отображается во всех функциональных областях пользовательского интерфейса. В противном случае модель отображается только в функциональной области **Обозреватель** . Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
|Разрешение|Описание|  
|----------------|-----------------|  
|**Чтение**|Пользователь может просматривать элементы, атрибуты, членство в иерархии или коллекциях.|  
|**Создание**|Пользователь может создавать элементы и назначать значения атрибутов во время создания.|  
|**Update**|Пользователь может обновлять элементы, атрибуты, членство в иерархии или коллекциях.|  
|**Удалить**|Пользователь может удалять элементы.|  
|**Запретить**|Запрет любого доступа к сущности.|  
|**Администратор**|Административные разрешения для модели. Административные разрешения доступны только на уровне модели.|  
  
 Разрешения на чтение, создание, обновление и удаление можно использовать в различных комбинациях. Когда назначаются разрешения на создание, обновление и удаление, автоматически добавляется и разрешение на чтение.  
  
## <a name="see-also"></a>См. также  
 [Назначение разрешений объекта модели &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Разрешения сущности &#40;Master Data Services&#41;](../master-data-services/entity-permissions-master-data-services.md)   
 [Разрешения коллекции (службы Master Data Services)](../master-data-services/collection-permissions-master-data-services.md)  
  
  
