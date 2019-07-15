---
title: Планирование задания | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
ms.assetid: f626390a-a3df-4970-b7a7-a0529e4a109c
author: markingmyname
ms.author: maghan
manager: jroth
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8b05a190b3c2c7c37a4d7389ead957e19c2085c4
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67685204"
---
# <a name="schedule-a-job"></a>Schedule a Job
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описан процесс составления расписания задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Перед началом работы**  
  
    [безопасность](#Security)  
  
-   **Для планирования задания используется:**  
  
    [Среда SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [Управляющие объекты SQL Server](#SMO)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-create-and-attach-a-schedule-to-a-job"></a>Создание и присоединение расписания к заданию  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server**, **Задания**, правой кнопкой мыши щелкните задание, для которого составляется расписание, и выберите **Свойства**.  
  
3.  Выберите страницу **Расписания** , затем нажмите **Создать**.  
  
4.  В поле **Имя** введите имя нового расписания.  
  
5.  Если расписание не должно вступать в силу немедленно после его создания, сбросьте флажок **Включено** .  
  
6.  Выберите одно из следующих значений для параметра **Тип расписания**:  
  
    -   Для запуска задания во время запуска службы агента **выберите элемент** Запускать автоматически при запуске агента SQL Server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   Для запуска задания, когда процессоры переходят в бездействующее состояние, щелкните **Запускать при бездействии процессоров** .  
  
    -   Если необходимо составить расписание для периодического выполнения, выберите **Повторяющееся задание** . Затем в диалоговом окне заполните группы **Частота**, **Сколько раз в день**и **Продолжительность** .  
  
    -   Если планируется однократное выполнение, выберите **Один раз** . Для установки расписания **Один раз** заполните в диалоговом окне группу **Однократное выполнение** .  
  
#### <a name="to-attach-a-schedule-to-a-job"></a>Присоединение расписания к заданию  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server**, **Задания**, правой кнопкой мыши щелкните задание, для которого составляется расписание, и выберите **Свойства**.  
  
3.  Выберите страницу **Расписания** и нажмите кнопку **Выбрать**.  
  
4.  Выберите расписание, которое нужно присоединить, и нажмите кнопку **ОК**.  
  
5.  В диалоговом окне **Свойства задания** дважды щелкните присоединенное расписание.  
  
6.  Убедитесь, что значение **Дата начала** настроено правильно. В противном случае установите дату начала расписания и нажмите кнопку **ОК**.  
  
7.  В диалоговом окне **Свойства задания** нажмите кнопку **ОК**.  
  
## <a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-schedule-a-job"></a>Планирование задания  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE msdb ;  
    GO  
    -- creates a schedule named NightlyJobs.   
    -- Jobs that use this schedule execute every day when the time on the server is 01:00.   
    EXEC sp_add_schedule  
        @schedule_name = N'NightlyJobs' ,  
        @freq_type = 4,  
        @freq_interval = 1,  
        @active_start_time = 010000 ;  
    GO  
    -- attaches the schedule to the job BackupDatabase  
    EXEC sp_attach_schedule  
       @job_name = N'BackupDatabase',  
       @schedule_name = N'NightlyJobs' ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделах [sp_add_schedule (Transact-SQL)](https://msdn.microsoft.com/9060aae3-3ddd-40a5-83bb-3ea7ab1ffbd7) и [sp_attach_schedule (Transact-SQL)](https://msdn.microsoft.com/80c80eaf-cf23-4ed8-b8dd-65fe59830dd1).  
  
## <a name="SMO"></a>Использование управляющих объектов SQL Server  
Воспользуйтесь классом **JobSchedule** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell. Дополнительные сведения см. в разделе[Управляющие объекты SQL Server](https://msdn.microsoft.com/library/ms162169.aspx).  
  
