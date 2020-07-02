---
title: Разрешения коллекции
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], permissions
- permissions [Master Data Services], collections
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: efeb7025d9b0e959aba43cb172cdcb9d36d6c4c9
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811630"
---
# <a name="collection-permissions-master-data-services"></a>Разрешения коллекции (службы основных данных)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Разрешения коллекции применяются ко всем коллекциям для сущности. Нельзя назначить разрешение конкретной коллекции. Разрешения применяются ко всем коллекциям.  
  
> [!NOTE]  
>  Эти разрешения применяются только к функциональной области **Обозреватель** пользовательского интерфейса.  
  
|Разрешение|Описание|  
|----------------|-----------------|  
|**Чтение**|Пользователь может просматривать элементы коллекции и атрибуты элементов.|  
|**Создание**|Пользователь может создавать элементы коллекции и назначать значения атрибутов.|  
|**Update**|Пользователь может обновить элементы коллекции, атрибуты и связи.|  
|**Удалить**|Пользователь может удалять элементы коллекции.|  
|**Запретить**|Запрет любого доступа к элементам коллекции.|  
  
 Разрешения на чтение, создание, обновление и удаление можно использовать в различных сочетаниях. Когда назначается разрешение на создание, обновление или удаление, автоматически добавляется и разрешение на чтение.  
  
## <a name="see-also"></a>См. также  
 [Назначение разрешений объекта модели &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [&#40;коллекций Master Data Services&#41;](../master-data-services/collections-master-data-services.md)   
 [Разрешения объекта модели (службы Master Data Services)](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
