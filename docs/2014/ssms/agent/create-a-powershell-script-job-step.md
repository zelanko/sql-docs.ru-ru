---
title: Создание шага задания, использующего скрипт PowerShell | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], job steps
- jobs [SQL Server Agent], PowerShell
- job steps [PowerShell]
- SQL Server Agent jobs, PowerShell steps
ms.assetid: 50afcf84-fae0-4eb5-9b0f-f2cf144c1433
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 68f671d8c0345db830a6cdac463869b531b39011
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104614"
---
# <a name="create-a-powershell-script-job-step"></a>Create a PowerShell Script Job Step
  В этом разделе описано, как создать и определить шаг задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выполняющий скрипт PowerShell, в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Создание шага задания скрипта PowerShell с использованием:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-powershell-script-job-step"></a>Создание шага задания скрипта PowerShell  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните **Агент SQL Server**, создайте задание или щелкните правой кнопкой мыши существующее задание и выберите пункт **Свойства**. Дополнительные сведения о создании заданий см. в разделе [Создание заданий](create-jobs.md).  
  
3.  В диалоговом окне **Свойства задания** выберите страницу **Шаги** и нажмите кнопку **Добавить**.  
  
4.  В диалоговом окне **Новый шаг задания** введите **имя шага**задания.  
  
5.  В списке **Тип** выберите **PowerShell**.  
  
6.  В списке **Выполнять как** выберите учетную запись-посредник с учетными данными, используемыми в задании.  
  
7.  В поле **Команда** введите синтаксис скрипта PowerShell, который будет выполняться в данном шаге. Или нажмите кнопку **Открыть** и выберите файл, содержащий скрипт. В качестве примера скрипта PowerShell см. подраздел **Использование Transact-SQL** ниже.  
  
8.  Выберите страницу **Дополнительно** , чтобы задать следующие параметры шага задания: какие действия предпринять в случае успешного или неуспешного выполнения шага задания, сколько раз агенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытаться его выполнить и как часто повторять эти попытки.  
  
##  <a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-powershell-script-job-step"></a>Создание шага задания скрипта PowerShell  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- creates a PowerShell job step that finds the processes that use more than 1000 MB of memory and kills them  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Kills all processes that use more than 1000 MB of memory',  
        @subsystem = N'PowerShell',  
        @command = N'Get-Process | Where-Object { $_.WS -gt 1000MB } | Stop-Process',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).  
  
##  <a name="SMO"></a> Использование управляющих объектов SQL Server  
 **Создание шага задания скрипта PowerShell**  
  
 Используйте `JobStep` , используя язык программирования, таком как Visual Basic, Visual C# или PowerShell.  
  
  
