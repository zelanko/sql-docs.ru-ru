---
title: Пользователи и группы (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- users [Master Data Services]
- groups [Master Data Services]
- users [Master Data Services], about users
- groups [Master Data Services], about groups
ms.assetid: ed08dd2d-248e-4b68-91d4-e9961cb50eed
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 73db25d4dca461782e6e648642158c25b6163ddf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164715"
---
# <a name="users-and-groups-master-data-services"></a>Пользователи и группы (службы Master Data Services)
  Для доступа к веб-приложению [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] у пользователя должна быть учетная запись домена Windows или учетная запись на сервере, на котором установлены службы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Чтобы предоставить доступ к среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , можно выполнить одно из следующих действий.  
  
-   Добавить учетную запись пользователя в домен или локальную группу и добавить группу в список групп в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
-   Добавить учетную запись пользователя в список пользователей в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
    > [!NOTE]  
    >  Если пользователь принадлежит к группе, имеющей доступ к среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], имя такого пользователя автоматически добавляется в список пользователей, когда пользователь в первый раз обращается к среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] или MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].  
  
 Чтобы выполнять действия в функциональной области **Обозреватель** пользовательского интерфейса, группе или пользователю должен быть назначен доступ к функциональной области **Обозреватель** , а также назначено разрешение на доступ к объектам модели.  
  
 Если пользователю или группе необходим доступ к другим функциональным областям, то такой пользователь или группа должны быть администратором. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
## <a name="best-practice"></a>Рекомендации  
 Чтобы упростить администрирование, создайте группы и присвойте каждой группе разрешение для функциональных областей и объектов моделей. Затем можно добавлять пользователей в группы и удалять из них, не задействуя пользовательский интерфейс [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
 Не присваивайте отдельным пользователям дополнительные разрешения и не включайте пользователей в несколько групп, имеющих доступ к службам [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Кроме того, не используйте разрешения для элементов иерархии, за исключением случаев, когда группе необходим был ограниченный доступ к определенным элементам.  
  
## <a name="see-also"></a>См. также  
 [Добавление пользователя &#40;службы Master Data Services&#41;](../../2014/master-data-services/add-a-user-master-data-services.md)   
 [Добавление группы (службы Master Data Services)](../../2014/master-data-services/add-a-group-master-data-services.md)   
 [Удаление пользователей или групп (службы Master Data Services)](../../2014/master-data-services/delete-users-or-groups-master-data-services.md)   
 [Проверка разрешений пользователя (службы Master Data Services)](../../2014/master-data-services/test-a-user-s-permissions-master-data-services.md)  
  
  
