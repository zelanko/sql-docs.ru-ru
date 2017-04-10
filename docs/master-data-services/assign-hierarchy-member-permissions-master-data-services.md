---
title: "Назначение разрешений для элемента иерархии (службы Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "разрешения [службы Master Data Services], назначение разрешений элемента"
  - "элементы [службы Master Data Services], назначение разрешений"
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Назначение разрешений для элемента иерархии (службы Master Data Services)
  Разрешения для элементов иерархии назначаются, чтобы дать пользователям или группам возможность просматривать данные в функциональной области **Обозреватель** [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Разрешения для элементов иерархии необязательны. Они позволяют детализировать разрешения для объектов модели в случаях, когда это необходимо.  
  
## Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### Назначение разрешений для элементов иерархии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  На странице **Пользователи** или **Группы** выберите строку пользователя или группы, которые необходимо изменить.  
  
3.  Нажмите **Изменить выделенного пользователя**.  
  
4.  Перейдите на вкладку **Элементы иерархии** .  
  
5.  Выберите модель из списка **Модель** .  
  
6.  Выберите версию из списка **Версия** .  
  
7.  Выберите иерархию из списка **Иерархия** .  
  
8.  Нажмите кнопку **Изменить**.  
  
9. Разверните дерево и щелкните узел иерархии, для которого нужно назначить разрешения.  
  
10. В меню выберите сочетание разрешений на **создание**, **чтение, обновление** и **удаление** или **запретите** их.  
  
11. Нажмите кнопку **Сохранить**.  
  
    > [!NOTE]  
    >  Разрешения для элемента иерархии вступают в силу не сразу. См. раздел [Срочное применение разрешения для элемента (службы Master Data Services)](../master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
## См. также:  
 [Удаление разрешений элемента иерархии (службы Master Data Services)](../master-data-services/delete-hierarchy-member-permissions-master-data-services.md)   
 [Назначение разрешения для объекта модели (службы Master Data Services)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Разрешения на элементы иерархии (службы Master Data Services)](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  