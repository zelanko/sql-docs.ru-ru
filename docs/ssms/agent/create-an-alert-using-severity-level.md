---
title: Создание предупреждения с учетом уровня серьезности | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
- SQL Server Agent, alerts
- severity levels [SQL Server]
- alerts [SQL Server], severity levels
ms.assetid: a1fd71bf-5bf9-4ce2-9a1d-032576a4a6e9
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6db64cacb1cdd5cb19bd103f1622c973ef1e9f68
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65093774"
---
# <a name="create-an-alert-using-severity-level"></a>Create an Alert Using Severity Level
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описывается, как создать предупреждение агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , срабатывающее, когда событие указанной степени серьезности происходит в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   **Для создания предупреждения по степени серьезности используется:**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает простой графический способ управления всей системой предупреждений и рекомендуется для настройки инфраструктуры предупреждений.  
  
-   События, сформированные посредством процедуры **xp_logevent** , появляются в базе данных master. Поэтому **xp_logevent** не вызывает срабатывание предупреждения, если только значение аргумента **@database_name** для предупреждения не равно **'master'** или NULL.  
  
-   При уровнях серьезности от 19 до 25 сообщение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] направляется в журнал приложения [!INCLUDE[msCoName](../../includes/msconame_md.md)] и вызывает срабатывание предупреждения. События с уровнями серьезности меньше 19 вызовут срабатывание предупреждения только в случае, если были использованы **sp_altermessage**, RAISERROR WITH LOG или **xp_logevent** , чтобы принудительно осуществить запись этих событий в журнал приложения Windows.  
  
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
    -- Adds an alert (Test Alert) that notifies the
    -- Alert Operator via email when an error with a 
    -- severity of 23 is detected.
    
    -- Assumes that the Alert Operator already exists 
    -- and that database mail is configured.
    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert @name=N'Test Alert', 
      @message_id = 0, 
      @severity = 23, 
      @enabled = 1, 
      @include_event_description_in = 1
    ;
    GO
    
    EXEC dbo.sp_add_notification @alert_name=N'Test Alert',
      @operator_name=N'Alert Operator',
      @notification_method=1
    ;
    GO

    ```  
  
Дополнительные сведения см. в разделе [sp_add_alert (Transact-SQL)](https://msdn.microsoft.com/d9b41853-e22d-4813-a79f-57efb4511f09).  
  
