---
title: Создание шага задания со скриптом ActiveX | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ActiveX scripting jobs [SQL Server]
- job steps [Analysis Services]
ms.assetid: e6c46c6b-2d61-4571-bc8e-a831cd6e6302
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d502d81e5edddb8c47ffc3a9bcdf742aa84a59da
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43820840"
---
# <a name="create-an-activex-script-job-step"></a>Create an ActiveX Script Job Step
  В этом разделе описывается создание и определение шага агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , выполняющего скрипт ActiveX, с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или управляющих объектов SQL Server.  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Для создания шага задания Transact-SQL используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
## <a name="before-you-begin"></a>Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
###  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-an-activex-script-job-step"></a>Создание шага задания скрипта ActiveX  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните **Агент SQL Server**, создайте задание или щелкните правой кнопкой мыши существующее задание и выберите пункт **Свойства**. Дополнительные сведения о создании заданий см. в разделе [Создание заданий](create-jobs.md).  
  
3.  В диалоговом окне **Свойства задания** выберите страницу **Шаги** и нажмите кнопку **Добавить**.  
  
4.  В диалоговом окне **Новый шаг задания** введите **имя шага**задания.  
  
5.  В списке **Тип** выберите **Скрипт ActiveX**.  
  
6.  В списке **Выполнять как** выберите учетную запись-посредник с учетными данными, используемыми в задании.  
  
7.  Выберите **Язык** , на котором написан скрипт. Или выберите **Другой** и введите имя языка скриптов [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX, на котором будет написан скрипт.  
  
8.  В поле **Команда** введите скрипт, который будет выполняться этим шагом задания. Или нажмите кнопку **Открыть** и выберите файл, содержащий скрипт.  
  
9. Выберите страницу **Дополнительно** , чтобы задать следующие параметры шага задания: какие действия предпринять в случае успешного или неуспешного выполнения шага задания, сколько раз агенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытаться его выполнить и как часто повторять эти попытки.  
  
##  <a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-create-an-activex-script-job-step"></a>Создание шага задания скрипта ActiveX  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
  
              -- create an ActiveX Script job step written in VBScript that creates a restore point  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Create a restore point',  
        @subsystem = N'ACTIVESCRIPTING',  
        @command = N'Const RESTORE_POINT = 20  
  
    strComputer = "."  
    Set objWMIService = GetObject("winmgmts:" _  
        & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\default")  
  
    Set objItem = objWMIService.Get("SystemRestore")  
    errResults = objItem.Restore(RESTORE_POINT)',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).  
  
##  <a name="SMO"></a> Использование управляющих объектов SQL Server  
 **Создание шага задания скрипта ActiveX**  
  
 Используйте `JobStep` , используя язык программирования, таком как Visual Basic, Visual C# или PowerShell.  
  
  
