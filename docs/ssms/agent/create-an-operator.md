---
title: "Создание оператора | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, operators
- jobs [SQL Server Agent], notification options
- operators (users) [Database Engine], creating with Management Studio
- SQL Server Agent jobs, notification options
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 1359d790-5905-4927-a208-e7155e7768a2
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: afca596bc8dc55411bcfbd48b74d3bdfd7c11248
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="create-an-operator"></a>Создание оператора
В этом разделе описано, как настроить для пользователя получение уведомлений о заданиях агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] или [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   **Создание оператора**  
  
    [Среда Среда SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   Режимы отправки уведомлений с помощью пейджера и команды **net send** будут удалены из агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в следующей версии [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Старайтесь не использовать эти функции в новых разработках и предусмотрите соответствующие изменения в приложениях, которые используют их в настоящее время.  
  
-   Обратите внимание, что для использования компонента Database Mail для отправки операторам уведомлений по электронной почте и на пейджер агент SQL Server необходимо настроить для использования компонента Database Mail. Дополнительные сведения см. в разделе [Назначить предупреждения для оператора](http://msdn.microsoft.com/library/ms190038.aspx).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Создавать операторов могут только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-create-an-operator"></a>Создание оператора  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, на котором необходимо создать оператора агента SQL Server.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши папку **Операторы** и выберите пункт **Создать оператора**.  
  
    На странице **Общие** диалогового окна **Создание оператора** доступны следующие параметры.  
  
    **Название**  
    Изменить имя оператора.  
  
    **Включено**  
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
    Выберите время суток, после которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] отправляет сообщения на пейджер.  
  
    **Конец рабочего дня**  
    Выберите время суток, после которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] перестает отправлять сообщения на пейджер.  
  
    На странице **Уведомления** диалогового окна **Создание оператора** доступны следующие параметры.  
  
    **Предупреждения**  
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
  
    **Команда Команда Net send**  
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
  
Дополнительные сведения см. в разделе [sp_add_operator (Transact-SQL)](http://msdn.microsoft.com/en-us/817cd98a-4dff-4ed8-a546-f336c144d1e0).  
  

