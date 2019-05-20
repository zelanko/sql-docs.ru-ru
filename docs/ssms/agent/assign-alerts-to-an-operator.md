---
title: Назначение предупреждений оператору | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- assigning alerts to operator
- SQL Server Agent, alerts
- alerts [SQL Server], assigning to operator
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: aa818155-6fa2-4565-a09f-5c7e31c89754
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b889b3c391bde7e064eab49c3791fa05cdf1e674
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65104398"
---
# <a name="assign-alerts-to-an-operator"></a>Assign Alerts to an Operator
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как назначать предупреждения агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для операторов, что позволяет им получать уведомления о заданиях в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   **Назначение предупреждений оператору с помощью:**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает простой графический способ управления всей системой предупреждений. Использование среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] рекомендуется для настройки инфраструктуры предупреждений.  
  
-   Чтобы в ответ на предупреждение отправить уведомление, необходимо настроить агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для отправки почты. Дополнительные сведения см. в статье [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
-   Ошибки, возникающие при отправке сообщения по электронной почте или уведомления по пейджеру, регистрируются в журнале ошибок службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Только члены предопределенной роли сервера **sysadmin** могут назначать предупреждения операторам.  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-assign-alerts-to-an-operator"></a>Назначение предупреждений оператору  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, содержащий оператора, которому необходимо назначить предупреждение.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните значок «плюс», чтобы развернуть папку **Операторы** .  
  
4.  Щелкните правой кнопкой мыши оператора, для которого нужно назначить предупреждение, выберите пункт **Свойства**и перейдите на страницу **Уведомления** .  
  
5.  В разделе **Выбор страницы** диалогового окна _Свойства_**имя\_оператора** выберите **Уведомления**.  
  
6.  В поле **Просмотр отправленных пользователю уведомлений по**выберите **Предупреждения** , чтобы просмотреть список предупреждений, отправляемых этому оператору, либо **Задания** , чтобы просмотреть список заданий, отправляющих уведомления этому оператору. Установите перечисленные ниже флажки, чтобы выбрать способ доставки для каждого из уведомлений: **Электронная почта**, **Пейджер** или **Net send**.  
  
7.  После завершения нажмите кнопку **ОК**.  
  
## <a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-assign-alerts-to-an-operator"></a>Назначение предупреждений оператору  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- adds an e-mail notification for the specified alert (Test Alert)  
    -- This example assumes that Test Alert already exists
    -- and that François Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'François Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_add_notification (Transact-SQL)](https://msdn.microsoft.com/0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd).  
  
