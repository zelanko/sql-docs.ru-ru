---
title: "Добавление группы (Master Data Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups [Master Data Services], adding
- adding groups [Master Data Services]
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f333376223c44056bc8380c705a0289113bcdbd7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="add-a-group-master-data-services"></a>Добавление группы (службы Master Data Services)
  Чтобы начать процесс назначения разрешений для веб-приложения, нужно добавить группу в список **Группы** служб [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Прежде чем пользователь группы сможет получить доступ к [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], группе необходимо предоставить разрешения для одной или нескольких функциональных областей и объектов модели.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
### <a name="to-add-a-group"></a>Добавление группы  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  На панели меню страницы **Пользователи** нажмите кнопку **Управление группами**.  
  
3.  Нажмите кнопку **Добавить группы**.  
  
4.  Введите имя группы, предваряемое именем домена Active Directory либо именем сервера в виде *домен\имя_группы* или *компьютер\имя_группы*.  
  
5.  По желанию нажмите кнопку **Проверить имена**.  
  
6.  Нажмите кнопку **ОК**.  
  
    > [!NOTE]  
    >  После первого обращения пользователя к [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]имя пользователя добавляется в список пользователей [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Назначение разрешений для функциональной области &#40; Службы Master Data Services &#41;](../master-data-services/assign-functional-area-permissions-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Безопасность (службы Master Data Services)](../master-data-services/security-master-data-services.md)  
  
  
