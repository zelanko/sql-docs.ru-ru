---
title: Создание шага задания Transact-SQL | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: 69c571a7-debe-4063-9d38-e4b6a1e8e84c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 488e07e86ba5a7febcb0675611136a1e0d792007
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "72798257"
---
# <a name="create-a-transact-sql-job-step"></a>Создание шага задания Transact-SQL
  В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этом разделе описывается создание [!INCLUDE[tsql](../../includes/tsql-md.md)] шага задания агента, выполняющего скрипты в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или управляющие объекты SQL Server.  
  
 Эти скрипты шагов задания могут вызывать хранимые процедуры и расширенные хранимые процедуры. Один шаг задания [!INCLUDE[tsql](../../includes/tsql-md.md)] может содержать несколько пакетов и команд GO. Дополнительные сведения о создании заданий см. в разделе [Создание заданий](create-jobs.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для создания шага задания Transact-SQL используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-transact-sql-job-step"></a>Создание шага задания Transact-SQL  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните **Агент SQL Server**, создайте задание или щелкните правой кнопкой мыши существующее задание и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства задания** выберите страницу **Шаги** и нажмите кнопку **Добавить**.  
  
4.  В диалоговом окне **Новый шаг задания** введите **имя шага**задания.  
  
5.  В списке **Тип** выберите **Скрипт Transact-SQL (TSQL)**.  
  
6.  На панели **Команда** введите пакет команд [!INCLUDE[tsql](../../includes/tsql-md.md)] или нажмите кнопку **Открыть** и выберите файл [!INCLUDE[tsql](../../includes/tsql-md.md)] , используемый в качестве команды.  
  
7.  Нажмите кнопку **Синтаксический анализ** для проверки синтаксиса.  
  
8.  Если синтаксис правильный, появится сообщение «Синтаксический анализ успешно завершен». При обнаружении ошибки исправьте ее.  
  
9. Щелкните вкладку **Дополнительно** , чтобы задать следующие параметры шага задания: какое действие необходимо выполнить при успешном или неуспешном выполнении шага задания, сколько раз агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен пытаться выполнить шаг задания, а также файл или таблицу, куда агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может записывать результат выполнения шага задания. Только члены предопределенной роли сервера **sysadmin** могут записывать выходные данные шага задания в файл операционной системы. В таблицу выходные данные могут записывать все пользователи агента SQL Server.  
  
10. Если члену предопределенной роли сервера **sysadmin** нужно выполнить шаг задания в контексте другого имени входа SQL, ему следует выбрать имя входа SQL из списка **Выполнять от имени** .  
  
##  <a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-transact-sql-job-step"></a>Создание шага задания Transact-SQL  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
    -- creates a job step that uses Transact-SQL  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).  
  
##  <a name="SMO"></a>Использование управляющие объекты SQL Server  
 **Создание шага задания Transact-SQL**  
  
 Воспользуйтесь классом `JobStep` в любом языке программирования (Visual Basic, Visual C# или PowerShell).  
