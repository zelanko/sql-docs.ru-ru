---
title: "Назначение разрешения для объекта модели (службы Master Data Services) | Microsoft Docs"
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
  - "модели [службы Master Data Services], назначение разрешений объекта"
  - "разрешения [службы Master Data Services], назначения разрешений объекта модели"
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Назначение разрешения для объекта модели (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]назначьте разрешения для объектов модели при необходимости разрешить пользователю или группе доступ к данным в функциональной области **Обозреватель** в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]или при необходимости сделать пользователя или группу администратором.  
  
> [!NOTE]  
>  При назначении разрешения на модель доступ ко всем другим моделям неявно запрещается. Если не будут назначены никакие разрешения, то пользователи и группы не смогут обращаться к данным в **Обозревателе**.  
  
## Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### Назначения разрешений объекта модели  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  На странице **Пользователи** или **Группы** выберите строку пользователя или группы, которые необходимо изменить.  
  
3.  Нажмите **Изменить выделенного пользователя**.  
  
4.  Перейдите на вкладку **Модели** .  
  
5.  По желанию выберите модель из списка **Модель** .  
  
6.  Нажмите кнопку **Изменить**.  
  
7.  Разверните дерево и щелкните объект модели, для которого нужно назначить разрешения.  
  
8.  В меню выберите разрешения на создание, чтение, обновление и удаление или запретите их.  
  
9. На верхнем уровне модели выберите **Администратор** , если необходимо сделать пользователя администратором модели.  
  
10. Нажмите кнопку **Сохранить**.  
  
## Следующие шаги  
  
-   [Назначение разрешений для элемента иерархии (службы Master Data Services)](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md) (необязательно)  
  
## См. также:  
 [Удаление разрешений для объекта модели (службы Master Data Services)](../master-data-services/delete-model-object-permissions-master-data-services.md)   
 [Разрешения объекта модели (службы Master Data Services)](../master-data-services/model-object-permissions-master-data-services.md)   
 [Создание администратора модели (службы Master Data Services)](../master-data-services/create-a-model-administrator-master-data-services.md)  
  
  