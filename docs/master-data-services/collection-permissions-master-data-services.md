---
title: Разрешения коллекции (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], permissions
- permissions [Master Data Services], collections
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: aa360d47553f539438843ab1872fedc270ac1e99
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47749700"
---
# <a name="collection-permissions-master-data-services"></a>Разрешения коллекции (службы основных данных)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Разрешения коллекции применяются ко всем коллекциям для сущности. Нельзя назначить разрешение конкретной коллекции. Разрешения применяются ко всем коллекциям.  
  
> [!NOTE]  
>  Эти разрешения применяются только к функциональной области **Обозреватель** пользовательского интерфейса.  
  
|Разрешение|Описание|  
|----------------|-----------------|  
|**Чтение**|Пользователь может просматривать элементы коллекции и атрибуты элементов.|  
|**Создание**|Пользователь может создавать элементы коллекции и назначать значения атрибутов.|  
|**Update**|Пользователь может обновить элементы коллекции, атрибуты и связи.|  
|**Удаление**|Пользователь может удалять элементы коллекции.|  
|**Запретить**|Запрет любого доступа к элементам коллекции.|  
  
 Разрешения на чтение, создание, обновление и удаление можно использовать в различных сочетаниях. Когда назначается разрешение на создание, обновление или удаление, автоматически добавляется и разрешение на чтение.  
  
## <a name="see-also"></a>См. также:  
 [Назначение разрешения для объекта модели (службы Master Data Services)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Коллекции (службы Master Data Services)](../master-data-services/collections-master-data-services.md)   
 [Разрешения объекта модели (службы Master Data Services)](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
