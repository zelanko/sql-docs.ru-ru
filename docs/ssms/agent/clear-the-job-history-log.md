---
title: Очистка журнала заданий | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], history
- clearing job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 34b9398a-c409-4040-8ea1-0deceb18f961
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c5904515ec74467bf90dfc031be7b3048513eb44
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="clear-the-job-history-log"></a>Clear the Job History Log
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как удалить содержимое журнала заданий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] средствами [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)]или управляющих объектов SQL Server.  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [безопасность](#Security)  
  
-   **Для очистки журнала заданий используется:**  
  
    [Среда SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [Управляющие объекты SQL Server](#SMO)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-clear-the-job-history-log"></a>Очистка журнала заданий  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Раскройте узел **Агент SQL Server**, а затем узел **Задания**.  
  
3.  Щелкните правой кнопкой мыши задание и выберите **Просмотреть журнал**.  
  
4.  В **Программе просмотра файла журнала**выберите задание, журнал которого нужно очистить, и выполните одно из следующих действий.  
  
    -   В окне **Удалить журнал**нажмите кнопку **Удалить** , затем **Удалить весь журнал** . Можно удалить как весь журнал заданий, так и только записи, сделанные до указанной даты. Чтобы удалить весь журнал заданий, нажмите кнопку **Удалить весь журнал**. Чтобы удалить из журнала заданий записи определенной давности, нажмите кнопку **Удалить журнал до**и укажите дату.  
  
    -   Чтобы очистить журнал многосерверного задания, нажмите кнопку **Состояние задания** . Нажмите кнопку **Задание**, выберите имя задания, а затем выберите пункт **Просмотреть удаленный журнал заданий**.  
  
5.  Щелкните **Удалить**.  
  
## <a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-clear-the-job-history-log"></a>Очистка журнала заданий  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- example removes the history for a job named NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_purge_jobhistory  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
## <a name="SMO"></a>Использование управляющих объектов SQL Server  
**Очистка журнала заданий**  
  
Используйте метод **PurgeJobHistory** класса **JobServer** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell. Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
