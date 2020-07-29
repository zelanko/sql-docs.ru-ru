---
title: Запуск задания
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: fe08331577d8b3f905d0a2917d9d19e3ae320f65
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755108"
---
# <a name="start-a-job"></a>Запуск задания
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этой статье описано, как запустить задание агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов SQL Server.  
  
Задание — это указанная последовательность действий, выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут выполняться на одном локальном сервере или на нескольких удаленных серверах.  
  
-   **Перед началом работы**  
  
    [Безопасность](#Security)  
  
-   **Для запуска задания используется:**  
  
    [Среда SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [Управляющие объекты SQL Server](#SMO)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="security"></a><a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-start-a-job"></a>Запуск задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Разверните узел **Агент SQL Server** , затем разверните узел **Задания**. В зависимости от того, как нужно запускать задание, сделайте следующее.  
  
    -   При работе с одиночным сервером, работе на целевом сервере или запуске задания локального сервера на главном сервере щелкните правой кнопкой мыши задание, которое нужно запустить, и выберите пункт **Запустить задание**.  
  
    -   Если нужно запустить несколько заданий, щелкните правой кнопкой мыши компонент **Монитор активности заданий**, а затем выберите пункт **Просмотр активности заданий**. В разделе "Монитор активности заданий" можно выбрать несколько заданий, щелкнуть их правой кнопкой мыши и выбрать пункт **Запустить задания**.  
  
    -   При работе на главном сервере, чтобы все целевые серверы запускали данное задание одновременно, щелкните правой кнопкой мыши нужное задание, выберите пункт **Запустить задание**, а затем пункт **Запустить на всех целевых серверах**.  
  
    -   При работе на главном сервере, чтобы указать целевые серверы для данного задания, щелкните правой кнопкой мыши нужное задание, выберите пункт **Запустить задание**, а затем пункт **Запустить на указанных целевых серверах**. В диалоговом окне **Инструкции после загрузки** установите флажок **Эти целевые серверы** и отметьте все серверы, на которых должно запускаться данное задание.  
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>Использование Transact-SQL  
  
#### <a name="to-start-a-job"></a>Запуск задания  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_start_job (Transact-SQL)](https://msdn.microsoft.com/8a91df6a-eb84-4512-9a17-4a6e32a9538a).  
  
## <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Использование управляющих объектов SQL Server  
**Запуск задания**  
  
Вызовите метод **Start** класса **Job** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell. Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
