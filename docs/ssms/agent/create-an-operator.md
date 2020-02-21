---
title: Create an Operator
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- jobs [SQL Server Agent], notification options
- operators (users) [Database Engine], creating with Management Studio
- SQL Server Agent jobs, notification options
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 1359d790-5905-4927-a208-e7155e7768a2
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 65c9940c130dbaf27d5b50b73d11b22adb11664e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75258774"
---
# <a name="create-an-operator"></a>Create an Operator
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этой статье описано, как настроить для пользователя получение уведомлений о заданиях агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   Режимы отправки уведомлений с помощью пейджера и команды **net send** будут удалены из агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в следующей версии [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Старайтесь не использовать эти функции в новых разработках и предусмотрите соответствующие изменения в приложениях, которые используют их в настоящее время.  
  
-   Обратите внимание, что для использования компонента Database Mail для отправки операторам уведомлений по электронной почте и на пейджер агент SQL Server необходимо настроить для использования компонента Database Mail. Дополнительные сведения см. в разделе [Назначить предупреждения для оператора](assign-alerts-to-an-operator.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Создавать операторов могут только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-create-an-operator"></a>Создание оператора  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, на котором необходимо создать оператора агента SQL Server.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши папку **Операторы** и выберите пункт **Создать оператора**.  
  
    На странице **Общие** диалогового окна **Создание оператора** доступны следующие параметры.  
  
    **имя**;  
    Изменить имя оператора.  
  
    **Enabled**  
    Разрешить оператор. Если он не включен, то уведомления оператору не отправляются.  
  
    **Имя для электронной почты**  
    Определяет адрес электронной почты оператора.  
  
    **Адрес для команды net send**  
    Задает адрес, используемый для **net send**.  
  
    **Имя для сообщения на пейджер**  
    Определяет адрес электронной почты пейджера оператора.  
  
    **Расписание работы для пейджера**  
    Указывает время, когда пейджер активен.  
  
    **Понедельник — воскресенье**  
    Выберите дни, когда пейджер активен.  
  
    **Начало рабочего дня**  
    Выберите время суток, после которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправляет сообщения на пейджер.  
  
    **Конец рабочего дня**  
    Выберите время суток, после которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перестает отправлять сообщения на пейджер.  
  
    На странице **Уведомления** диалогового окна **Создание оператора** доступны следующие параметры.  
  
    **Оповещения**  
    Просмотреть предупреждения в экземпляре.  
  
    **Задания**  
    Просмотреть задания в экземпляре.  
  
    **Список предупреждений**  
    Содержит список предупреждений в экземпляре.  
  
    **Список заданий**  
    Содержит список заданий в экземпляре.  
  
    **Электронная почта**  
    Уведомить этого оператора, используя электронную почту.  
  
    **Пейджер**  
    Уведомить этого оператора, отправив сообщение электронной почты на адрес пейджера.  
  
    **Команда Net send**  
    Уведомить этого оператора, используя **net send**.  
  
4.  После завершения создания оператора нажмите кнопку **ОК**.  
  
## <a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-create-an-operator"></a>Создание оператора  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- sets up the operator information for user 'danwi.'
    -- The operator is enabled.   
    -- SQL Server Agent sends notifications by pager 
    -- from Monday through Friday from 8 A.M. to 5 P.M.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_operator  
        @name = N'Dan Wilson',  
        @enabled = 1,  
        @email_address = N'danwi',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 62 ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_add_operator (Transact-SQL)](https://msdn.microsoft.com/817cd98a-4dff-4ed8-a546-f336c144d1e0).  
  
