---
title: Создание предупреждения с учетом уровня серьезности | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
- SQL Server Agent, alerts
- severity levels [SQL Server]
- alerts [SQL Server], severity levels
ms.assetid: a1fd71bf-5bf9-4ce2-9a1d-032576a4a6e9
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aa914bec1c74a96d4574765fb2c504e76623fa63
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155635"
---
# <a name="create-an-alert-using-severity-level"></a>Create an Alert Using Severity Level
  В этом разделе описывается, как создать предупреждение агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , срабатывающее, когда событие указанной степени серьезности происходит в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Для создания предупреждения по степени серьезности используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает простой графический способ управления всей системой предупреждений и рекомендуется для настройки инфраструктуры предупреждений.  
  
-   События, сформированные посредством процедуры **xp_logevent** , появляются в базе данных master. Поэтому **xp_logevent** не вызывает срабатывание предупреждения, если только значение аргумента **@database_name** для предупреждения не равно **'master'** или NULL.  
  
-   При уровнях серьезности от 19 до 25 сообщение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] направляется в журнал приложения [!INCLUDE[msCoName](../../includes/msconame-md.md)] и вызывает срабатывание предупреждения. События с уровнями серьезности меньше 19 вызовут срабатывание предупреждения только в случае, если были использованы **sp_altermessage**, RAISERROR WITH LOG или **xp_logevent** , чтобы принудительно осуществить запись этих событий в журнал приложения Windows.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 По умолчанию только члены предопределенной роли сервера **sysadmin** могут выполнять процедуру **sp_add_alert**.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
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
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-an-alert-using-severity-level"></a>Создание предупреждения с указанием уровня серьезности  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- adds an alert (Test Alert) that runs the Back up the AdventureWorks2012 Database job when fired   
    -- assumes that the message 55001 and the Back up the AdventureWorks2012 Database job already exist.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert',  
        @message_id = 55001,   
       @severity = 0,   
       @notification_message = N'Error 55001 has occurred. The database will be backed up...',   
       @job_name = N'Back up the AdventureWorks2012 Database' ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql).  
  
  
