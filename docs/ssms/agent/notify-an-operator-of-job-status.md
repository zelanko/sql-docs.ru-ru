---
title: Уведомление оператора о состоянии задания | Документация Майкрософт
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
- status information [SQL Server], jobs
- jobs [SQL Server Agent], notification options
- SQL Server Agent jobs, status
- jobs [SQL Server Agent], status
- SQL Server Agent jobs, notification options
- notifications [SQL Server], job status
ms.assetid: e7399505-27ac-48d9-a637-73bf92b9df49
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c72c5538062bbd4b29d3b142b165c62c78cb6d30
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="notify-an-operator-of-job-status"></a>Notify an Operator of Job Status
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описывается настройка параметров уведомления в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)]или управляющих объектов SQL Server, чтобы агент [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] мог отправлять оператору уведомления о заданиях.  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [безопасность](#Security)  
  
-   **Для уведомления оператора о состоянии задания используется:**  
  
    [Среда SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [Управляющие объекты SQL Server](#SMO)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-notify-an-operator-of-job-status"></a>Уведомление оператора о состоянии задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server**, выберите раздел **Задания**, щелкните правой кнопкой мыши задание, которое нужно изменить, и затем выберите **Свойства**.  
  
3.  В окне **Свойства задания** перейдите на страницу **Уведомления** .  
  
4.  Если нужно оповещать оператора по электронной почте, установите флажок **Электронная почта**, выберите из списка оператора, а затем выберите одно из следующих значений:  
  
    -   **При успешном завершении задания** известить оператора о том, что задание удачно завершено.  
  
    -   **При ошибке задания** известить оператора о неуспешном завершении задания.  
  
    -   **При завершении задания** известить оператора независимо от состояния выполнения.  
  
5.  Если необходимо оповещать оператора по пейджеру, отметьте **Пейджер**, выберите из списка оператора, а затем выберите один из следующих вариантов:  
  
    -   **При успешном завершении задания** известить оператора о том, что задание удачно завершено.  
  
    -   **При ошибке задания** известить оператора о неуспешном завершении задания.  
  
    -   **При завершении задания** известить оператора независимо от состояния выполнения.  
  
6.  Если нужно оповещать оператора через net send, установите флажок **Команда net send**, выберите из списка оператора, а затем выберите один из следующих вариантов:  
  
    -   **При успешном завершении задания** известить оператора о том, что задание удачно завершено.  
  
    -   **При ошибке задания** известить оператора о неуспешном завершении задания.  
  
    -   **При завершении задания** известить оператора независимо от состояния выполнения.  
  
## <a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-notify-an-operator-of-job-status"></a>Уведомление оператора о состоянии задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- adds an e-mail notification for the specified alert (Test Alert).  
    -- This example assumes that Test Alert already exists
    --  and that François Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_notification   
    @alert_name = N'Test Alert',   
    @operator_name = N'François Ajenstat',   
    @notification_method = 1 ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_add_notification (Transact-SQL)](http://msdn.microsoft.com/en-us/0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd).  
  
## <a name="SMO"></a>Использование управляющих объектов SQL Server  
**Уведомление оператора о состоянии задания**  
  
Воспользуйтесь классом **Job** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell. Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
