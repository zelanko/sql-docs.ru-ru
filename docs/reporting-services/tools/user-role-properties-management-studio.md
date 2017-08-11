---
title: "Свойства ролей пользователей (Management Studio) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.reportserver.userroleproperties.f1
ms.assetid: c8b22236-a8b1-4e15-b1ff-4e1909b602d3
caps.latest.revision: 27
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 76bd80e1fc470d9cdb998d23834d0a3473d411fe
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="user-role-properties-management-studio"></a>Свойства пользовательской роли (среда Management Studio)
  На этой странице можно просмотреть задачи, выбранные для определения роли на уровне элемента. Эту страницу также можно использовать для изменения списка задач или модификации описания роли.  
  
 Определение роли на уровне элемента является именованной коллекцией задач, выполняемых пользователем относительно определенного элемента (например, папки, отчета, ресурса или общего источника данных). Определения ролей назначаются пользователю или группе для создания назначения роли в диспетчере отчетов. Задачи в определении роли описывают, что пользователь или группа могут делать.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]включает ряд определения стандартных ролей на уровне элемента, с которыми можно работать. Определения ролей можно изменить, изменив список задач для каждого из них. Изменение определения роли влияет на все назначения ролей, включенные в ее определение.  
  
> [!NOTE]  
>  Пользовательские назначения ролей применяются только на сервере отчетов, который работает в собственном режиме. Если сервер отчетов настроен для работы в режиме интеграции с SharePoint, то на этой странице отображаются сведения только для чтения о ролях и уровнях разрешений, которые определены на сайте SharePoint.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Название определения роли.  
  
 **Description**  
 Описание определения системной роли. В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]это описание отображается только на данной странице. В диспетчере отчетов это описание позволяет пользователям решить, следует ли использовать роль в назначении роли.  
  
 **Задача**  
 Выводит список задач на уровне элемента, которые можно выбрать для данного определения роли. Можно добавлять или удалять элементы из списка предопределенных задач, чтобы определить, какой доступ к данному элементу будет у пользователей с данной ролью. Нельзя создавать новые задачи или изменять уже существующие. Список задач определения ролей появляется только в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Описание задачи**  
 Выводит сведения по каждой из задач. Нельзя изменять описания задач.  
  
## <a name="see-also"></a>См. также  
 [Задачи уровня элемента](../../reporting-services/security/tasks-and-permissions-item-level-tasks.md)   
 [Определения ролей](../../reporting-services/security/role-definitions.md)   
 [Сервер отчетов в Справка F1 среды Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Задачи и разрешения](../../reporting-services/security/tasks-and-permissions.md)   
 [Предопределенные роли](../../reporting-services/security/role-definitions-predefined-roles.md)  
  
  
