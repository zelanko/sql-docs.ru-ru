---
title: Разрешения сущности (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4219830c82710861ee7b079ce78d1b5859681753
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65479533"
---
# <a name="entity-permissions-master-data-services"></a>Разрешения сущности (службы Master Data Services)
  Разрешения сущности применяются:  
  
-   ко всем атрибутам сущности, в том числе к атрибутам **Имя** и **Code**, для конечных и для консолидированных элементов;  
  
-   ко всем коллекциям сущности;  
  
-   к членству и связям явной иерархии.  
  
 При наличии разрешения для сущности пользователь может добавлять и удалять элементы из сущности, ее явных иерархий и коллекций.  
  
> [!NOTE]  
>  Эти разрешения применяются только к функциональной области **Обозреватель** пользовательского интерфейса.  
  
|Разрешение|Описание|  
|----------------|-----------------|  
|**Только для чтения**|Сущность отображается, но пользователь не может добавлять, удалять или изменять элементы.|  
|**Update**|Сущность отображается, пользователь может добавлять, удалять и изменять элементы.|  
|**Запретить**|Сущность не отображается.|  
  
## <a name="see-also"></a>См. также  
 [Назначение разрешения для объекта модели (службы Master Data Services)](assign-model-object-permissions-master-data-services.md)   
 [Разрешения объекта модели (службы Master Data Services)](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Сущности (службы Master Data Services)](../../2014/master-data-services/entities-master-data-services.md)  
  
  
