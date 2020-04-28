---
title: Запуск задания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e94adcf8242c6acaca7c28ff9a854e0aa87cb3ea
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "72798177"
---
# <a name="start-a-job"></a>Запуск задания
  В этом разделе описано, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] как начать выполнение задания агента в с помощью или управляющие объекты SQL Server.  
  
 Задание — это указанная последовательность действий, выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут выполняться на одном локальном сервере или на нескольких удаленных серверах.  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для запуска задания используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
### <a name="to-start-a-job"></a>Запуск задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Разверните узел **Агент SQL Server** , затем разверните узел **Задания**. В зависимости от того, как нужно запускать задание, сделайте следующее.  
  
    -   При работе с одиночным сервером, работе на целевом сервере или запуске задания локального сервера на главном сервере щелкните правой кнопкой мыши задание, которое нужно запустить, и выберите пункт **Запустить задание**.  
  
    -   Если нужно запустить несколько заданий, щелкните правой кнопкой мыши компонент **Монитор активности заданий**, а затем выберите пункт **Просмотр активности заданий**. В разделе "Монитор активности заданий" можно выбрать несколько заданий, щелкнуть их правой кнопкой мыши и выбрать пункт **Запустить задания**.  
  
    -   При работе на главном сервере, чтобы все целевые серверы запускали данное задание одновременно, щелкните правой кнопкой мыши нужное задание, выберите пункт **Запустить задание**, а затем пункт **Запустить на всех целевых серверах**.  
  
    -   При работе на главном сервере, чтобы указать целевые серверы для данного задания, щелкните правой кнопкой мыши нужное задание, выберите пункт **Запустить задание**, а затем пункт **Запустить на указанных целевых серверах**. В диалоговом окне **Инструкции после загрузки** установите флажок **Эти целевые серверы** и отметьте все серверы, на которых должно запускаться данное задание.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Использование Transact-SQL  
  
### <a name="to-start-a-job"></a>Запуск задания  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_start_job (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Использование управляющие объекты SQL Server  

### <a name="to-start-a-job"></a>Запуск задания
  
 Вызовите метод `Start` класса `Job` на языке программирования по своему выбору (Visual Basic, Visual C# или PowerShell). Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
