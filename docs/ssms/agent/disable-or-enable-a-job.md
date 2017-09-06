---
title: "Отключение или включение задания | Документация Майкрософт"
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
- stopping jobs
- disabling jobs
- SQL Server Agent jobs, disabling
- jobs [SQL Server Agent], disabling
ms.assetid: 5041261f-0c32-4d4a-8bee-59a6c16200dd
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 63ab17f3ac8fb0de122b8553d2f5ce536ef3701c
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="disable-or-enable-a-job"></a>Отключение или включение задания
В этом разделе описано, как отключить задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] или [!INCLUDE[tsql](../../includes/tsql_md.md)]. Отключение задания не удаляет его, поэтому при необходимости оно может быть включено заново.  
  
**В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
    [безопасность](#Security)  
  
-   **Для включения или отключения задания используется:**  
  
    [Среда Среда SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-disable-or-enable-a-job"></a>Включение или отключение задания  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server**.  
  
3.  Разверните папку **Задания**, а затем правой кнопкой мыши щелкните задание, которое нужно включить или отключить.  
  
4.  Чтобы отключить задание, выберите команду **Отключить**. Чтобы включить задание, выберите команду **Включить**.  
  
## <a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-disable-or-enable-a-job"></a>Включение или отключение задания  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- changes the name, description, and disables status of the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @new_name = N'NightlyBackups -- Disabled',  
        @description = N'Nightly backups disabled during server migration.',  
        @enabled = 0 ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_update_job (Transact-SQL)](http://msdn.microsoft.com/en-us/cbdfea38-9e42-47f3-8fc8-5978b82e2623).  
  

