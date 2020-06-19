---
title: Просмотр задания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], viewing
- viewing jobs
- SQL Server Agent jobs, viewing
- displaying jobs
ms.assetid: d2241a3f-dbcf-433c-b7bc-f96bdf0eac8c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 22cb99da1e842ef435840643d05a4c546264aecc
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062137"
---
# <a name="view-a-job"></a>View a Job
  В этом разделе описывается просмотр [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заданий агента в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для просмотра задания используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Если пользователь не принадлежит к предопределенной роли сервера **sysadmin** , он может просматривать лишь те задания, которыми владеет. Члены этой роли могут просматривать все задания. Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-a-job"></a>Просмотр задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Раскройте узел **Агент SQL Server**, а затем узел **Задания**.  
  
3.  Правой кнопкой мыши щелкните задание и выберите **Свойства**.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-view-a-job"></a>Просмотр задания  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
    -- lists all aspects of the information for the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_job  
        @job_name = N'NightlyBackups',  
        @job_aspect = N'ALL' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Использование управляющие объекты SQL Server  
 **Просмотр задания**  
  
 Воспользуйтесь классом `Job` в любом языке программирования (Visual Basic, Visual C# или PowerShell). Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
