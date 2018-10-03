---
title: Разрешения сущности (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 7add4e6562bdfff222bca289af6d7486efe4e8a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193784"
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
 [Назначение разрешений объекта модели &#40;службы Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;службы Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Сущности (службы Master Data Services)](../../2014/master-data-services/entities-master-data-services.md)  
  
  
