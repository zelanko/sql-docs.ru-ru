---
title: Создание шага задания со службами Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [Analysis Services]
ms.assetid: 03d4bb86-514b-4a55-97b9-c2c0fa08b428
author: stevestein
ms.author: sstein
ms.openlocfilehash: ed0e63c22d4cad270bcb544b03decba269e4f43a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054661"
---
# <a name="create-an-analysis-services-job-step"></a>Create an Analysis Services Job Step
  В этом разделе описан процесс создания и определения в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] шагов заданий агента [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , которые выполняют команды и запросы служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Services с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов SQL Server (SMO).  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Создание шагов заданий SQL Server с помощью команд или запросов служб Analysis Services с использованием следующих средств.**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Если шаг задания использует команду служб Analysis Services, то инструкция команды должна быть методом XMLA **Execute** . Инструкция не может содержать полный конверт SOAP или метод **Discover** XML для аналитики. Хотя в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] поддерживаются полные конверты SOAP и метод **Discover** , шаги заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в ней не поддерживаются. Дополнительные сведения о XML для служб Analysis Services см. в разделе [Общие сведения о XML для аналитики (XMLA)](https://msdn.microsoft.com/library/ms187190.aspx).  
  
-   Если шаг задания использует запрос служб Analysis Services, то инструкция запроса команды должна быть запросом многомерных выражений (MDX). Дополнительные сведения о многомерных выражениях см. в разделе [основные принципы запросов многомерных выражений &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
  
-   Чтобы запустить шаг задания, использующий подсистему служб Analysis Services, пользователь должен быть членом предопределенной роли сервера **sysadmin** или обладать правом доступа к правильной учетной записи-посреднику, определенной для использования этой подсистемы. К тому же учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или его учетная запись-посредник должна быть учетной записью администратора служб Analysis Services и правильной учетной записью домена Windows.  
  
-   Записывать выходные данные шага задания в файл могут только элементы предопределенной роли сервера **sysadmin** . Если шаги задания выполняются пользователями, которые являются элементами роли базы данных **SQLAgentUserRole** в базе данных **msdb** , то выходные данные можно записать только в таблицу. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывает выходные данные шага задания в таблицу **sysjobstepslog** базы данных **msdb** .  
  
-   Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-an-analysis-services-command-job-step"></a>Создание шага задания команды службы Analysis Services  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Разверните **Агент SQL Server**, создайте задание или щелкните правой кнопкой мыши существующее задание и выберите пункт **Свойства**. Дополнительные сведения о создании заданий см. в разделе [Создание заданий](create-jobs.md).  
  
3.  В диалоговом окне **Свойства задания** выберите страницу **Шаги** и нажмите кнопку **Добавить**.  
  
4.  В диалоговом окне **Новый шаг задания** введите **Имя шага**задания.  
  
5.  В списке **Типы** выберите **Команда служб SQL Server Analysis Services**.  
  
6.  В списке **Выполнять как** выберите учетную запись-посредник, определенную для использования подсистемы команд служб Analysis Services. Пользователь, являющийся членом предопределенной роли сервера **sysadmin** , также может выбрать **Учетную запись службы агента SQL Server** , чтобы запустить этот шаг задания.  
  
7.  Выберите **Сервер** , на котором будет выполняться шаг задания, или введите имя сервера.  
  
8.  Введите инструкцию в поле **Команда** или нажмите кнопку **Открыть** , чтобы выбрать инструкцию.  
  
9. Перейдите на страницу **Дополнительно** , чтобы определить параметры данного шага задания, например действия, которые должны быть выполнены агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в случае успешного или неуспешного выполнения этого шага, количество попыток выполнения шага задания, а также место записи результатов шага задания.  
  
#### <a name="to-create-an-analysis-services-query-job-step"></a>Создание шага задания запроса служб Analysis Services  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Разверните **Агент SQL Server**, создайте задание или щелкните правой кнопкой мыши существующее задание и выберите пункт **Свойства**. Дополнительные сведения о создании заданий см. в разделе [Создание заданий](create-jobs.md).  
  
3.  В диалоговом окне **Свойства задания** выберите страницу **Шаги** и нажмите кнопку **Добавить**.  
  
4.  В диалоговом окне **Новый шаг задания** введите **имя шага**задания.  
  
5.  В списке **Типы** выберите **Запрос служб SQL Server Analysis Services**.  
  
6.  В списке **Выполнять как** выберите учетную запись-посредник, определенную для использования подсистемы Query служб Analysis Services. Пользователь, являющийся членом предопределенной роли сервера **sysadmin** , также может выбрать **Учетную запись службы агента SQL Server** , чтобы запустить этот шаг задания.  
  
7.  Выберите пункты **Сервер** и **База данных** , на которых будет выполняться шаг задания, или введите имя сервера или базы данных.  
  
8.  Введите инструкцию в поле **Команда** или нажмите кнопку **Открыть** , чтобы выбрать инструкцию.  
  
9. Перейдите на страницу **Дополнительно** , чтобы определить параметры данного шага задания, например действия, которые должны быть выполнены агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в случае успешного или неуспешного выполнения этого шага, количество попыток выполнения шага задания, а также место записи результатов шага задания.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-create-an-analysis-services-command-job-step"></a>Создание шага задания команды службы Analysis Services  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
    -- Creates a job step that uses XMLA to create a relational data source that references the AdventureWorks2012 Microsoft SQL Server database  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Create a relational data source that references the AdventureWorks2012 Microsoft SQL Server database ',  
        @subsystem = N'ANALYSISCOMMAND',  
        @command = N' <Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
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
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql
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
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Использование управляющие объекты SQL Server  
 **Создание шага задания скрипта PowerShell**  
  
 Используйте класс `JobStep` в выбранном языке программирования, например XMLA или MDX. Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
