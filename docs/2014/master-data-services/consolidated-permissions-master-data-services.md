---
title: Объединенные разрешения (Master Data Services) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], consolidated member attribute permissions
- consolidated members [Master Data Services], attribute permissions
- permissions [Master Data Services], consolidated members
- members [Master Data Services], consolidated member permissions
ms.assetid: 084055a3-5fd3-43f3-b620-ac6afab42a3d
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 91c00dc638369d46986ee3757a6d889ed5a1439f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925416"
---
# <a name="consolidated-permissions-master-data-services"></a>Объединенные разрешения (службы основных данных)
  Объединенные разрешения применяются к значениям атрибутов для всех консолидированных элементов сущности.  
  
 Объединенные разрешения применяются только к сущностям, разрешенным для явных иерархий и коллекций.  
  
 **Примечания.**  
  
-   Разрешения конечного элемента применяются только к функциональной области **Обозреватель** пользовательского интерфейса.  
  
-   Разрешения, назначенные для атрибутов **Имя** и **Код** , не применяются.  
  
|Разрешение|Описание|  
|----------------|-----------------|  
|**Только для чтения**|Консолидированные элементы отображаются, но пользователь не может добавлять, удалять или изменять их.|  
|**Update**|Консолидированные элементы отображаются, и пользователь может добавлять, удалять и изменять их.|  
|**Запретить**|Консолидированные элементы для сущности не отображаются.|  
  
## <a name="attribute-permissions"></a>Разрешения атрибута  
 Разрешения атрибута применимы только к значениям атрибута указанной сущности. Пользователи с разрешениями только для атрибутов не могут добавлять или удалять элементы.  
  
|Разрешение|Описание|  
|----------------|-----------------|  
|**Только для чтения**|Атрибут отображается, но пользователь не может изменить его значений.|  
|**Update**|Атрибут отображается, и пользователь может изменить его значения.|  
|**Запретить**|Атрибут не отображается.<br /><br /> Примечание. Нельзя явно запретить доступ к атрибуты Name и Code.|  
  
## <a name="see-also"></a>См. также  
 [Назначение разрешения для объекта модели (службы Master Data Services)](assign-model-object-permissions-master-data-services.md)   
 [Разрешения конечного элемента &#40;службы Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [Разрешения объекта модели (службы Master Data Services)](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Элементы (службы Master Data Services)](../../2014/master-data-services/members-master-data-services.md)   
 [Атрибуты (службы Master Data Services)](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
