---
title: "Изменение параметров расписания для главного задания агента SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5414451-4d8e-464b-bd9e-f2b70c6899b3
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b3b08fe5a5a2e076dab9ef2f6c00b9dac86f1a56
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="change-the-scheduling-details-for-a-sql-server-agent-master-job"></a>Изменение параметров расписания для главного задания агента SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
В этом разделе описывается изменение параметров расписания для определения задания в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] или [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   **Изменение параметров расписания для определения задания с помощью:**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
Главное задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] не может быть ориентировано как на локальный, так и на удаленный сервер.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Если пользователь не является членом предопределенной роли сервера **sysadmin** , он может изменять только свои собственные задания. Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-change-the-scheduling-details-for-a-job-definition"></a>Изменение параметров расписания для определения задания  
  
1.  В **обозревателе объектов** щелкните знак «плюс», чтобы развернуть сервер, содержащий задание, для которого нужно изменить расписание.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Чтобы развернуть папку **Задания** , щелкните значок «плюс».  
  
4.  Щелкните правой кнопкой мыши задание, расписание которого необходимо изменить, и выберите пункт **Свойства**.  
  
5.  В диалоговом окне **Свойства задания —***имя_задания* в разделе **Выберите страницу** выберите пункт **Расписания**. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Свойства задания — создание задания (страница "Расписания")](../../ssms/agent/job-properties-new-job-schedules-page.md).  
  
6.  После завершения нажмите кнопку **ОК**.  
  
## <a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-change-the-scheduling-details-for-a-job-definition"></a>Изменение параметров расписания для определения задания  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- changes the enabled status of the NightlyJobs schedule to 0   
    -- and sets the owner to terrid.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_schedule  
        @name = 'NightlyJobs',  
        @enabled = 0,  
        @owner_login_name = 'terrid' ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_update_schedule (Transact-SQL)](http://msdn.microsoft.com/en-us/97b3119b-e43e-447a-bbfb-0b5499e2fefe).  
  
