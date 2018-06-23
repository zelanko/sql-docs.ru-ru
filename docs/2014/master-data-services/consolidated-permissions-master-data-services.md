---
title: Консолидированные разрешения (Master Data Services) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [Master Data Services], consolidated member attribute permissions
- consolidated members [Master Data Services], attribute permissions
- permissions [Master Data Services], consolidated members
- members [Master Data Services], consolidated member permissions
ms.assetid: 084055a3-5fd3-43f3-b620-ac6afab42a3d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a0436df9a9aa4f21d9a581172e2874ca2dad6aa6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187782"
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
 [Назначение разрешения объекта модели &#40;службы Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Конечные разрешения &#40;службы Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;службы Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Элементы (службы Master Data Services)](../../2014/master-data-services/members-master-data-services.md)   
 [Атрибуты &#40;службы Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  