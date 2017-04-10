---
title: "Добавление группы (службы Master Data Services) | Microsoft Docs"
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
  - "группы [службы Master Data Services], добавление"
  - "добавление групп [службы Master Data Services]"
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Добавление группы (службы Master Data Services)
  Чтобы начать процесс назначения разрешений для веб-приложения, нужно добавить группу в список **Группы** служб [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Прежде чем пользователь группы сможет получить доступ к [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], группе необходимо предоставить разрешения для одной или нескольких функциональных областей и объектов модели.  
  
## Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
### Добавление группы  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  На панели меню страницы **Пользователи** нажмите кнопку **Управление группами**.  
  
3.  Нажмите кнопку **Добавить группы**.  
  
4.  Введите имя группы, предваряемое именем домена Active Directory либо именем сервера в виде *домен\имя_группы* или *компьютер\имя_группы*.  
  
5.  По желанию нажмите кнопку **Проверить имена**.  
  
6.  Нажмите кнопку **ОК**.  
  
    > [!NOTE]  
    >  После первого обращения пользователя к [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] имя пользователя добавляется в список пользователей [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## Следующие шаги  
  
-   [Назначение разрешений для функциональной области (службы Master Data Services)](../master-data-services/assign-functional-area-permissions-master-data-services.md)  
  
## См. также:  
 [Безопасность (службы Master Data Services)](../master-data-services/security-master-data-services.md)  
  
  