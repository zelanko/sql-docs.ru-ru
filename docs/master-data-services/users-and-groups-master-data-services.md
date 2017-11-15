---
title: "Пользователи и группы (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- users [Master Data Services]
- groups [Master Data Services]
- users [Master Data Services], about users
- groups [Master Data Services], about groups
ms.assetid: ed08dd2d-248e-4b68-91d4-e9961cb50eed
caps.latest.revision: "8"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 50539aba8f6bb6b4a207d3c03a3a1bf6df6a7b62
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="users-and-groups-master-data-services"></a>Пользователи и группы (службы Master Data Services)
  Для доступа к веб-приложению [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] у пользователя должна быть учетная запись домена Windows или учетная запись на сервере, на котором установлены службы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Чтобы предоставить доступ к среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , можно выполнить одно из следующих действий.  
  
-   Добавить учетную запись пользователя в домен или локальную группу и добавить группу в список групп в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
-   Добавить учетную запись пользователя в список пользователей в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
    > [!NOTE]  
    >  Если пользователь принадлежит к группе, имеющей доступ к среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], имя такого пользователя автоматически добавляется в список пользователей, когда пользователь в первый раз обращается к среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] или MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].  
  
 Чтобы выполнять действия в функциональной области **Обозреватель** пользовательского интерфейса, группе или пользователю должен быть назначен доступ к функциональной области **Обозреватель** , а также назначено разрешение на доступ к объектам модели.  
  
 Если пользователю или группе необходим доступ к другим функциональным областям, им должен быть предоставлен доступ к ней.  
  
## <a name="best-practice"></a>Рекомендации  
 Чтобы упростить администрирование, создайте группы и присвойте каждой группе разрешение для функциональных областей и объектов моделей. Затем можно добавлять пользователей в группы и удалять из них, не задействуя пользовательский интерфейс [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
 Не присваивайте отдельным пользователям дополнительные разрешения и не включайте пользователей в несколько групп, имеющих доступ к службам [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Кроме того, не используйте разрешения для элементов иерархии, за исключением случаев, когда группе необходим был ограниченный доступ к определенным элементам.  
  
## <a name="see-also"></a>См. также:  
 [Добавление пользователя (службы Master Data Services)](../master-data-services/add-a-user-master-data-services.md)   
 [Добавление группы (службы Master Data Services)](../master-data-services/add-a-group-master-data-services.md)   
 [Удаление пользователей или групп (службы Master Data Services)](../master-data-services/delete-users-or-groups-master-data-services.md)   
 [Проверка разрешений пользователя (службы Master Data Services)](../master-data-services/test-a-user-s-permissions-master-data-services.md)  
  
  
