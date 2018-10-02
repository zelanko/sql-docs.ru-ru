---
title: Пошаговое руководство. Расширение процесса развертывания для проекта базы данных для изменения плана развертывания | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 22b077b1-fa25-49ff-94f6-6d0d196d870a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f0bf343b332a92b88aab32a12eace6052b6b9b60
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47652822"
---
# <a name="walkthrough-extend-database-project-deployment-to-modify-the-deployment-plan"></a>Пошаговое руководство. Расширение процесса развертывания проекта базы данных для изменения плана развертывания
Можно создать участников развертывания для выполнения специализированных действий при развертывании проекта SQL. Возможные типы участников — [DeploymentPlanModifier](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx) и [DeploymentPlanExecutor](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanexecutor.aspx). Используйте [DeploymentPlanModifier](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx) для изменения плана до его выполнения и [DeploymentPlanExecutor](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanexecutor.aspx) для осуществления операций в ходе выполнения плана. В этом пошаговом руководстве показано, как создать [DeploymentPlanModifier](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx) с именем SqlRestartableScriptContributor, чтобы добавлять инструкции IF к пакетам в скрипте развертывания. Таким образом можно разрешить в скрипте повторный запуск пакетов, пока они не будут успешно завершены, если в ходе выполнения возникает ошибка.  
  
В этом пошаговом руководстве показано выполнение следующих основных задач:  
  
-   [создание участника развертывания типа DeploymentPlanModifier](#CreateDeploymentContributor);  
  
-   [установка участника развертывания](#InstallDeploymentContributor);  
  
-   [выполнение или тестирование применяемого участника развертывания](#TestDeploymentContributor).  
  
## <a name="prerequisites"></a>предварительные требования  
Для выполнения этого пошагового руководства требуются следующие компоненты:  
  
-   Необходимо установить версию Visual Studio, которая включает SQL Server Data Tools и поддерживает разработку VB или C#.  
  
-   Необходимо иметь проект SQL, который содержит объекты SQL.  
  
-   Экземпляр SQL Server, на котором можно развернуть проект базы данных.  
  
> [!NOTE]  
> Это пошаговое руководство предназначено для пользователей, уже знакомых с функциями SQL пакета SQL Server Data Tools. Предполагается также знакомство с основными средствами Visual Studio, такими как создание библиотеки классов и использование редактора кода для добавления кода к классу.  
  
## <a name="CreateDeploymentContributor"></a>Создание участника развертывания  
Для создания участника развертывания необходимо выполнить следующие задачи:  
  
-   Создать проект библиотеки классов и добавить необходимые ссылки.  
  
-   Определить класс с именем SqlRestartableScriptContributor, который наследует от [DeploymentPlanModifier](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx).  
  
-   Переопределить метод [OnExecute](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplancontributor.onexecute.aspx).  
  
-   Добавить закрытые вспомогательные методы.  
  
-   Построить результирующую сборку.  
  
#### <a name="to-create-a-class-library-project"></a>Создание проекта библиотеки классов  
  
1.  Создайте проект библиотеки классов Visual C# или Visual Basic с именем MyOtherDeploymentContributor.  
  
2.  Переименуйте файл Class1.cs в SqlRestartableScriptContributor.cs.  
  
3.  В обозревателе решений щелкните правой кнопкой мыши узел проекта, затем выберите команду **Добавить ссылку**.  
  
4.  Выберите **System.ComponentModel.Composition** на вкладке "Платформы".  
  
5.  Щелкните **Обзор**, перейдите к каталогу **C:\Program Files (x86)\Microsoft SQL Server\110\SDK\Assemblies**, выберите **Microsoft.SqlServer.TransactSql.ScriptDom.dll** и нажмите кнопку **ОК**.  
  
6.  Добавьте необходимые ссылки SQL — щелкните правой кнопкой мыши узел проекта, затем нажмите **Добавить ссылку**. Щелкните **Обзор** и перейдите к папке **C:\Program Files (x86)\Microsoft SQL Server\110\DAC\Bin**. Выберите записи **Microsoft.SqlServer.Dac.dll**, **Microsoft.SqlServer.Dac.Extensions.dll** и **Microsoft.Data.Tools.Schema.Sql.dll**, щелкните **Добавить**, а затем нажмите кнопку **ОК**.  
  
После этого приступите к добавлению кода к классу.  
  
#### <a name="to-define-the-sqlrestartablescriptcontributor-class"></a>Определение класса SqlRestartableScriptContributor  
  
1.  В редакторе кода обновите файл class1.cs для согласования со следующими **используемыми** инструкциями:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Globalization;  
    using System.Text;  
    using Microsoft.SqlServer.Dac.Deployment;  
    using Microsoft.SqlServer.Dac.Model;  
    using Microsoft.SqlServer.TransactSql.ScriptDom;  
    ```  
  
2.  Обновите определение класса для согласования со следующим примером:  
  
    ```csharp  
        /// <summary>  
    /// This deployment contributor modifies a deployment plan by adding if statements  
    /// to the existing batches in order to make a deployment script able to be rerun to completion  
    /// if an error is encountered during execution  
    /// </summary>  
    [ExportDeploymentPlanModifier("MyOtherDeploymentContributor.RestartableScriptContributor", "1.0.0.0")]  
    public class SqlRestartableScriptContributor : DeploymentPlanModifier  
    {  
    }  
  
    ```  
  
    Теперь вы определили участника развертывания, который наследует от [DeploymentPlanModifier](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx). В ходе сборки и развертывания специализированные участники загружаются из каталога стандартных расширений. Участники, изменяющие план развертывания, обозначаются атрибутом [ExportDeploymentPlanModifier](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.exportdeploymentplanmodifierattribute.aspx). Этот атрибут требуется для обнаружения участников. Атрибут должен выглядеть примерно так:  
  
    ```csharp  
    [ExportDeploymentPlanModifier("MyOtherDeploymentContributor.RestartableScriptContributor", "1.0.0.0")]  
  
    ```  
  
3.  Добавьте следующие объявления элементов:  
  
    ```vb  
         private const string BatchIdColumnName = "BatchId";  
            private const string DescriptionColumnName = "Description";  
  
            private const string CompletedBatchesVariableName = "CompletedBatches";  
            private const string CompletedBatchesVariable = "$(CompletedBatches)";  
            private const string CompletedBatchesSqlCmd = @":setvar " + CompletedBatchesVariableName + " __completedBatches_{0}_{1}";  
            private const string TotalBatchCountSqlCmd = @":setvar TotalBatchCount {0}";  
            private const string CreateCompletedBatchesTable = @"  
    if OBJECT_ID(N'tempdb.dbo." + CompletedBatchesVariable + @"', N'U') is null  
    begin  
    use tempdb  
    create table [dbo].[$(CompletedBatches)]  
    (  
    BatchId int primary key,  
    Description nvarchar(300)  
    )  
    use [$(DatabaseName)]  
    end  
    ";  
  
    ```  
  
    Затем необходимо переопределить метод OnExecute для добавления кода, который должен быть выполнен при развертывании проекта базы данных.  
  
#### <a name="to-override-onexecute"></a>Переопределение метода OnExecute  
  
1.  Добавьтесь следующий метод к применяемому классу SqlRestartableScriptContributor:  
  
    ```csharp  
    /// <summary>  
    /// You override the OnExecute method to do the real work of the contributor.  
    /// </summary>  
    /// <param name="context"></param>  
    protected override void OnExecute(DeploymentPlanContributorContext context)  
    {  
         // Replace this with the method body  
    }  
  
    ```  
  
    Метод [OnExecute](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplancontributor.onexecute.aspx) переопределяется из базового класса [DeploymentPlanContributor](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplancontributor.aspx), являющегося базовым и для [DeploymentPlanModifier](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx), и для [DeploymentPlanExecutor](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanexecutor.aspx). В метод OnExecute передается объект [DeploymentPlanContributorContext](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplancontributorcontext.aspx), который предоставляет доступ ко всем указанным аргументам, модели базы данных-источника и целевой базы данных, плану развертывания и вариантам развертывания. В этом примере должны быть получены план развертывания и имя целевой базы данных.  
  
2.  Перейдем к добавлению начала текста в метод OnExecute:  
  
    ```vb  
    // Obtain the first step in the Plan from the provided context  
    DeploymentStep nextStep = context.PlanHandle.Head;  
    int batchId = 0;  
    BeginPreDeploymentScriptStep beforePreDeploy = null;  
  
    // Loop through all steps in the deployment plan  
    while (nextStep != null)  
    {  
        // Increment the step pointer, saving both the current and next steps  
        DeploymentStep currentStep = nextStep;  
        nextStep = currentStep.Next;  
  
        // Add additional step processing here  
    }  
  
    // if we found steps that required processing, set up a temporary table to track the work that you are doing  
    if (beforePreDeploy != null)  
    {  
        // Add additional post-processing here  
    }  
  
    // Cleanup and drop the table   
    DeploymentScriptStep dropStep = new DeploymentScriptStep(DropCompletedBatchesTable);  
    base.AddAfter(context.PlanHandle, context.PlanHandle.Tail, dropStep);  
  
    ```  
  
    Этот код определяет несколько локальных переменных и задает цикл, осуществляющий обработку всех шагов плана развертывания. После завершения цикла необходимо выполнить некоторую последующую обработку и удалить временную таблицу, созданную во время развертывания для отслеживания хода выполнения плана. Основными применяемыми здесь типами являются [DeploymentStep](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentstep.aspx) и [DeploymentScriptStep](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentscriptstep.aspx). Основной метод — AddAfter.  
  
3.  Теперь добавим дополнительный шаг обработки вместо комментария с текстом «Ввести дополнительный шаг обработки здесь»:  
  
    ```csharp  
    // Look for steps that mark the pre/post deployment scripts  
    // These steps will always be in the deployment plan even if the  
    // user's project does not have a pre/post deployment script  
    if (currentStep is BeginPreDeploymentScriptStep)  
    {  
        // This step marks the begining of the predeployment script.  
        // Save the step and move on.  
        beforePreDeploy = (BeginPreDeploymentScriptStep)currentStep;  
        continue;  
    }  
    if (currentStep is BeginPostDeploymentScriptStep)  
    {  
        // This is the step that marks the beginning of the post deployment script.    
        // We do not continue processing after this point.  
        break;  
    }  
    if (currentStep is SqlPrintStep)  
    {  
        // We do not need to put if statements around these  
        continue;  
    }  
  
    // if we have not yet found the beginning of the pre-deployment script steps,   
    // skip to the next step.  
    if (beforePreDeploy == null)  
    {  
        // We only surround the "main" statement block with conditional  
        // statements  
        continue;  
    }  
  
    // Determine if this is a step that we need to surround with a conditional statement  
    DeploymentScriptDomStep domStep = currentStep as DeploymentScriptDomStep;  
    if (domStep == null)  
    {  
        // This step is not a step that we know how to modify,  
        // so skip to the next step.  
        continue;  
    }  
  
    TSqlScript script = domStep.Script as TSqlScript;  
    if (script == null)  
    {  
        // The script dom step does not have a script with batches - skip  
        continue;  
    }  
  
        // Loop through all the batches in the script for this step.  All the statements  
        // in the batch will be enclosed in an if statement that will check the  
        // table to ensure that the batch has not already been executed  
        TSqlObject sqlObject;  
        string stepDescription;  
        GetStepInfo(domStep, out stepDescription, out sqlObject);  
        int batchCount = script.Batches.Count;  
  
    for (int batchIndex = 0; batchIndex < batchCount; batchIndex++)  
    {  
        // Add batch processing here  
    }  
  
    ```  
  
    Комментарии в коде поясняют выполняемую обработку. Вкратце можно отметить, что в этом коде происходит поиск интересующих нас шагов, пропуск других шагов и останов после достижения начала шагов, следующих за развертыванием. Если шаг содержит инструкции, которые необходимо заключить в условные операции, выполняется дополнительная обработка. К основным типам, методам и свойствам относятся [BeginPreDeploymentScriptStep](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.beginpredeploymentscriptstep.aspx), [BeginPostDeploymentScriptStep](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.beginpostdeploymentscriptstep.aspx), [TSqlObject](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlobject.aspx), [TSqlScript](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.tsqlscript.aspx), Script, [DeploymentScriptDomStep](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentscriptdomstep.aspx) и [SqlPrintStep](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.sqlprintstep.aspx).  
  
4.  Теперь добавим код пакетной обработки вместо комментария с текстом «Ввести пакетную обработку здесь»:  
  
    ```csharp  
        // Create the if statement that will contain the batch's contents  
        IfStatement ifBatchNotExecutedStatement = CreateIfNotExecutedStatement(batchId);  
        BeginEndBlockStatement statementBlock = new BeginEndBlockStatement();  
        ifBatchNotExecutedStatement.ThenStatement = statementBlock;  
        statementBlock.StatementList = new StatementList();  
  
        TSqlBatch batch = script.Batches[batchIndex];  
        int statementCount = batch.Statements.Count;  
  
        // Loop through all statements in the batch, embedding those in an sp_execsql  
        // statement that must be handled this way (schemas, stored procedures,   
        // views, functions, and triggers).  
        for (int statementIndex = 0; statementIndex < statementCount; statementIndex++)  
        {  
            // Add additional statement processing here  
        }  
  
        // Add an insert statement to track that all the statements in this  
        // batch were executed.  Turn on nocount to improve performance by  
        // avoiding row inserted messages from the server  
        string batchDescription = string.Format(CultureInfo.InvariantCulture,  
            "{0} batch {1}", stepDescription, batchIndex);  
  
        PredicateSetStatement noCountOff = new PredicateSetStatement();  
        noCountOff.IsOn = false;  
        noCountOff.Options = SetOptions.NoCount;  
  
        PredicateSetStatement noCountOn = new PredicateSetStatement();  
        noCountOn.IsOn = true;  
        noCountOn.Options = SetOptions.NoCount;   
        InsertStatement batchCompleteInsert = CreateBatchCompleteInsert(batchId, batchDescription);  
        statementBlock.StatementList.Statements.Add(noCountOn);  
    statementBlock.StatementList.Statements.Add(batchCompleteInsert);  
        statementBlock.StatementList.Statements.Add(noCountOff);  
  
        // Remove all the statements from the batch (they are now in the if block) and add the if statement  
        // as the sole statement in the batch  
        batch.Statements.Clear();  
        batch.Statements.Add(ifBatchNotExecutedStatement);  
  
        // Next batch  
        batchId++;  
  
    ```  
  
    В этом коде создается инструкция IF с блоком BEGIN/END. Затем выполняется дополнительная обработка инструкций пакета. После ее завершения добавляется инструкция INSERT для ввода информации во временную таблицу, которая отслеживает ход выполнения скрипта. Наконец, обновим пакет, заменив инструкции, которые использовались с новой инструкцией IF, содержащей указанные инструкции. Основные типы, методы и свойства включают [IfStatement](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.ifstatement.aspx), [BeginEndBlockStatement](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.beginendblockstatement.aspx), [StatementList](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.statementlist.aspx), [TSqlBatch](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.tsqlbatch.aspx), [PredicateSetStatement](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.predicatesetstatement.aspx), [SetOptions](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.setoptions.aspx) и [InsertStatement](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.insertstatement.aspx).  
  
5.  Теперь добавим текст инструкции, реализующей цикл. Замените комментарий с текстом «Введите дополнительную обработку инструкции здесь»:  
  
    ```csharp  
    TSqlStatement smnt = batch.Statements[statementIndex];  
  
    if (IsStatementEscaped(sqlObject))  
    {  
        // "escape" this statement by embedding it in a sp_executesql statement  
        string statementScript;  
        domStep.ScriptGenerator.GenerateScript(smnt, out statementScript);  
        ExecuteStatement spExecuteSql = CreateExecuteSql(statementScript);  
        smnt = spExecuteSql;  
    }  
  
    statementBlock.StatementList.Statements.Add(smnt);  
  
    ```  
  
    Применительно к каждой инструкции в пакете, если эта инструкция относится к типу, требующему заключения в инструкцию sp_executesql, внесите в эту инструкцию соответствующие изменения. Затем в коде добавляется инструкция к списку инструкций, относящемуся к созданному блоку BEGIN/END. Основные типы, методы и свойства включают [TSqlStatement](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.tsqlstatement.aspx) и [ExecuteStatement](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.executestatement.aspx).  
  
6.  Наконец, добавьте раздел для последующей обработки вместо комментария с текстом «Введите дополнительную последующую обработку здесь»:  
  
    ```csharp  
    // Declare a SqlCmd variables.  
    //  
    // CompletedBatches variable - defines the name of the table in tempdb that will track  
    // all the completed batches.  The temporary table's name has the target database name and  
    // a guid embedded in it so that:  
    // * Multiple deployment scripts targeting different DBs on the same server  
    // * Failed deployments with old tables do not conflict with more recent deployments  
    //  
    // TotalBatchCount variable - the total number of batches surrounded by if statements.  Using this  
    // variable pre/post deployment scripts can also use the CompletedBatches table to make their  
    // script rerunnable if there is an error during execution  
    StringBuilder sqlcmdVars = new StringBuilder();  
    sqlcmdVars.AppendFormat(CultureInfo.InvariantCulture, CompletedBatchesSqlCmd,  
        context.Options.TargetDatabaseName, Guid.NewGuid().ToString("D"));  
    sqlcmdVars.AppendLine();  
    sqlcmdVars.AppendFormat(CultureInfo.InvariantCulture, TotalBatchCountSqlCmd, batchId);  
  
    DeploymentScriptStep completedBatchesSetVarStep = new DeploymentScriptStep(sqlcmdVars.ToString());  
    base.AddBefore(context.PlanHandle, beforePreDeploy, completedBatchesSetVarStep);  
  
    // Create the temporary table we will use to track the work that we are doing  
    DeploymentScriptStep createStatusTableStep = new DeploymentScriptStep(CreateCompletedBatchesTable);  
    base.AddBefore(context.PlanHandle, beforePreDeploy, createStatusTableStep);  
  
    ```  
  
    Если в ходе обработки обнаруживаются один или несколько шагов, заключенных в условные операторы, необходимо добавить в скрипт развертывания инструкции задания переменных SQLCMD. Первая переменная CompletedBatches содержит уникальное имя для временной таблицы, используемой в скрипте развертывания для отслеживания того, какие пакеты были успешно завершены при выполнении скрипта. Вторая переменная TotalBatchCount содержит общее число пакетов в скрипте развертывания.  
  
    Дополнительные типы, свойства и методы, представляющие интерес, включают:  
  
    StringBuilder, [DeploymentScriptStep](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentscriptstep.aspx) и AddBefore.  
  
    Затем необходимо определить вспомогательные методы, вызываемые этим методом.  
  
#### <a name="to-add-the-helper-methods"></a>Добавление вспомогательных методов  
  
-   Может быть определен целый ряд вспомогательных методов. К важным методам относятся следующие.  
  
    |**Метод**|**Описание**|  
    |--------------|-------------------|  
    |CreateExecuteSQL|Определение метода CreateExecuteSQL для включения предоставленной инструкции в инструкцию EXEC sp_executesql. К основным типам, методам и свойствам относятся [ExecuteStatement](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.executestatement.aspx), [ExecutableProcedureReference](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.executableprocedurereference.aspx), [SchemaObjectName](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.schemaobjectname.aspx), [ProcedureReference](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.procedurereference.aspx) и [ExecuteParameter](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.executeparameter.aspx).|  
    |CreateCompletedBatchesName|Определение метода CreateCompletedBatchesName. С помощью этого метода создается имя, которое будет вставлено во временную таблицу для пакета. К основным типам, методам и свойствам относится [SchemaObjectName](http://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.schemaobjectname.aspx).|  
    |IsStatementEscaped|Определение метода IsStatementEscaped. Этот метод определяет, относится ли элемент модели к такому типу, который требует заключения инструкции в инструкцию EXEC sp_executesql, прежде чем ее можно будет включить в инструкцию IF. К основным типам, методам и свойствам относятся TSqlObject.ObjectType, ModelTypeClass и свойство TypeClass для следующих типов моделей: Schema, Procedure, View,  TableValuedFunction, ScalarFunction, DatabaseDdlTrigger, DmlTrigger, ServerDdlTrigger.|  
    |CreateBatchCompleteInsert|Определение метода CreateBatchCompleteInsert. Этот метод создает инструкцию INSERT, которая добавляется к скрипту развертывания для отслеживания хода выполнения скрипта. К основным типам, методам и свойствам относятся InsertStatement, NamedTableReference, ColumnReferenceExpression, ValuesInsertSource и RowValue.|  
    |CreateIfNotExecutedStatement|Определение метода CreateIfNotExecutedStatement. Этот метод создает инструкцию IF для проверки того, показывают ли результаты в таблице выполнения временных пакетов, что этот пакет уже выполнялся. К основным типам, методам и свойствам относятся IfStatement, ExistsPredicate, ScalarSubquery, NamedTableReference, WhereClause, ColumnReferenceExpression, IntegerLiteral, BooleanComparisonExpression и BooleanNotExpression.|  
    |GetStepInfo|Определение метода GetStepInfo. Этот метод извлекает сведения об элементе модели, используемом для создания скрипта данного шага, в дополнение к имени шага. Типы и методы, представляющие интерес, включают [DeploymentPlanContributorContext](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplancontributorcontext.aspx), [DeploymentScriptDomStep](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentscriptdomstep.aspx), [TSqlObject](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlobject.aspx), [CreateElementStep](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.createelementstep.aspx), [AlterElementStep](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.alterelementstep.aspx) и [DropElementStep](http://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.dropelementstep.aspx).|  
    |GetElementName|Создает отформатированное имя для TSqlObject.|  
  
1.  Добавьте следующий код для определения вспомогательных методов:  
  
    ```csharp  
  
    /// <summary>  
    /// The CreateExecuteSql method "wraps" the provided statement script in an "sp_executesql" statement  
    /// Examples of statements that must be so wrapped include: stored procedures, views, and functions  
    /// </summary>  
    private static ExecuteStatement CreateExecuteSql(string statementScript)  
    {  
        // define a new Exec statement  
        ExecuteStatement executeSp = new ExecuteStatement();  
        ExecutableProcedureReference spExecute = new ExecutableProcedureReference();  
        executeSp.ExecuteSpecification = new ExecuteSpecification { ExecutableEntity = spExecute };  
  
        // define the name of the procedure that you want to execute, in this case sp_executesql  
        SchemaObjectName procName = new SchemaObjectName();  
        procName.Identifiers.Add(CreateIdentifier("sp_executesql", QuoteType.NotQuoted));  
        ProcedureReference procRef = new ProcedureReference { Name = procName };  
  
        spExecute.ProcedureReference = new ProcedureReferenceName { ProcedureReference = procRef };  
  
        // add the script parameter, constructed from the provided statement script  
        ExecuteParameter scriptParam = new ExecuteParameter();  
        spExecute.Parameters.Add(scriptParam);  
        scriptParam.ParameterValue = new StringLiteral { Value = statementScript };  
        scriptParam.Variable = new VariableReference { Name = "@stmt" };  
        return executeSp;  
    }  
  
    /// <summary>  
    /// The CreateIdentifier method returns a Identifier with the specified value and quoting type  
    /// </summary>  
    private static Identifier CreateIdentifier(string value, QuoteType quoteType)  
    {  
        return new Identifier { Value = value, QuoteType = quoteType };  
    }  
  
    /// <summary>  
    /// The CreateCompletedBatchesName method creates the name that will be inserted  
    /// into the temporary table for a batch.  
    /// </summary>  
    private static SchemaObjectName CreateCompletedBatchesName()  
    {  
        SchemaObjectName name = new SchemaObjectName();  
        name.Identifiers.Add(CreateIdentifier("tempdb", QuoteType.SquareBracket));  
        name.Identifiers.Add(CreateIdentifier("dbo", QuoteType.SquareBracket));  
        name.Identifiers.Add(CreateIdentifier(CompletedBatchesVariable, QuoteType.SquareBracket));  
        return name;  
    }  
  
    /// <summary>  
    /// Helper method that determins whether the specified statement needs to  
    /// be escaped  
    /// </summary>  
    /// <param name="sqlObject"></param>  
    /// <returns></returns>  
    private static bool IsStatementEscaped(TSqlObject sqlObject)  
    {  
        HashSet<ModelTypeClass> escapedTypes = new HashSet<ModelTypeClass>  
        {  
            Schema.TypeClass,  
            Procedure.TypeClass,  
            View.TypeClass,  
            TableValuedFunction.TypeClass,  
            ScalarFunction.TypeClass,  
            DatabaseDdlTrigger.TypeClass,  
            DmlTrigger.TypeClass,  
            ServerDdlTrigger.TypeClass  
        };  
        return escapedTypes.Contains(sqlObject.ObjectType);  
    }  
  
    /// <summary>  
    /// Helper method that creates an INSERT statement to track a batch being completed  
    /// </summary>  
    /// <param name="batchId"></param>  
    /// <param name="batchDescription"></param>  
    /// <returns></returns>  
    private static InsertStatement CreateBatchCompleteInsert(int batchId, string batchDescription)  
    {  
        InsertStatement insert = new InsertStatement();  
        NamedTableReference batchesCompleted = new NamedTableReference();  
        insert.InsertSpecification = new InsertSpecification();  
        insert.InsertSpecification.Target = batchesCompleted;  
        batchesCompleted.SchemaObject = CreateCompletedBatchesName();  
  
        // Build the columns inserted into  
        ColumnReferenceExpression batchIdColumn = new ColumnReferenceExpression();  
        batchIdColumn.MultiPartIdentifier = new MultiPartIdentifier();  
        batchIdColumn.MultiPartIdentifier.Identifiers.Add(CreateIdentifier(BatchIdColumnName, QuoteType.NotQuoted));  
  
        ColumnReferenceExpression descriptionColumn = new ColumnReferenceExpression();  
        descriptionColumn.MultiPartIdentifier = new MultiPartIdentifier();  
        descriptionColumn.MultiPartIdentifier.Identifiers.Add(CreateIdentifier(DescriptionColumnName, QuoteType.NotQuoted));  
  
        insert.InsertSpecification.Columns.Add(batchIdColumn);  
        insert.InsertSpecification.Columns.Add(descriptionColumn);  
  
        // Build the values inserted  
        ValuesInsertSource valueSource = new ValuesInsertSource();  
        insert.InsertSpecification.InsertSource = valueSource;  
  
        RowValue values = new RowValue();  
        values.ColumnValues.Add(new IntegerLiteral { Value = batchId.ToString() });  
        values.ColumnValues.Add(new StringLiteral { Value = batchDescription });  
        valueSource.RowValues.Add(values);  
  
        return insert;  
    }  
  
    /// <summary>  
    /// This is a helper method that generates an if statement that checks the batches executed  
    /// table to see if the current batch has been executed.  The if statement will look like this  
    ///   
    /// if not exists(select 1 from [tempdb].[dbo].[$(CompletedBatches)]   
    ///                where BatchId = batchId)  
    /// begin  
    /// end  
    /// </summary>  
    /// <param name="batchId"></param>  
    /// <returns></returns>  
    private static IfStatement CreateIfNotExecutedStatement(int batchId)  
    {  
        // Create the exists/select statement  
        ExistsPredicate existsExp = new ExistsPredicate();  
        ScalarSubquery subQuery = new ScalarSubquery();  
        existsExp.Subquery = subQuery;  
  
        subQuery.QueryExpression = new QuerySpecification  
        {  
            SelectElements =  
            {  
                new SelectScalarExpression  { Expression = new IntegerLiteral { Value ="1" } }  
            },  
            FromClause = new FromClause  
            {  
                TableReferences =  
                    {  
                        new NamedTableReference() { SchemaObject = CreateCompletedBatchesName() }  
                    }  
            },  
            WhereClause = new WhereClause  
            {  
                SearchCondition = new BooleanComparisonExpression  
                {  
                    ComparisonType = BooleanComparisonType.Equals,  
                    FirstExpression = new ColumnReferenceExpression  
                    {  
                        MultiPartIdentifier = new MultiPartIdentifier  
                        {  
                            Identifiers = { CreateIdentifier(BatchIdColumnName, QuoteType.SquareBracket) }  
                        }  
                    },  
                    SecondExpression = new IntegerLiteral { Value = batchId.ToString() }  
                }  
            }  
        };  
  
        // Put together the rest of the statement  
        IfStatement ifNotExists = new IfStatement  
        {  
            Predicate = new BooleanNotExpression  
            {  
                Expression = existsExp  
            }  
        };  
  
        return ifNotExists;  
    }  
  
    /// <summary>  
    /// Helper method that generates a useful description of the step.  
    /// </summary>  
    private static void GetStepInfo(  
        DeploymentScriptDomStep domStep,  
        out string stepDescription,  
        out TSqlObject element)  
    {  
        element = null;  
  
        // figure out what type of step we've got, and retrieve  
        // either the source or target element.  
        if (domStep is CreateElementStep)  
        {  
            element = ((CreateElementStep)domStep).SourceElement;  
        }  
        else if (domStep is AlterElementStep)  
        {  
            element = ((AlterElementStep)domStep).SourceElement;  
        }  
        else if (domStep is DropElementStep)  
        {  
            element = ((DropElementStep)domStep).TargetElement;  
        }  
  
        // construct the step description by concatenating the type and the fully qualified  
        // name of the associated element.  
        string stepTypeName = domStep.GetType().Name;  
        if (element != null)  
        {  
            string elementName = GetElementName(element);  
  
            stepDescription = string.Format(CultureInfo.InvariantCulture, "{0} {1}",  
                stepTypeName, elementName);  
        }  
        else  
        {  
            // if the step has no associated element, just use the step type as the description  
            stepDescription = stepTypeName;  
        }  
    }  
  
    private static string GetElementName(TSqlObject element)  
    {  
        StringBuilder name = new StringBuilder();  
        if (element.Name.HasExternalParts)  
        {  
            foreach (string part in element.Name.ExternalParts)  
            {  
                if (name.Length > 0)  
                {  
                    name.Append('.');  
                }  
                name.AppendFormat("[{0}]", part);  
            }  
        }  
  
        foreach (string part in element.Name.Parts)  
        {  
            if (name.Length > 0)  
            {  
                name.Append('.');  
            }  
            name.AppendFormat("[{0}]", part);  
        }  
  
        return name.ToString();  
    }  
  
    ```  
  
2.  Сохраните изменения в SqlRestartableScriptContributor.cs.  
  
Затем необходимо выполнить сборку библиотеки классов.  
  
#### <a name="to-sign-and-build-the-assembly"></a>Подписание и построение сборки  
  
1.  В меню **Проект** щелкните параметр **свойств MyOtherDeploymentContributor**.  
  
2.  Откройте вкладку **Подписание** .  
  
3.  Щелкните **Подписать сборку**.  
  
4.  В окне **Выберите файл ключа строгого имени** щелкните **<New>**.  
  
5.  В диалоговом окне **Создать ключ со строгим именем** в поле **Имя файла ключа**введите **MyRefKey**.  
  
6.  (Необязательно) Можно указать пароль для файла ключа для строгого имени.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  В меню **Файл** выберите команду **Сохранить все**.  
  
9. В меню **Сборка** выберите **Построить решение**.  
  
    Затем необходимо установить сборку, чтобы она загружалась при развертывании проектов SQL.  
  
## <a name="InstallDeploymentContributor"></a>Установка участника развертывания  
Для установки участника развертывания необходимо скопировать сборку и связанный файл PDB в папку Extensions.  
  
#### <a name="to-install-the-myotherdeploymentcontributor-assembly"></a>Установка сборки MyOtherDeploymentContributor  
  
1.  Затем необходимо будет скопировать данные сборки в каталог Extensions. Visual Studio при запуске идентифицирует все расширения в каталоге %Program Files%\Microsoft SQL Server\110\DAC\Bin\Extensions и его подкаталогах, чтобы сделать их доступными для использования.  
  
2.  Скопируйте файл сборки **MyOtherDeploymentContributor.dll** из выходного каталога в каталог %Program Files%\Microsoft SQL Server\110\DAC\Bin\Extensions. По умолчанию путем к cкомпилированному файлу библиотеки DLL является ПутьКВашемуРешению\ПутьКВашемуПроекту\bin\Debug или ПутьКВашемуРешению\ПутьКВашемуПроекту\bin\Release.  
  
## <a name="TestDeploymentContributor"></a>Выполнение или тестирование применяемого участника развертывания  
Для выполнения или тестирования применяемого участника развертывания необходимо выполнить следующие задачи:  
  
-   Добавить свойства к файлу SQLPROJ, планируемому для сборки.  
  
-   Развернуть проект базы данных с использованием MSBuild и предоставить соответствующие параметры.  
  
### <a name="add-properties-to-the-sql-project-sqlproj-file"></a>Добавление свойств к файлу проекта SQL (SQLPROJ)  
Необходимо всегда обновлять файл проекта SQL для указания идентификаторов участников, которые намечены для выполнения. Это можно сделать одним из двух способов.  
  
1.  Можно изменить файл SQLPROJ вручную для добавления требуемых аргументов. Этот вариант является предпочтительным, если применяемый участник не имеет каких-либо аргументов участника, требуемых для настройки, или если вы не намереваетесь повторно использовать участника сборки в большом количестве проектов. Если выбран этот вариант, введите следующие инструкции в файл SQLPROJ после первого узла Import в файле:  
  
    ```  
    <PropertyGroup>  
      <DeploymentContributors>  
        $(DeploymentContributors); MyOtherDeploymentContributor.RestartableScriptContributor  
      </DeploymentContributors>  
    </PropertyGroup>  
    ```  
  
2.  Второй метод предусматривает создание целевого файла, содержащего требуемые аргументы участника. Это удобно, если один и тот же участник используется в нескольких проектах и имеются требуемые аргументы участника, поскольку он включает значения по умолчанию. В этом случае создайте целевой файл в пути расширений MSBuild:  
  
    1.  Перейдите в каталог %Program Files%\MSBuild.  
  
    2.  Создайте папку MyContributors для сохранения своих целевых файлов.  
  
    3.  Создайте в этом каталоге файл MyContributors.targets, введите в него следующий текст и сохраните файл:  
  
        ```  
        <?xml version="1.0" encoding="utf-8"?>  
  
        <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
          <PropertyGroup>  
            <DeploymentContributors>$(DeploymentContributors);MyOtherDeploymentContributor.RestartableScriptContributor</DeploymentContributors>  
          </PropertyGroup>  
        </Project>  
  
        ```  
  
    4.  В файле SQLPROJ каждого проекта, в котором будут запускаться участники, импортируйте файл целей построения, добавив следующую инструкцию в файл SQLPROJ после узла \<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.SqlTasks.targets" \/> в файле:  
  
        ```  
        <Import Project="$(MSBuildExtensionsPath)\MyContributors\MyContributors.targets " />  
  
        ```  
  
После реализации одного из этих подходов можно использовать MSBuild для передачи параметров для командной строки сборки.  
  
> [!NOTE]  
> Необходимо всегда обновлять свойство DeploymentContributors для указания идентификатора применяемого участника. Это тот же идентификатор, который используется в атрибуте ExportDeploymentPlanModifier в файле исходного кода участника. Без этого требуемый участник не будет вызываться на выполнение при сборке проекта. Свойство ContributorArguments необходимо обновлять, только если для вызова участника на выполнение требуются аргументы.  
  
## <a name="deploy-the-database-project"></a>Развертывание проекта базы данных  
  
#### <a name="to-deploy-your-sql-project-and-generate-a-deployment-report"></a>Развертывание проекта SQL и создание отчета о развертывании  
  
-   Как правило, проект может быть опубликован или развернут в Visual Studio. Просто откройте решение, содержащее ваш проект SQL, и выберите пункт «Опубликовать...» контекстного меню для проекта или используйте клавишу F5 для отладки развертывания в LocalDB. В этом примере мы будем использовать диалоговое окно «Опубликовать...» для создания скрипта развертывания.  
  
    1.  Откройте Visual Studio и вызовите решение, содержащее проект SQL.  
  
    2.  Щелкните правой кнопкой мыши проект в обозревателе решений и выберите параметр **Опубликовать…** .  
  
    3.  Задайте имя сервера и имя базы данных для публикации в них.  
  
    4.  Выберите **Создать скрипт** в параметрах в нижней части диалогового окна. Это приведет к созданию скрипта, который может использоваться для развертывания. Изучим его в целях проверки того, добавлены ли инструкции IF, позволяющие запускать скрипт повторно.  
  
    5.  Изучите результирующий скрипт развертывания. Непосредственно перед разделом с обозначением «Шаблон скрипта, выполняемого перед развертыванием» должен присутствовать примерно такой код Transact-SQL:  
  
        ```  
        :setvar CompletedBatches __completedBatches_CompareProjectDB_cd1e348a-8f92-44e0-9a96-d25d65900fca  
        :setvar TotalBatchCount 17  
        GO  
  
        if OBJECT_ID(N'tempdb.dbo.$(CompletedBatches)', N'U') is null  
        begin  
        use tempdb  
        create table [dbo].[$(CompletedBatches)]  
        (  
        BatchId int primary key,  
        Description nvarchar(300)  
        )  
        use [$(DatabaseName)]  
        end  
  
        ```  
  
        Далее в скрипте развертывания вокруг каждого пакета должны находиться инструкции IF, окружающие эту исходную инструкцию. Например, применительно к инструкции CREATE SCHEMA может быть показано следующее:  
  
        ```  
        IF NOT EXISTS (SELECT 1  
                       FROM   [tempdb].[dbo].[$(CompletedBatches)]  
                       WHERE  [BatchId] = 0)  
            BEGIN  
                EXECUTE sp_executesql @stmt = N'CREATE SCHEMA [Sales]  
            AUTHORIZATION [dbo]';  
                SET NOCOUNT ON;  
                INSERT  [tempdb].[dbo].[$(CompletedBatches)] (BatchId, Description)  
                VALUES                                      (0, N'CreateElementStep Sales batch 0');  
                SET NOCOUNT OFF;  
            END  
  
        ```  
  
        Следует отметить, что CREATE SCHEMA — это одна из инструкций, которая должна быть заключена в инструкцию EXECUTE sp_executesql в рамках инструкции IF. Такие инструкции, как CREATE TABLE, не требуют применения инструкции EXECUTE sp_executesql и выглядят примерно так:  
  
        ```  
        IF NOT EXISTS (SELECT 1  
                       FROM   [tempdb].[dbo].[$(CompletedBatches)]  
                       WHERE  [BatchId] = 1)  
            BEGIN  
                CREATE TABLE [Sales].[Customer] (  
                    [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
                    [CustomerName] NVARCHAR (40) NOT NULL,  
                    [YTDOrders]    INT           NOT NULL,  
                    [YTDSales]     INT           NOT NULL  
                );  
                SET NOCOUNT ON;  
                INSERT  [tempdb].[dbo].[$(CompletedBatches)] (BatchId, Description)  
                VALUES                                      (1, N'CreateElementStep Sales.Customer batch 0');  
                SET NOCOUNT OFF;  
            END  
  
        ```  
  
        > [!NOTE]  
        > При развертывании проекта базы данных, которая идентична целевой базе данных, результирующий отчет не является слишком содержательным. Для получения более содержательных результатов разверните изменения в базе данных или новую базу данных.  
  
## <a name="command-line-deployment-using-generated-dacpac-file"></a>Развертывание с помощью командной строки, в котором используется созданный файл dacpac  
После сборки проекта SQL создается файл dacpac, который может использоваться для развертывания схемы из командной строки и который может обеспечить развертывание с другого компьютера, такого как компьютер сборки. SqlPackage — это программа командной строки, которая обеспечивает развертывание файлов dacpac с полным диапазоном вариантов, позволяющих пользователям, кроме всего прочего, развернуть dacpac или создать скрипт развертывания. Дополнительные сведения см. в описании [SqlPackage.exe](http://msdn.microsoft.com/library/hh550080(v=VS.103).aspx).  
  
> [!NOTE]  
> Для успешного развертывания файлов dacpac, построенных на основе проектов с заданным свойством DeploymentContributors, необходимо установить на используемом компьютере DLL-библиотеки, которые содержат применяемых участников развертывания. Это связано с тем, что участники отмечены как требуемые для успешного развертывания.  
>   
> Чтобы избавиться от необходимости выполнять это требование, исключите участника развертывания из файла SQLPROJ. Вместо этого укажите, какие участники будут вызываться для выполнения во время развертывания, используя программу SqlPackage с параметром **AdditionalDeploymentContributors**. Это удобно в тех случаях, если участник должен использоваться только в особых обстоятельствах, таких как развертывание на каком-то конкретном сервере.  
  
## <a name="next-steps"></a>Next Steps  
Можно проводить эксперименты с другими типами изменений в планах развертывания до их выполнения. Некоторые типы изменений, которые могут быть внесены, включают следующее:  
  
-   Добавление расширенного свойства ко всем объектам базы данных, с которыми связан номер версии.  
  
-   Добавление или удаление дополнительных диагностических инструкций печати или комментариев из скриптов развертывания.  
  
## <a name="see-also"></a>См. также:  
[Изменение процесса сборки и развертывания базы данных с помощью участников сборки и развертывания](../ssdt/use-deployment-contributors-to-customize-database-build-and-deployment.md)  
[Walkthrough: Extend Database Project Build to Generate Model Statistics](../ssdt/walkthrough-extend-database-project-build-to-generate-model-statistics.md) (Пошаговое руководство. Расширение сборки для проекта базы данных для создания статистики модели)  
[Walkthrough: Extend Database Project Deployment to Analyze the Deployment Plan](../ssdt/walkthrough-extend-database-project-deployment-to-analyze-the-deployment-plan.md) (Пошаговое руководство. Расширение процесса развертывания для проекта базы данных для анализа плана развертывания)  
  
