---
title: "Создание предупреждения с учетом уровня серьезности | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- alerts [SQL Server], creating
- SQL Server Agent, alerts
- severity levels [SQL Server]
- alerts [SQL Server], severity levels
ms.assetid: a1fd71bf-5bf9-4ce2-9a1d-032576a4a6e9
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5650891f3e4bfb9a4df68eeb8f32994705146ce8
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="create-an-alert-using-severity-level"></a>Create an Alert Using Severity Level
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описывается, как создать предупреждение агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], срабатывающее, когда событие указанной степени серьезности происходит в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)], с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] или [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   **Для создания предупреждения по степени серьезности используется:**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] обеспечивает простой графический способ управления всей системой предупреждений и рекомендуется для настройки инфраструктуры предупреждений.  
  
-   События, сформированные посредством процедуры **xp_logevent** , появляются в базе данных master. Поэтому **xp_logevent** не вызывает срабатывание предупреждения, если только значение аргумента **@database_name** для предупреждения не равно **'master'** или NULL.  
  
-   При уровнях серьезности от 19 до 25 сообщение [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] направляется в журнал приложения [!INCLUDE[msCoName](../../includes/msconame_md.md)] и вызывает срабатывание предупреждения. События с уровнями серьезности меньше 19 вызовут срабатывание предупреждения только в случае, если были использованы **sp_altermessage**, RAISERROR WITH LOG или **xp_logevent** , чтобы принудительно осуществить запись этих событий в журнал приложения Windows.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
По умолчанию только члены предопределенной роли сервера **sysadmin** могут выполнять процедуру **sp_add_alert**.  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-create-an-alert-using-severity-level"></a>Создание предупреждения с указанием уровня серьезности  
  
1.  В **обозревателе объектов** щелкните знак «плюс», чтобы развернуть сервер, на котором необходимо создать предупреждение по степени серьезности.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой пункт **Предупреждения** и выберите **Создать предупреждение**.  
  
4.  В поле **Имя** диалогового окна **Создание предупреждения** введите имя этого предупреждения.  
  
5.  В списке **Тип** выберите **Предупреждение о событии SQL Server**.  
  
6.  В разделе **Определение предупреждения о событии**в списке **Имя базы данных** выберите базу данных для установки ограничения на предупреждение относительно конкретной базы банных.  
  
7.  В разделе **Предупреждение будет выдано на основании**выберите пункт **Серьезность** , а затем выберите степень серьезности для предупреждения.  
  
8.  Чтобы ограничить сообщение определенной последовательностью символов, установите флажок в поле **Создавать предупреждение, если сообщение содержит** и введите ключевое слово или строку символов в поле **Текст сообщения**. Максимальное количество символов равно 100.  
  
9. Нажмите кнопку **ОК**.  
  
## <a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-create-an-alert-using-severity-level"></a>Создание предупреждения с указанием уровня серьезности  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- adds an alert (Test Alert) that runs the Back up
    -- the AdventureWorks2012 Database job when fired   
    -- assumes that the message 55001 and the Back up
    -- the AdventureWorks2012 Database job already exist.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert',  
        @message_id = 55001,   
       @severity = 0,   
       @notification_message = N'Error 55001 has occurred. The DB will be backed up...',   
       @job_name = N'Back up the AdventureWorks2012 Database' ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_add_alert (Transact-SQL)](http://msdn.microsoft.com/en-us/d9b41853-e22d-4813-a79f-57efb4511f09).  
  
