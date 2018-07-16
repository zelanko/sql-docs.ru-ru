---
title: Создание шага задания со службами Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- job steps [Analysis Services]
ms.assetid: 03d4bb86-514b-4a55-97b9-c2c0fa08b428
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ca39e4dcd48bea68b59e529ef6103baabdc2093b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37326954"
---
# <a name="create-an-analysis-services-job-step"></a>Create an Analysis Services Job Step
  В этом разделе описан процесс создания и определения в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] шагов заданий агента [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , которые выполняют команды и запросы служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Services с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов SQL Server (SMO).  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Создание шагов заданий SQL Server с помощью команд или запросов служб Analysis Services с использованием следующих средств.**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Если шаг задания использует команду служб Analysis Services, то инструкция команды должна быть методом XMLA **Execute** . Инструкция не может содержать полный конверт SOAP или метод **Discover** XML для аналитики. Хотя в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] поддерживаются полные конверты SOAP и метод **Discover** , шаги заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в ней не поддерживаются. Дополнительные сведения о XML для служб Analysis Services см. в разделе [Общие сведения о XML для аналитики (XMLA)](http://msdn.microsoft.com/library/ms187190.aspx).  
  
-   Если шаг задания использует запрос служб Analysis Services, то инструкция запроса команды должна быть запросом многомерных выражений (MDX). Дополнительные сведения о многомерных Выражениях см. в разделе [основные принципы запросов многомерных Выражений &#40;служб Analysis Services&#41;](../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
  
-   Чтобы запустить шаг задания, использующий подсистему служб Analysis Services, пользователь должен быть членом предопределенной роли сервера **sysadmin** или обладать правом доступа к правильной учетной записи-посреднику, определенной для использования этой подсистемы. К тому же учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или его учетная запись-посредник должна быть учетной записью администратора служб Analysis Services и правильной учетной записью домена Windows.  
  
-   Записывать выходные данные шага задания в файл могут только элементы предопределенной роли сервера **sysadmin** . Если шаги задания выполняются пользователями, которые являются элементами роли базы данных **SQLAgentUserRole** в базе данных **msdb** , то выходные данные можно записать только в таблицу. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывает выходные данные шага задания в таблицу **sysjobstepslog** базы данных **msdb** .  
  
-   Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-an-analysis-services-command-job-step"></a>Создание шага задания команды службы Analysis Services  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните **Агент SQL Server**, создайте задание или щелкните правой кнопкой мыши существующее задание и выберите пункт **Свойства**. Дополнительные сведения о создании заданий см. в разделе [Создание заданий](create-jobs.md).  
  
3.  В диалоговом окне **Свойства задания** выберите страницу **Шаги** и нажмите кнопку **Добавить**.  
  
4.  В диалоговом окне **Новый шаг задания** введите **Имя шага**задания.  
  
5.  В списке **Типы** выберите **Команда служб SQL Server Analysis Services**.  
  
6.  В списке **Выполнять как** выберите учетную запись-посредник, определенную для использования подсистемы команд служб Analysis Services. Пользователь, являющийся членом предопределенной роли сервера **sysadmin** , также может выбрать **Учетную запись службы агента SQL Server** , чтобы запустить этот шаг задания.  
  
7.  Выберите **Сервер** , на котором будет выполняться шаг задания, или введите имя сервера.  
  
8.  Введите инструкцию в поле **Команда** или нажмите кнопку **Открыть** , чтобы выбрать инструкцию.  
  
9. Перейдите на страницу **Дополнительно** , чтобы определить параметры данного шага задания, например действия, которые должны быть выполнены агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в случае успешного или неуспешного выполнения этого шага, количество попыток выполнения шага задания, а также место записи результатов шага задания.  
  
#### <a name="to-create-an-analysis-services-query-job-step"></a>Создание шага задания запроса служб Analysis Services  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните **Агент SQL Server**, создайте задание или щелкните правой кнопкой мыши существующее задание и выберите пункт **Свойства**. Дополнительные сведения о создании заданий см. в разделе [Создание заданий](create-jobs.md).  
  
3.  В диалоговом окне **Свойства задания** выберите страницу **Шаги** и нажмите кнопку **Добавить**.  
  
4.  В диалоговом окне **Новый шаг задания** введите **имя шага**задания.  
  
5.  В списке **Типы** выберите **Запрос служб SQL Server Analysis Services**.  
  
6.  В списке **Выполнять как** выберите учетную запись-посредник, определенную для использования подсистемы Query служб Analysis Services. Пользователь, являющийся членом предопределенной роли сервера **sysadmin** , также может выбрать **Учетную запись службы агента SQL Server** , чтобы запустить этот шаг задания.  
  
7.  Выберите пункты **Сервер** и **База данных** , на которых будет выполняться шаг задания, или введите имя сервера или базы данных.  
  
8.  Введите инструкцию в поле **Команда** или нажмите кнопку **Открыть** , чтобы выбрать инструкцию.  
  
9. Перейдите на страницу **Дополнительно** , чтобы определить параметры данного шага задания, например действия, которые должны быть выполнены агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в случае успешного или неуспешного выполнения этого шага, количество попыток выполнения шага задания, а также место записи результатов шага задания.  
  
##  <a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-create-an-analysis-services-command-job-step"></a>Создание шага задания команды службы Analysis Services  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
  
              -- Creates a job step that uses XMLA to create a relational data source that references the AdventureWorks2012 Microsoft SQL Server database  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Create a relational data source that references the AdventureWorks2012 Microsoft SQL Server database ',  
        @subsystem = N'ANALYSISCOMMAND',  
        @command = N' <Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
        <ParentObject>  
            <DatabaseID>AdventureWorks2012</DatabaseID>  
        </ParentObject>  
        <ObjectDefinition>  
            <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
                <ID>AdventureWorks2012</ID>  
                <Name>Adventure Works 2012</Name>  
                <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorks2012;Integrated Security=True</ConnectionString>  
                <ImpersonationInfo>  
                    <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
                </ImpersonationInfo>  
                <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
                <Timeout>PT0S</Timeout>  
            </DataSource>  
        </ObjectDefinition>  
    </Create>', ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).  
  
#### <a name="to-create-an-analysis-services-query-job-step"></a>Создание шага задания запроса служб Analysis Services  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
  
              -- Creates a job step that uses MDX to return data  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Returns the Internet sales amount by state',  
        @subsystem = N'ANALYSISQUERY',  
        @command = N' SELECT  
       [Measures].[Internet Sales Amount] ON COLUMNS,  
       [Customer].[State-Province].Members ON ROWS  
    FROM [AdventureWorks2012]',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).  
  
##  <a name="SMO"></a> Использование управляющих объектов SQL Server  
 **Создание шага задания скрипта PowerShell**  
  
 Используйте класс `JobStep` в выбранном языке программирования, например XMLA или MDX. Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
  
