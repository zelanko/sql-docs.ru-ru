---
title: Остановка задания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 78986e85dd8ee808f5fb621182d903a94bbc5eb7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067520"
---
# <a name="stop-a-job"></a>Остановка задания
  В этом разделе описывается, как прерывать [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Задание агента. Задание — это указанная последовательность действий, выполняемая агентом SQL Server.  
  
-   **Перед началом:** ,  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для остановки задания используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Если задание в данный момент выполняет этап типа **CmdExec** или **PowerShell**, выполняемый процесс (например MyProgram.exe) принудительно завершается раньше времени. Это может привести к непредсказуемому поведению, например файлы, используемые процессом, могут остаться открытыми.  
  
-   Для многосерверного задания инструкция STOP отправляется на все целевые серверы, с которыми связано задание.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-stop-a-job"></a>Остановка задания  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Разверните узел **Агент SQL Server**, выберите раздел **Задания**, щелкните правой кнопкой мыши задание, которое необходимо остановить, и выберите команду **Прервать задание**.  
  
3.  Если нужно остановить несколько заданий, щелкните правой кнопкой мыши компонент **Монитор активности заданий**, а затем выберите пункт **Просмотр активности заданий**. На мониторе активности заданий отметьте задания, которые нужно остановить, щелкните выделенные строки правой кнопкой мыши и выберите **Прервать задания**.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Использование Transact-SQL  
  
### <a name="to-stop-a-job"></a>Остановка задания  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_stop_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-stop-job-transact-sql).  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Использование управляющие объекты SQL Server  

### <a name="to-stop-a-job"></a>Остановка задания
  
 Вызовите метод `Stop` класса `Job` на языке программирования по своему выбору (Visual Basic, Visual C# или PowerShell). Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
