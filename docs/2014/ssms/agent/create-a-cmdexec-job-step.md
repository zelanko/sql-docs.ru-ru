---
title: Создание шага задания CmdExec | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CmdExec jobs
ms.assetid: b48da5b4-6fe7-4eb7-bade-dc7d697c6d5c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 896a3d19345805d5468f3ec238ae5e75be34daba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68211476"
---
# <a name="create-a-cmdexec-job-step"></a>Создание шага задания CmdExec
  В этом разделе описано, как создать и определить шаг задания агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , использующий выполняемую программу или команду операционной системы, с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов SQL Server.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Для создания шага задания CmdExec используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
 По умолчанию только члены предопределенной роли сервера **sysadmin** могут создавать шаги задания CmdExec. Шаги задания службы агента SQL Server запускаются под учетной записью службы агента SQL Server, если пользователь **sysadmin** не создал учетную запись-посредника. Пользователь, не являющийся членом предопределенной роли сервера **sysadmin** может создавать шаги задания CmdExec, только если у него есть доступ к учетной записи-посреднику CmdExec.  
  
####  <a name="Permissions"></a> Permissions  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-cmdexec-job-step"></a>Создание шага задания CmdExec  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните **Агент SQL Server**, создайте задание или щелкните правой кнопкой мыши существующее задание и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства задания** выберите страницу **Шаги** и нажмите кнопку **Добавить**.  
  
4.  В диалоговом окне **Новый шаг задания** введите **имя шага**задания.  
  
5.  В списке **Тип** выберите **Операционная система (CmdExec)** .  
  
6.  В списке **Выполнять как** выберите учетную запись-посредник с учетными данными, используемыми в задании. По умолчанию шаги задания CmdExec выполняются под учетной записью службы агента SQL Server.  
  
7.  В поле **Код завершения процесса успешной команды** введите значение от 0 до 999999.  
  
8.  В поле **Команда** введите команду операционной системы или программу для выполнения. Пример см. в разделе «Использование Transact T-SQL».  
  
9. Выберите вкладку **Дополнительно** , чтобы задать следующие параметры шага задания: действие, которое необходимо выполнить при успешном или неуспешном выполнении шага задания, количество попыток агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнить шаг задания и файл, в который агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может записывать результат выполнения шага задания. Только члены предопределенной роли сервера **sysadmin** могут записывать выходные данные шага задания в файл операционной системы.  
  
##  <a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-cmdexec-job-step"></a>Создание шага задания CmdExec  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- creates a job step that uses CmdExec  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'CMDEXEC',  
        @command = C:\clickme_scripts\SQL11\PostBOLReorg GetHsX.exe',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
##  <a name="SMO"></a> Использование управляющих объектов SQL Server  
 **Создание шага задания CmdExec**  
  
 Воспользуйтесь классом `JobStep` в любом языке программирования (Visual Basic, Visual C# или PowerShell).  
  
  
