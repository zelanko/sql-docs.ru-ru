---
title: Разрешения модели (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 29269184b63f32c02d2386d0e75757b748c5bd2f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112725"
---
# <a name="model-permissions-master-data-services"></a>Разрешения модели (службы Master Data Services)
  Разрешения модели применяются ко всем сущностям, явным и производным иерархиям и коллекциям, существующим в модели. Разрешения, назначенные для модели, можно переопределить для любого отдельного объекта.  
  
> [!NOTE]  
>  Если пользователь является администратором модели, то модель отображается во всех функциональных областях пользовательского интерфейса. В противном случае модель отображается только в функциональной области **Обозреватель**. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
|Разрешение|Описание|  
|----------------|-----------------|  
|**Только для чтения**|В **Explorer**, модель отображается, но пользователь не может добавлять или удалять членов, а также обновлять значения атрибутов, членство иерархии или коллекции.|  
|**Update**|В **Explorer**, модель отображается и пользователь может добавлять и удалять участников, можно обновить значения атрибутов, членство в иерархии и членство в коллекциях.|  
|**Запретить**|Модель не отображается.|  
  
 При назначении разрешения модели пользователь получает доступ ко всем версиям модели. Нельзя назначить разрешение для отдельной версии.  
  
## <a name="see-also"></a>См. также  
 [Назначение разрешений объекта модели &#40;службы Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;службы Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Разрешения сущности (службы Master Data Services)](../../2014/master-data-services/entity-permissions-master-data-services.md)   
 [Разрешения коллекции (службы Master Data Services)](../../2014/master-data-services/collection-permissions-master-data-services.md)  
  
  
