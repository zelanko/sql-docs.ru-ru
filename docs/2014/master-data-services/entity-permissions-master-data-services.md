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
ms.openlocfilehash: 83b489db3e5324febe26da10c980814d5dd50f8f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971504"
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
  
## <a name="see-also"></a>См. также:  
 [Назначение разрешений объекта модели &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Сущности (службы Master Data Services)](../../2014/master-data-services/entities-master-data-services.md)  
  
  
