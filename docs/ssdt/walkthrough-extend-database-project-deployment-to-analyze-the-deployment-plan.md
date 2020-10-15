---
title: Расширение процесса развертывания проекта базы данных для анализа плана развертывания
description: Создайте участник развертывания DeploymentPlanExecutor. Настройте участник, который хранит записи о событиях, происходящих при развертывании проекта базы данных.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: 9ead8470-93ba-44e3-8848-b59322e37621
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 54ea252e2fbe828200339fdbfb4d25ef83451cb3
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "91987550"
---
# <a name="walkthrough-extend-database-project-deployment-to-analyze-the-deployment-plan"></a>Пошаговое руководство. Расширение процесса развертывания проекта базы данных для анализа плана развертывания

Можно создать участников развертывания для выполнения специализированных действий при развертывании проекта SQL. Предусмотрена возможность создать участников DeploymentPlanModifier и DeploymentPlanExecutor. Используйте DeploymentPlanModifier для изменения плана до его выполнения и DeploymentPlanExecutor для осуществления операций в ходе выполнения плана. В данном пошаговом руководстве будет создан DeploymentPlanExecutor с именем DeploymentUpdateReportContributor, который будет формировать отчет о действиях, выполненных при развертывании проекта. Поскольку данный участник сборки принимает параметр, управляющий формированием отчета, необходимо выполнить дополнительное действие.  
  
В этом пошаговом руководстве показано выполнение следующих основных задач:  
  
-   [создание участника развертывания с типом DeploymentPlanExecutor](#CreateDeploymentContributor);  
  
-   [установка участника развертывания](#InstallDeploymentContributor);  
  
-   [тестирование участника развертывания](#TestDeploymentContributor).  
  
## <a name="prerequisites"></a>Предварительные требования  
Для выполнения этого пошагового руководства требуются следующие компоненты:  
  
-   Необходимо установить версию Visual Studio, которая включает SQL Server Data Tools (SSDT) и поддерживает разработку VB или C#.  
  
-   Необходимо иметь проект SQL, который содержит объекты SQL.  
  
-   Экземпляр SQL Server, на котором можно развернуть проект базы данных.  
  
> [!NOTE]  
> Это пошаговое руководство предназначено для пользователей, уже знакомых с функциями SQL пакета SSDT. Предполагается также знакомство с основными средствами Visual Studio, такими как создание библиотеки классов и использование редактора кода для добавления кода к классу.  
  
## <a name="create-a-deployment-contributor"></a><a name="CreateDeploymentContributor"></a>Создание участника развертывания  
Для создания участника развертывания необходимо выполнить следующие задачи:  
  
-   Создать проект библиотеки классов и добавить необходимые ссылки.  
  
-   Определите класс с именем DeploymentUpdateReportContributor, наследуемый от [DeploymentPlanExecutor](/dotnet/api/microsoft.sqlserver.dac.deployment.deploymentplanexecutor).  
  
-   Переопределить метод OnExecute.  
  
-   Добавить закрытый вспомогательный класс.  
  
-   Построить результирующую сборку.  
  
#### <a name="to-create-a-class-library-project"></a>Создание проекта библиотеки классов  
  
1.  Создайте проект библиотеки классов Visual C# или Visual Basic с именем MyDeploymentContributor.  
  
2.  Переименуйте файл Class1.cs в DeploymentUpdateReportContributor.cs.  
  
3.  В обозревателе решений щелкните правой кнопкой мыши узел проекта, затем выберите команду **Добавить ссылку**.  
  
4.  Выберите **System.ComponentModel.Composition** на вкладке "Платформы".  
  
5.  Добавьте необходимые ссылки SQL. Для этого щелкните правой кнопкой мыши узел проекта и выберите **Добавить ссылку**. Щелкните **Обзор** и перейдите к папке **C:\Program Files (x86)\Microsoft SQL Server\110\DAC\Bin**. Выберите записи **Microsoft.SqlServer.Dac.dll**, **Microsoft.SqlServer.Dac.Extensions.dll** и **Microsoft.Data.Tools.Schema.Sql.dll**, затем щелкните **Добавить** и **ОК**.  
  
    После этого приступите к добавлению кода к классу.  
  
#### <a name="to-define-the-deploymentupdatereportcontributor-class"></a>Определение класса DeploymentUpdateReportContributor  
  
1.  В редакторе кода обновите файл DeploymentUpdateReportContributor.cs, чтобы инструкции **Using** в нем выглядели так:  
  
    ```csharp  
    using System;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using Microsoft.SqlServer.Dac.Deployment;  
    using Microsoft.SqlServer.Dac.Extensibility;  
    using Microsoft.SqlServer.Dac.Model;  
  
    ```  
  
2.  Обновите определение класса для согласования со следующим:  
  
    ```csharp  
    /// <summary>  
        /// An executor that generates a report detailing the steps in the deployment plan. Will only run  
        /// if a "GenerateUpdateReport=true" contributor argument is set in the project file, in a targets file or  
        /// passed as an additional argument to the DacServices API. To set in a project file, add the following:  
        ///   
        /// <PropertyGroup>  
        ///     <ContributorArguments Condition="'$(Configuration)' == 'Debug'">  
        /// $(ContributorArguments);DeploymentUpdateReportContributor.GenerateUpdateReport=true;  
        ///     </ContributorArguments>  
        /// <PropertyGroup>  
        ///   
        /// </summary>  
        [ExportDeploymentPlanExecutor("MyDeploymentContributor.DeploymentUpdateReportContributor", "1.0.0.0")]  
        public class DeploymentUpdateReportContributor : DeploymentPlanExecutor  
        {  
        }  
  
    ```  
  
    Тем самым определен участник развертывания, который наследует от DeploymentPlanExecutor. В ходе сборки и развертывания специализированные участники загружаются из каталога стандартных расширений. Участники в выполнении плана развертывания обозначаются атрибутом [ExportDeploymentPlanExecutor](/dotnet/api/microsoft.sqlserver.dac.deployment.exportdeploymentplanexecutorattribute).  
  
    Этот атрибут требуется для обнаружения участников. Экран будет выглядеть примерно так:  
  
    ```csharp  
    [ExportDeploymentPlanExecutor("MyDeploymentContributor.DeploymentUpdateReportContributor", "1.0.0.0")]  
  
    ```  
  
    В данном случае первый параметр атрибута должен быть уникальным идентификатором — он будет использоваться для идентификации участника в файлах проекта. Мы рекомендуем при создании идентификатора объединить пространство имен библиотеки (MyDeploymentContributor в нашем примере) с именем класса (DeploymentUpdateReportContributor).  
  
3.  Далее добавьте следующий член, который позволит поставщику принимать параметр командной строки:  
  
    ```csharp  
    public const string GenerateUpdateReport = "DeploymentUpdateReportContributor.GenerateUpdateReport";  
    ```  
  
    Данный член позволяет пользователю указать, должен ли отчет формироваться с параметром GenerateUpdateReport.  
  
    Затем необходимо переопределить метод OnExecute для добавления кода, который должен быть выполнен при развертывании проекта базы данных.  
  
#### <a name="to-override-onexecute"></a>Переопределение метода OnExecute  
  
-   Добавьте следующий метод к применяемому классу DeploymentUpdateReportContributor:  
  
    ```csharp  
    /// <summary>  
            /// Override the OnExecute method to perform actions when you execute the deployment plan for  
            /// a database project.  
            /// </summary>  
            protected override void OnExecute(DeploymentPlanContributorContext context)  
            {  
                // determine whether the user specified a report is to be generated  
                bool generateReport = false;  
                string generateReportValue;  
                if (context.Arguments.TryGetValue(GenerateUpdateReport, out generateReportValue) == false)  
                {  
                    // couldn't find the GenerateUpdateReport argument, so do not generate  
                    generateReport = false;  
                }  
                else  
                {  
                    // GenerateUpdateReport argument was specified, try to parse the value  
                    if (bool.TryParse(generateReportValue, out generateReport))  
                    {  
                        // if we end up here, the value for the argument was not valid.  
                        // default is false, so do nothing.  
                    }  
                }  
  
                if (generateReport == false)  
                {  
                    // if user does not want to generate a report, we are done  
                    return;  
                }  
  
                // We will output to the same directory where the deployment script  
                // is output or to the current directory  
                string reportPrefix = context.Options.TargetDatabaseName;  
                string reportPath;  
                if (string.IsNullOrEmpty(context.DeploymentScriptPath))  
                {  
                    reportPath = Environment.CurrentDirectory;  
                }  
                else  
                {  
                    reportPath = Path.GetDirectoryName(context.DeploymentScriptPath);  
                }  
                FileInfo summaryReportFile = new FileInfo(Path.Combine(reportPath, reportPrefix + ".summary.xml"));  
                FileInfo detailsReportFile = new FileInfo(Path.Combine(reportPath, reportPrefix + ".details.xml"));  
  
                // Generate the reports by using the helper class DeploymentReportWriter  
                DeploymentReportWriter writer = new DeploymentReportWriter(context);  
                writer.WriteReport(summaryReportFile);  
                writer.IncludeScripts = true;  
                writer.WriteReport(detailsReportFile);  
  
                string msg = "Deployment reports ->"  
                    + Environment.NewLine + summaryReportFile.FullName  
                    + Environment.NewLine + detailsReportFile.FullName;  
  
                ExtensibilityError reportMsg = new ExtensibilityError(msg, Severity.Message);  
                base.PublishMessage(reportMsg);  
            }  
        /// <summary>  
        /// Override the OnExecute method to perform actions when you execute the deployment plan for  
        /// a database project.  
        /// </summary>  
            protected override void OnExecute(DeploymentPlanContributorContext context)  
            {  
                // determine whether the user specified a report is to be generated  
                bool generateReport = false;  
                string generateReportValue;  
                if (context.Arguments.TryGetValue(GenerateUpdateReport, out generateReportValue) == false)  
                {  
                    // couldn't find the GenerateUpdateReport argument, so do not generate  
                    generateReport = false;  
                }  
                else  
                {  
                    // GenerateUpdateReport argument was specified, try to parse the value  
                    if (bool.TryParse(generateReportValue, out generateReport))  
                    {  
                        // if we end up here, the value for the argument was not valid.  
                        // default is false, so do nothing.  
                    }  
                }  
  
                if (generateReport == false)  
                {  
                    // if user does not want to generate a report, we are done  
                    return;  
                }  
  
                // We will output to the same directory where the deployment script  
                // is output or to the current directory  
                string reportPrefix = context.Options.TargetDatabaseName;  
                string reportPath;  
                if (string.IsNullOrEmpty(context.DeploymentScriptPath))  
                {  
                    reportPath = Environment.CurrentDirectory;  
                }  
                else  
                {  
                    reportPath = Path.GetDirectoryName(context.DeploymentScriptPath);  
                }  
                FileInfo summaryReportFile = new FileInfo(Path.Combine(reportPath, reportPrefix + ".summary.xml"));  
                FileInfo detailsReportFile = new FileInfo(Path.Combine(reportPath, reportPrefix + ".details.xml"));  
  
                // Generate the reports by using the helper class DeploymentReportWriter  
                DeploymentReportWriter writer = new DeploymentReportWriter(context);  
                writer.WriteReport(summaryReportFile);  
                writer.IncludeScripts = true;  
                writer.WriteReport(detailsReportFile);  
  
                string msg = "Deployment reports ->"  
                    + Environment.NewLine + summaryReportFile.FullName  
                    + Environment.NewLine + detailsReportFile.FullName;  
  
                DataSchemaError reportMsg = new DataSchemaError(msg, ErrorSeverity.Message);  
                base.PublishMessage(reportMsg);  
            }  
    ```  
  
    Методу OnExecute передается объект [DeploymentPlanContributorContext](/dotnet/api/microsoft.sqlserver.dac.deployment.deploymentplancontributorcontext), который предоставляет доступ ко всем указанным аргументам, модели базы данных-источника и базы данных-получателя, свойствам сборки и файлам расширения. В данном примере мы получаем модель, затем вызываем вспомогательные функции, чтобы вывести сведения о модели. Мы используем вспомогательный метод PublishMessage в базовом классе для вывода всех произошедших ошибок.  
  
    Дополнительные типы и методы, представляющие интерес, включают [TSqlModel](/dotnet/api/microsoft.sqlserver.dac.model.tsqlmodel), [ModelComparisonResult](/dotnet/api/microsoft.sqlserver.dac.deployment.modelcomparisonresult), [DeploymentPlanHandle](/dotnet/api/microsoft.sqlserver.dac.deployment.deploymentplanhandle) и [SqlDeploymentOptions](/dotnet/api/microsoft.sqlserver.dac.deployment.sqldeploymentoptions).  
  
    Далее определяем вспомогательный класс, который работает с планом развертывания.  
  
#### <a name="to-add-the-helper-class-that-generates-the-report-body"></a>Добавление вспомогательного класса, формирующего текст отчета  
  
-   Добавьте вспомогательный класс и его методы из следующего кода:  
  
    ```csharp  
    /// <summary>  
            /// This class is used to generate a deployment  
            /// report.   
            /// </summary>  
            private class DeploymentReportWriter  
            {  
                readonly TSqlModel _sourceModel;  
                readonly ModelComparisonResult _diff;  
                readonly DeploymentStep _planHead;  
  
                /// <summary>  
                /// The constructor accepts the same context info  
                /// that was passed to the OnExecute method of the  
                /// deployment contributor.  
                /// </summary>  
                public DeploymentReportWriter(DeploymentPlanContributorContext context)  
                {  
                    if (context == null)  
                    {  
                        throw new ArgumentNullException("context");  
                    }  
  
                    // save the source model, source/target differences,  
                    // and the beginning of the deployment plan.  
                    _sourceModel = context.Source;  
                    _diff = context.ComparisonResult;  
                    _planHead = context.PlanHandle.Head;  
                }  
                /// <summary>  
                /// Property indicating whether script bodies  
                /// should be included in the report.  
                /// </summary>  
                public bool IncludeScripts { get; set; }  
  
                /// <summary>  
                /// Drives the report generation, opening files,   
                /// writing the beginning and ending report elements,  
                /// and calling helper methods to report on the  
                /// plan operations.  
                /// </summary>  
                internal void WriteReport(FileInfo reportFile)  
                {// Assumes that we have a valid report file  
                    if (reportFile == null)  
                    {  
                        throw new ArgumentNullException("reportFile");  
                    }  
  
                    // set up the XML writer  
                    XmlWriterSettings xmlws = new XmlWriterSettings();  
                    // Indentation makes it a bit more readable  
                    xmlws.Indent = true;  
                    FileStream fs = new FileStream(reportFile.FullName, FileMode.Create, FileAccess.Write, FileShare.ReadWrite);  
                    XmlWriter xmlw = XmlWriter.Create(fs, xmlws);  
  
                    try  
                    {  
                        xmlw.WriteStartDocument(true);  
                        xmlw.WriteStartElement("DeploymentReport");  
  
                        // Summary report of the operations that  
                        // are contained in the plan.  
                        ReportPlanOperations(xmlw);  
  
                        // You could add a method call here  
                        // to produce a detailed listing of the   
                        // differences between the source and  
                        // target model.  
                        xmlw.WriteEndElement();  
                        xmlw.WriteEndDocument();  
                        xmlw.Flush();  
                        fs.Flush();  
                    }  
                    finally  
                    {  
                        xmlw.Close();  
                        fs.Dispose();  
                    }  
                }  
  
                /// <summary>  
                /// Writes details for the various operation types  
                /// that could be contained in the deployment plan.  
                /// Optionally writes script bodies, depending on  
                /// the value of the IncludeScripts property.  
                /// </summary>  
                private void ReportPlanOperations(XmlWriter xmlw)  
                {// write the node to indicate the start  
                    // of the list of operations.  
                    xmlw.WriteStartElement("Operations");  
  
                    // Loop through the steps in the plan,  
                    // starting at the beginning.  
                    DeploymentStep currentStep = _planHead;  
                    while (currentStep != null)  
                    {  
                        // Report the type of step  
                        xmlw.WriteStartElement(currentStep.GetType().Name);  
  
                        // based on the type of step, report  
                        // the relevant information.  
                        // Note that this procedure only handles   
                        // a subset of all step types.  
                        if (currentStep is SqlRenameStep)  
                        {  
                            SqlRenameStep renameStep = (SqlRenameStep)currentStep;  
                            xmlw.WriteAttributeString("OriginalName", renameStep.OldName);  
                            xmlw.WriteAttributeString("NewName", renameStep.NewName);  
                            xmlw.WriteAttributeString("Category", GetElementCategory(renameStep.RenamedElement));  
                        }  
                        else if (currentStep is SqlMoveSchemaStep)  
                        {  
                            SqlMoveSchemaStep moveStep = (SqlMoveSchemaStep)currentStep;  
                            xmlw.WriteAttributeString("OrignalName", moveStep.PreviousName);  
                            xmlw.WriteAttributeString("NewSchema", moveStep.NewSchema);  
                            xmlw.WriteAttributeString("Category", GetElementCategory(moveStep.MovedElement));  
                        }  
                        else if (currentStep is SqlTableMigrationStep)  
                        {  
                            SqlTableMigrationStep dmStep = (SqlTableMigrationStep)currentStep;  
                            xmlw.WriteAttributeString("Name", GetElementName(dmStep.SourceTable));  
                            xmlw.WriteAttributeString("Category", GetElementCategory(dmStep.SourceElement));  
                        }  
                        else if (currentStep is CreateElementStep)  
                        {  
                            CreateElementStep createStep = (CreateElementStep)currentStep;  
                            xmlw.WriteAttributeString("Name", GetElementName(createStep.SourceElement));  
                            xmlw.WriteAttributeString("Category", GetElementCategory(createStep.SourceElement));  
                        }  
                        else if (currentStep is AlterElementStep)  
                        {  
                            AlterElementStep alterStep = (AlterElementStep)currentStep;  
                            xmlw.WriteAttributeString("Name", GetElementName(alterStep.SourceElement));  
                            xmlw.WriteAttributeString("Category", GetElementCategory(alterStep.SourceElement));  
                        }  
                        else if (currentStep is DropElementStep)  
                        {  
                            DropElementStep dropStep = (DropElementStep)currentStep;  
                            xmlw.WriteAttributeString("Name", GetElementName(dropStep.TargetElement));  
                            xmlw.WriteAttributeString("Category", GetElementCategory(dropStep.TargetElement));  
                        }  
  
                        // If the script bodies are to be included,  
                        // add them to the report.  
                        if (this.IncludeScripts)  
                        {  
                            using (StringWriter sw = new StringWriter())  
                            {  
                                currentStep.GenerateBatchScript(sw);  
                                string tsqlBody = sw.ToString();  
                                if (string.IsNullOrEmpty(tsqlBody) == false)  
                                {  
                                    xmlw.WriteCData(tsqlBody);  
                                }  
                            }  
                        }  
  
                        // close off the current step  
                        xmlw.WriteEndElement();  
                        currentStep = currentStep.Next;  
                    }  
                    xmlw.WriteEndElement();  
                }  
  
                /// <summary>  
                /// Returns the category of the specified element  
                /// in the source model  
                /// </summary>  
                private string GetElementCategory(TSqlObject element)  
                {  
                    return element.ObjectType.Name;  
                }  
  
                /// <summary>  
                /// Returns the name of the specified element  
                /// in the source model  
                /// </summary>  
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
            }        /// <summary>  
            /// This class is used to generate a deployment  
            /// report.   
            /// </summary>  
            private class DeploymentReportWriter  
            {  
                /// <summary>  
                /// The constructor accepts the same context info  
                /// that was passed to the OnExecute method of the  
                /// deployment contributor.  
                /// </summary>  
                public DeploymentReportWriter(DeploymentPlanContributorContext context)  
                {  
               }  
                /// <summary>  
                /// Property indicating whether script bodies  
                /// should be included in the report.  
                /// </summary>  
                public bool IncludeScripts { get; set; }  
  
                /// <summary>  
                /// Drives the report generation, opening files,   
                /// writing the beginning and ending report elements,  
                /// and calling helper methods to report on the  
                /// plan operations.  
                /// </summary>  
                internal void WriteReport(FileInfo reportFile)  
                {  
                }  
  
                /// <summary>  
                /// Writes details for the various operation types  
                /// that could be contained in the deployment plan.  
                /// Optionally writes script bodies, depending on  
                /// the value of the IncludeScripts property.  
                /// </summary>  
                private void ReportPlanOperations(XmlWriter xmlw)  
                {  
                }  
  
                /// <summary>  
                /// Returns the category of the specified element  
                /// in the source model  
                /// </summary>  
                private string GetElementCategory(IModelElement element)  
                {  
                }  
  
                /// <summary>  
                /// Returns the name of the specified element  
                /// in the source model  
                /// </summary>  
                private string GetElementName(IModelElement element)  
                {  
                }  
            }  
    ```  
  
-   Сохраните изменения в файле класса. Во вспомогательном классе есть обращение к нескольким полезным типам.  
  
    |**Область кода**|**Полезные типы**|  
    |-----------------|--------------------|  
    |Члены класса|[TSqlModel](/dotnet/api/microsoft.sqlserver.dac.model.tsqlmodel), [ModelComparisonResult](/dotnet/api/microsoft.sqlserver.dac.deployment.modelcomparisonresult), [DeploymentStep](/dotnet/api/microsoft.sqlserver.dac.deployment.deploymentstep)|  
    |Метод WriteReport|XmlWriter и XmlWriterSettings|  
    |Метод ReportPlanOperations|Интересующие нас типы: [DeploymentStep](/dotnet/api/microsoft.sqlserver.dac.deployment.deploymentstep), [SqlRenameStep](/dotnet/api/microsoft.sqlserver.dac.deployment.sqlrenamestep), [SqlMoveSchemaStep](/dotnet/api/microsoft.sqlserver.dac.deployment.sqlmoveschemastep), [SqlTableMigrationStep](/dotnet/api/microsoft.sqlserver.dac.deployment.sqltablemigrationstep), [CreateElementStep](/dotnet/api/microsoft.sqlserver.dac.deployment.createelementstep), [AlterElementStep](/dotnet/api/microsoft.sqlserver.dac.deployment.alterelementstep), [DropElementStep](/dotnet/api/microsoft.sqlserver.dac.deployment.dropelementstep).<br /><br />Есть и некоторые другие действия — см. полный список в документации по API.|  
    |GetElementCategory|[TSqlObject](/dotnet/api/microsoft.sqlserver.dac.model.tsqlobject)|  
    |GetElementName|[TSqlObject](/dotnet/api/microsoft.sqlserver.dac.model.tsqlobject)|  
  
    Затем необходимо выполнить сборку библиотеки классов.  
  
#### <a name="to-sign-and-build-the-assembly"></a>Подписание и построение сборки  
  
1.  В меню **Проект** выберите пункт **Свойства MyDeploymentContributor**.  
  
2.  Откройте вкладку **Подписание** .  
  
3.  Щелкните **Подписать сборку**.  
  
4.  В окне **Выберите файл ключа строгого имени** щелкните **<New>** .  
  
5.  В диалоговом окне **Создать ключ со строгим именем** в поле **Имя файла ключа**введите **MyRefKey**.  
  
6.  (Необязательно) Можно указать пароль для файла ключа для строгого имени.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  В меню **Файл** выберите команду **Сохранить все**.  
  
9. В меню **Сборка** выберите **Построить решение**.  
  
Затем необходимо установить сборку, чтобы она загружалась при сборке и развертывании проектов SQL.  
  
## <a name="install-a-deployment-contributor"></a><a name="InstallDeploymentContributor"></a>Установка участника развертывания  
Для установки участника развертывания необходимо скопировать сборку и связанный файл PDB в папку Extensions.  
  
#### <a name="to-install-the-mydeploymentcontributor-assembly"></a>Установка сборки MyDeploymentContributor  
  
-   Затем необходимо будет скопировать данные сборки в каталог Extensions. Visual Studio при запуске идентифицирует все расширения в каталоге %Program Files%\Microsoft SQL Server\110\DAC\Bin\Extensions и его подкаталогах, чтобы сделать их доступными для использования:  
  
-   Скопируйте файл сборки **MyDeploymentContributor.dll** из выходного каталога в каталог %Program Files%\Microsoft SQL Server\110\DAC\Bin\Extensions. По умолчанию путем к cкомпилированному файлу библиотеки DLL является ПутьКВашемуРешению\ПутьКВашемуПроекту\bin\Debug или ПутьКВашемуРешению\ПутьКВашемуПроекту\bin\Release.  
  
## <a name="test-your-deployment-contributor"></a><a name="TestDeploymentContributor"></a>Тестирование участника развертывания  
Для тестирования применяемого участника развертывания необходимо выполнить следующие задачи:  
  
-   Добавить свойства к файлу SQLPROJ, который должен быть развернут.  
  
-   Развернуть проект базы данных с использованием MSBuild и указать соответствующий параметр.  
  
### <a name="add-properties-to-the-sql-project-sqlproj-file"></a>Добавление свойств к файлу проекта SQL (SQLPROJ)  
Необходимо всегда обновлять файл проекта SQL для указания идентификаторов участников, которые намечены для выполнения. Также, поскольку участник ожидает аргумент GenerateUpdateReport, он должен быть указан как аргумент участника.  
  
Это можно сделать одним из двух способов. Можно изменить файл SQLPROJ вручную для добавления требуемых аргументов. Этот вариант является предпочтительным, если применяемый участник не имеет каких-либо аргументов участника, требуемых для настройки, или если вы не намереваетесь повторно использовать участника сборки в большом количестве проектов. Если выбран этот вариант, введите следующие инструкции в файл SQLPROJ после первого узла Import в файле:  
  
```  
<PropertyGroup>  
    <DeploymentContributors>$(DeploymentContributors); MyDeploymentContributor.DeploymentUpdateReportContributor</DeploymentContributors>  
<ContributorArguments Condition="'$(Configuration)' == 'Debug'">$(ContributorArguments);DeploymentUpdateReportContributor.GenerateUpdateReport=true;</ContributorArguments>  
  </PropertyGroup>  
```  
  
Второй метод предусматривает создание целевого файла, содержащего требуемые аргументы участника. Это удобно, если один и тот же участник используется в нескольких проектах и имеются требуемые аргументы участника, поскольку он включает значения по умолчанию. В этом случае создайте целевой файл в пути расширений MSBuild.  
  
1.  Перейдите в каталог %Program Files%\MSBuild.  
  
2.  Создайте папку MyContributors для сохранения своих целевых файлов.  
  
3.  Создайте в этом каталоге файл MyContributors.targets, введите в него следующий текст и сохраните файл:  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
  
    <Project xmlns="https://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
    <DeploymentContributors>$(DeploymentContributors);MyDeploymentContributor.DeploymentUpdateReportContributor</DeploymentContributors>  
    <ContributorArguments Condition="'$(Configuration)' == 'Debug'">$(ContributorArguments); DeploymentUpdateReportContributor.GenerateUpdateReport=true;</ContributorArguments>  
      </PropertyGroup>  
    </Project>  
    ```  
  
4.  В файле SQLPROJ для любого проекта, где вы хотите запустить участники, импортируйте файл целей построения, добавив следующую инструкцию в файл SQLPROJ после узла \<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.SqlTasks.targets" \/> в файле.  
  
    ```  
    <Import Project="$(MSBuildExtensionsPath)\MyContributors\MyContributors.targets " />  
    ```  
  
После реализации одного из этих подходов можно использовать MSBuild для передачи параметров для командной строки сборки.  
  
> [!NOTE]  
> Необходимо всегда обновлять свойство DeploymentContributors для указания идентификатора применяемого участника. Это тот же идентификатор, который используется в атрибуте ExportDeploymentPlanExecutor в файле исходного кода участника. Без этого требуемый участник не будет вызываться на выполнение при сборке проекта. Свойство ContributorArguments необходимо обновлять, только если для вызова участника на выполнение требуются аргументы.  
  
### <a name="deploy-the-database-project"></a>Развертывание проекта базы данных  
Как правило, проект может быть опубликован или развернут в Visual Studio. Откройте решение, содержащее проект SQL, и выберите пункт "Опубликовать…" в контекстном меню проекта или воспользуйтесь клавишей F5 для отладки развертывания в LocalDB. В этом примере для создания скрипта развертывания используется диалоговое окно "Опубликовать…".  
  
##### <a name="to-deploy-your-sql-project-and-generate-a-deployment-report"></a>Развертывание проекта SQL и создание отчета о развертывании  
  
1.  Откройте Visual Studio и вызовите решение, содержащее проект SQL.  
  
2.  Выберите свой проект и нажмите кнопку F5, чтобы выполнить отладочное развертывание. Примечание. Так как элемент ContributorArguments включается, только если задана конфигурация "Отладка", на текущий момент этот отчет формируется только для отладочных развертываний. Чтобы изменить это, уберите инструкцию Condition="'$(Configuration)' == 'Debug'" из определения ContributorArguments.  
  
3.  В окне вывода должно быть примерно следующее:  
  
    ```  
    ------ Deploy started: Project: Database1, Configuration: Debug Any CPU ------  
    Finished verifying cached model in 00:00:00  
    Deployment reports ->  
  
      C:\Users\UserName\Documents\Visual Studio 2012\Projects\MyDatabaseProject\MyDatabaseProject\sql\debug\MyTargetDatabase.summary.xml  
      C:\Users\UserName\Documents\Visual Studio 2012\Projects\MyDatabaseProject\MyDatabaseProject\sql\debug\MyTargetDatabase.details.xml  
  
      Deployment script generated to:  
      C:\Users\UserName\Documents\Visual Studio 2012\Projects\MyDatabaseProject\MyDatabaseProject\sql\debug\MyDatabaseProject.sql  
  
    ```  
  
4.  Откройте файл MyTargetDatabase.summary.xml и изучите его содержимое. В файле будет отображено новое развертывание базы данных:  
  
    ```  
    <?xml version="1.0" encoding="utf-8" standalone="yes"?>  
    <DeploymentReport>  
      <Operations>  
        <DeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <BeginPreDeploymentScriptStep />  
        <DeploymentScriptStep />  
        <EndPreDeploymentScriptStep />  
        <SqlBeginPreservationStep />  
        <SqlEndPreservationStep />  
        <SqlBeginDropsStep />  
        <SqlEndDropsStep />  
        <SqlBeginAltersStep />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales" Category="Schema" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Customer" Category="Table" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.PK_Customer_CustID" Category="Primary Key" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Orders" Category="Table" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.PK_Orders_OrderID" Category="Primary Key" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Def_Customer_YTDOrders" Category="Default Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Def_Customer_YTDSales" Category="Default Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Def_Orders_OrderDate" Category="Default Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Def_Orders_Status" Category="Default Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.FK_Orders_Customer_CustID" Category="Foreign Key" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.CK_Orders_FilledDate" Category="Check Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.CK_Orders_OrderDate" Category="Check Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspCancelOrder" Category="Procedure" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspFillOrder" Category="Procedure" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspNewCustomer" Category="Procedure" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspPlaceNewOrder" Category="Procedure" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspShowOrderDetails" Category="Procedure" />  
        <SqlEndAltersStep />  
        <DeploymentScriptStep />  
        <BeginPostDeploymentScriptStep />  
        <DeploymentScriptStep />  
        <EndPostDeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
      </Operations>  
    </DeploymentReport>  
  
    ```  
  
    > [!NOTE]  
    > При развертывании проекта базы данных, которая идентична целевой базе данных, результирующий отчет не является слишком содержательным. Для получения более содержательных результатов разверните изменения в базе данных или новую базу данных.  
  
5.  Откройте файл MyTargetDatabase.details.xml и изучите его содержимое. Небольшой раздел файла сведений содержит записи и скрипт для создания схемы Sales, вывода сообщения о создании таблицы и самого фактического создания таблицы.  
  
    ```  
    <CreateElementStep Name="Sales" Category="Schema"><![CDATA[CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
  
    ]]></CreateElementStep>  
        <SqlPrintStep><![CDATA[PRINT N'Creating [Sales].[Customer]...';  
  
    ]]></SqlPrintStep>  
        <CreateElementStep Name="Sales.Customer" Category="Table"><![CDATA[CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
  
    ]]></CreateElementStep>  
  
    ```  
  
    Анализируя план развертывания по мере его выполнения, можно отслеживать любые сведения, содержащиеся в развертывании, и выполнять дополнительные действия на основе шагов данного плана.  
  
## <a name="next-steps"></a>Next Steps  
Можно создать дополнительные средства для обработки выходных XML-файлов. Это лишь один пример применения [DeploymentPlanExecutor](/dotnet/api/microsoft.sqlserver.dac.deployment.deploymentplanexecutor). Также можно создать [DeploymentPlanModifier](/dotnet/api/microsoft.sqlserver.dac.deployment.deploymentplanmodifier), чтобы изменить план развертывания до его выполнения.  
  
## <a name="see-also"></a>См. также:  
[Пошаговое руководство. Расширение сборки проекта базы данных для формирования статистики модели](/previous-versions/visualstudio/visual-studio-2010/ee461508(v=vs.100))  
[Пошаговое руководство. Расширение процесса развертывания проекта базы данных для изменения плана развертывания](/previous-versions/visualstudio/visual-studio-2010/ee461507(v=vs.100))  
[Изменение процесса сборки и развертывания базы данных с помощью участников сборки и развертывания](/previous-versions/visualstudio/visual-studio-2010/ee461505(v=vs.100))  
