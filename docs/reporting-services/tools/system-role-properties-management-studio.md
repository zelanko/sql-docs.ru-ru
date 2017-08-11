---
title: "Свойства системной роли (среда Management Studio) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.reportserver.systemroleproperties.f1
ms.assetid: 0210fc2a-74fb-41dd-8e39-4830047ec417
caps.latest.revision: 30
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 68038228fd6fb7b2af8dd6f1bb5ae50b7f63daac
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="system-role-properties-management-studio"></a>Свойства системной роли (среда Management Studio)
  Страница «Системные роли» используется для просмотра определений системных ролей, определенных в настоящее время для сервера отчетов. Определение системной роли содержит именованную коллекцию задач, которые выполняются применительно ко всему сайту, а не к отдельному объекту. Определения ролей присваиваются пользователям или группам для создания назначения ролей. Задачи в определении ролей задают, какие действия может выполнять пользователь или группа.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]есть две стандартные системные роли: **системный администратор** и **Системный пользователь**. Можно изменять эти определения ролей, изменяя список задач, или создать новую системную роль, поддерживающую другую комбинацию задач. Изменение определения роли влияет на все назначения ролей, включенные в ее определение.  
  
> [!NOTE]  
>  Назначения системных ролей используются только на сервере отчетов, который работает в собственном режиме. Если сервер отчетов настроен для интеграции с SharePoint, эта страница недоступна.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Определяет имя определения системной роли.  
  
 **Description**  
 Отображает описание определения системной роли. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]это описание отображается только на данной странице. Пользователи, просматривающие этот элемент с помощью диспетчера отчетов, могут видеть это описание при просмотре данной иерархии папок.  
  
 **Задача**  
 Выводит список задач на уровне системы, которые можно выбрать для данного определения роли. Можно добавлять или удалять элементы из списка предопределенных задач, чтобы определить, какой доступ к данному элементу будет у пользователей с данной ролью. Нельзя создавать новые задачи или изменять уже существующие.  
  
 **Description**  
 Выводит сведения по каждой из задач. Нельзя изменять описания задач.  
  
## <a name="see-also"></a>См. также раздел  
 [Сервер отчетов в Справка F1 среды Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Задачи системного уровня](../../reporting-services/security/tasks-and-permissions-system-level-tasks.md)   
 [Задачи и разрешения](../../reporting-services/security/tasks-and-permissions.md)   
 [Предопределенные роли](../../reporting-services/security/role-definitions-predefined-roles.md)  
  
  
