---
title: "Создание шага задания Transact-SQL | Документация Майкрософт"
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
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: 69c571a7-debe-4063-9d38-e4b6a1e8e84c
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 30d692969db247383010a268c9dd58ee5d2bd3ea
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="create-a-transact-sql-job-step"></a>Создание шага задания Transact-SQL
В этом разделе описано, как создать шаг задания агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , который исполняет скрипты [!INCLUDE[tsql](../../includes/tsql_md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] , с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)]или управляющих объектов SQL Server.  
  
Эти скрипты шагов задания могут вызывать хранимые процедуры и расширенные хранимые процедуры. Один шаг задания [!INCLUDE[tsql](../../includes/tsql_md.md)] может содержать несколько пакетов и команд GO. Дополнительные сведения о создании заданий см. в разделе [Создание заданий](../../ssms/agent/create-jobs.md).  
  
**В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
    [безопасность](#Security)  
  
-   **Для создания шага задания Transact-SQL используется:**  
  
    [Среда Среда SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [Управляющие объекты SQL Server](#SMO)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-transact-sql-job-step"></a>Создание шага задания Transact-SQL  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните **Агент SQL Server**, создайте задание или щелкните правой кнопкой мыши существующее задание и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства задания** выберите страницу **Шаги** и нажмите кнопку **Добавить**.  
  
4.  В диалоговом окне **Новый шаг задания** введите **имя шага**задания.  
  
5.  В списке **Тип** выберите **Скрипт Transact-SQL (TSQL)**.  
  
6.  На панели **Команда** введите пакет команд [!INCLUDE[tsql](../../includes/tsql_md.md)] или нажмите кнопку **Открыть** и выберите файл [!INCLUDE[tsql](../../includes/tsql_md.md)] , используемый в качестве команды.  
  
7.  Нажмите кнопку **Синтаксический анализ** для проверки синтаксиса.  
  
8.  Если синтаксис правильный, появится сообщение «Синтаксический анализ успешно завершен». При обнаружении ошибки исправьте ее.  
  
9. Щелкните вкладку **Дополнительно** , чтобы задать следующие параметры шага задания: какое действие необходимо выполнить при успешном или неуспешном выполнении шага задания, сколько раз агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] должен пытаться выполнить шаг задания, а также файл или таблицу, куда агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] может записывать результат выполнения шага задания. Только члены предопределенной роли сервера **sysadmin** могут записывать выходные данные шага задания в файл операционной системы. В таблицу выходные данные могут записывать все пользователи агента SQL Server.  
  
10. Если члену предопределенной роли сервера **sysadmin** нужно выполнить шаг задания в контексте другого имени входа SQL, ему следует выбрать имя входа SQL из списка **Выполнять от имени** .  
  
## <a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-create-a-transact-sql-job-step"></a>Создание шага задания Transact-SQL  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- creates a job step that that uses Transact-SQL  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_add_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/97900032-523d-49d6-9865-2734fba1c755).  
  
## <a name="SMO"></a>Использование управляющих объектов SQL Server  
**Создание шага задания Transact-SQL**  
  
Воспользуйтесь классом **JobStep** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell.  
  

