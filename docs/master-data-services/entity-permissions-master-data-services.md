---
title: "Разрешения сущности (Master Data Services) | Документы Microsoft"
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
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 981c150415bed3470b33c29d34ab8e30e0dbf37e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="entity-permissions-master-data-services"></a>Разрешения сущности (службы Master Data Services)
  Разрешения сущности применяются:  
  
-   ко всем атрибутам сущности, в том числе к атрибутам **Имя** и **Code**, для конечных и для консолидированных элементов;  
  
-   ко всем коллекциям сущности;  
  
-   к членству и связям явной иерархии.  
  
 При наличии разрешения для сущности пользователь может добавлять и удалять элементы из сущности, ее явных иерархий и коллекций.  
  
> [!NOTE]  
>  Эти разрешения применяются только к функциональной области **Обозреватель** пользовательского интерфейса.  
  
|Разрешение|Description|  
|----------------|-----------------|  
|**Чтение**|Пользователь может просматривать элементы, атрибуты, членство в иерархии или коллекциях.|  
|**Создание**|Пользователь может создавать элементы и назначать значения атрибутов во время создания.|  
|**Update**|Пользователь может обновлять элементы, атрибуты, членство в иерархии или коллекциях.|  
|**Delete**|Пользователь может удалять элементы.|  
|**Запретить**|Запрет любого доступа к сущности.|  
  
 Разрешения на чтение, создание, обновление и удаление можно использовать в различных комбинациях. Когда назначаются разрешения на создание, обновление и удаление, автоматически добавляется и разрешение на чтение.  
  
## <a name="see-also"></a>См. также:  
 [Назначение разрешений для объекта модели &#40; Службы Master Data Services &#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40; Службы Master Data Services &#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Сущности (службы Master Data Services)](../master-data-services/entities-master-data-services.md)  
  
  
