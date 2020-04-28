---
title: Запись состояния задания в журнал приложений Windows | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- SQL Server Agent jobs, status
- writing job status to log
- jobs [SQL Server Agent], status
- logs [SQL Server], jobs
ms.assetid: 3b813702-8f61-40ec-bf3b-ce9deb7e68be
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ec615911233227c15f43e55125adfd6166cb51e8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "72783372"
---
# <a name="write-the-job-status-to-the-windows-application-log"></a>Write the Job Status to the Windows Application Log
  В этом разделе описывается настройка [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для записи состояния задания в журнал событий приложений Windows с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или управляющие объекты SQL Server.  
  
 Ответы заданий дают гарантию того, что администраторы базы данных будут знать о завершении выполнения заданий и частоте их выполнения. Обычными ответами заданий являются следующие.  
  
-   Уведомление оператора с помощью электронной почты, системы пейджинга или сообщения **net send** . Используйте один из этих ответов на задание, если оператор должен выполнить последующие действия. Например, после успешного выполнения задания резервного копирования оператор должен получить напоминание об удалении магнитной ленты с резервной копией и сохранении ее в безопасном месте.  
  
-   Запись сообщений о событиях в журнал приложений Windows. Этот ответ можно использовать только для неудачно завершившихся заданий.  
  
-   Автоматическое удаление задания. Используйте этот ответ только тогда, когда есть уверенность в том, что не понадобится выполнять это задание повторно.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для записи состояния задания в журнал приложений Windows используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-write-job-status-to-the-windows-application-log"></a>Запись данных о состоянии задания в журнал приложений Windows  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Разверните узел **Агент SQL Server**, выберите раздел **Задания**, щелкните правой кнопкой мыши задание, которое нужно изменить, и выберите пункт **Свойства**.  
  
3.  Выберите страницу **Уведомления** .  
  
4.  Установите флажок **Запись в журнал событий приложений Windows**, а затем выберите:  
  
    -   **При успешном завершении задания**для регистрации успешных завершений задания.  
  
    -   **При ошибке задания**для регистрации завершений задания с ошибками.  
  
    -   **При завершении задания** для регистрации любых состояний завершения задания.  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Использование управляющие объекты SQL Server  

### <a name="to-write-job-status-to-the-windows-application-log"></a>Запись данных о состоянии задания в журнал приложений Windows
  
 Вызовите свойство `EventLogLevel` класса `Job`, используя выбранный язык программирования, например Visual Basic, Visual C# или PowerShell.  
  
 В следующем примере кода для задания задается создание записи в журнале событий операционной системы после завершения выполнения задания.  
  
```powershell
$srv = new-object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = new-object Microsoft.SqlServer.Management.Smo.Agent.Job($srv.JobServer, "Test Job")  
$jb.EventLogLevel = [Microsoft.SqlServer.Management.Smo.Agent.CompletionAction]::Always  
```  
