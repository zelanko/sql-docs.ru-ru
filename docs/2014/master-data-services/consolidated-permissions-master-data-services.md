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
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6fbc636a4dcf67b6bdeaa17088405ffe079e50d9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096964"
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
|**Запретить**|Атрибут не отображается.<br /><br /> Примечание. Нельзя явно запретить доступ к атрибутам "Имя" и "Код".|  
  
## <a name="see-also"></a>См. также  
 [Назначение разрешений объекта модели &#40;службы Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Разрешения конечного элемента &#40;службы Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;службы Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Элементы (службы Master Data Services)](../../2014/master-data-services/members-master-data-services.md)   
 [Атрибуты &#40;службы Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
