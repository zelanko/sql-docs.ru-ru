---
title: "Удаление пользователей или группы (Master Data Services) | Документы Microsoft"
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
- deleting groups [Master Data Services]
- groups [Master Data Services], deleting
- users [Master Data Services], deleting
- deleting users [Master Data Services]
ms.assetid: 0bbf9d2c-b826-48bb-8aa9-9905db6e717f
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5c0a5934afc97b24d884738aa1d6f8c2cc1c80cf
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="delete-users-or-groups-master-data-services"></a>Удаление пользователей или группы (службы Master Data Services)
  Удалите пользователей и группы, если больше не нужно, чтобы они имели доступ к среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Помните о следующих правилах при удалении пользователей и групп.  
  
-   При удалении пользователя, который является членом группы с доступом к [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], у него останется доступ к [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , пока его не удалить из группы Active Directory или локальной группы.  
  
-   При удалении группы все пользователи из этой группы, которые ранее обращались к [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , будут отображаться в списке **Пользователи** , пока они не будут удалены.  
  
-   Изменения безопасности распространяются на MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] спустя 20 минут.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
### <a name="to-delete-users-or-groups"></a>Удаление пользователей или групп  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  Чтобы удалить пользователя, оставайтесь на странице **Пользователи** . Чтобы удалить группу, в строке меню щелкните **Управление группами**.  
  
3.  Выберите в сетке строку для пользователя или группы, которых необходимо удалить.  
  
4.  Нажмите **Удалить выбранного пользователя** или **Удалить выбранную группу**.  
  
5.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Безопасность (службы Master Data Services)](../master-data-services/security-master-data-services.md)  
  
  
