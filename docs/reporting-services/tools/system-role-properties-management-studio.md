---
title: Свойства ролей системы (Management Studio) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: ''
ms.component: tools
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.swb.reportserver.systemroleproperties.f1
ms.assetid: 0210fc2a-74fb-41dd-8e39-4830047ec417
caps.latest.revision: 30
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8028ef472cd23de251ab791e4099703640fdabc3
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="system-role-properties-management-studio"></a>Свойства системной роли (среда Management Studio)
  Страница «Системные роли» используется для просмотра определений системных ролей, определенных в настоящее время для сервера отчетов. Определение системной роли содержит именованную коллекцию задач, которые выполняются применительно ко всему сайту, а не к отдельному объекту. Определения ролей присваиваются пользователям или группам для создания назначения ролей. Задачи в определении ролей задают, какие действия может выполнять пользователь или группа.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] есть две стандартные системные роли: **Системный администратор** и **Системный пользователь**. Можно изменять эти определения ролей, изменяя список задач, или создать новую системную роль, поддерживающую другую комбинацию задач. Изменение определения роли влияет на все назначения ролей, включенные в ее определение.  
  
> [!NOTE]  
>  Назначения системных ролей используются только на сервере отчетов, который работает в собственном режиме. Если сервер отчетов настроен для интеграции с SharePoint, эта страница недоступна.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Определяет имя определения системной роли.  
  
 **Описание**  
 Отображает описание определения системной роли. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]это описание отображается только на данной странице. Пользователи, просматривающие этот элемент с помощью диспетчера отчетов, могут видеть это описание при просмотре данной иерархии папок.  
  
 **Задача**  
 Выводит список задач на уровне системы, которые можно выбрать для данного определения роли. Можно добавлять или удалять элементы из списка предопределенных задач, чтобы определить, какой доступ к данному элементу будет у пользователей с данной ролью. Нельзя создавать новые задачи или изменять уже существующие.  
  
 **Описание**  
 Выводит сведения по каждой из задач. Нельзя изменять описания задач.  
  
## <a name="see-also"></a>См. также:  
 [Справка F1 по использованию сервера отчетов среде Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Задачи системного уровня](../../reporting-services/security/tasks-and-permissions-system-level-tasks.md)   
 [Задачи и разрешения](../../reporting-services/security/tasks-and-permissions.md)   
 [Предопределенные роли](../../reporting-services/security/role-definitions-predefined-roles.md)  
  
  
