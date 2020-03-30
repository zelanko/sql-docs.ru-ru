---
title: Расширение сборки проекта базы данных для формирования статистики модели
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: d44935ce-63bf-46df-976a-5a54866c8119
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: fbbedff0adbe0302465344d437f9646bf68d997f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75242692"
---
# <a name="walkthrough-extend-database-project-build-to-generate-model-statistics"></a>Пошаговое руководство. Расширение сборки проекта базы данных для формирования статистики модели

Можно создать участников сборки для выполнения специализированных действий при сборке проекта базы данных. В ходе выполнения данного пошагового руководства будет создан участник сборки ModelStatistics, который будет выводить статистику из базы данных SQL при сборке проекта базы данных. Поскольку данный участник сборки при запуске принимает параметры, необходимо выполнить некоторые дополнительные действия.  
  
В этом пошаговом руководстве показано выполнение следующих основных задач:  
  
-   [Создание участника сборки](#CreateBuildContributor)  
  
-   [Установка участника сборки](#InstallBuildContributor)  
  
-   [Тестирование участника сборки](#TestBuildContributor)  
  
## <a name="prerequisites"></a>предварительные требования  
Для выполнения этого пошагового руководства требуются следующие компоненты:  
  
-   Необходимо установить версию Visual Studio, которая включает SQL Server Data Tools (SSDT) и поддерживает разработку VB или C#.  
  
-   Необходимо иметь проект SQL, который содержит объекты SQL.  
  
> [!NOTE]  
> Это пошаговое руководство предназначено для пользователей, уже знакомых с функциями SQL пакета SSDT. Предполагается также знакомство с основными средствами Visual Studio, такими как создание библиотеки классов и использование редактора кода для добавления кода к классу.  
  
## <a name="build-contributor-background"></a>Что такое участник сборки  
Участники сборки запускаются во время сборки проекта, после формирования модели проекта, но до сохранения проекта на диск. Они могут использоваться в нескольких случаях для различных целей, например для следующего:  
  
-   Проверка содержимого модели и возврат ошибок проверки вызывающему процессу. Это может быть сделано путем добавления ошибок в список, передаваемый в виде параметра в метод OnExecute.  
  
-   Формирование статистики модели и информирование пользователя. Это показано в данном руководстве.  
  
Главная точка входа для участников сборки — метод OnExecute. Все классы, наследующие от BuildContributor, должны реализовывать данный метод. В данный метод передается объект BuildContributorContext с данными о сборке: модель базы данных, свойства сборки, аргументы и файлы, используемые участником сборки.  
  
**TSqlModel и API модели базы данных**  
  
Самой полезной будет модель базы данных, представленная объектом TSqlModel. Это логическое отображение базы данных, включающее все таблицы, представления и другие элементы, а также связи между ними. Это строго типизированная схема, с помощью которой можно запрашивать определенные типы элементов и исследовать интересующие вас связи. В коде пошагового руководства будут показаны примеры использования этой модели:  
  
Ниже перечислены некоторые команды, используемые в примере участника сборки.  
  
|**Class**|**Метод или свойство**|**Описание**|  
|-------------|------------------------|-------------------|  
|[TSqlModel](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlmodel.aspx)|GetObjects()|Запрашивает в модели объекты и является главной точкой входа для API модели. Можно запрашивать только типы верхнего уровня, например Table или View. Такие типы, как Columns, можно находить только по мере прохождения модели. Если не указаны фильтры ModelTypeClass, то будут возвращены все типы верхнего уровня.|  
|[TSqlObject](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlobject.aspx)|GetReferencedRelationshipInstances()|Находит связи с элементом, на который ссылается текущий TSqlObject. Например, для таблицы будут возвращены объекты, представляющие столбцы Table. В данном случае можно использовать фильтр ModelRelationshipClass, чтобы указать, какие связи следует запрашивать (например, применение фильтра Table.Columns гарантирует получение только столбцов).<br /><br />Имеется целый ряд аналогичных методов, таких как GetReferencingRelationshipInstances, GetChildren и GetParent. Дополнительные сведения см. в документации к API.|  
  
**Уникальное определение участника**  
  
В ходе процесса сборки пользовательские участники загружаются из каталога стандартных расширений. Участники сборки обозначаются атрибутом [ExportBuildContributor](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.exportbuildcontributorattribute.aspx) . Этот атрибут требуется для обнаружения участников. Атрибут должен выглядеть примерно так:  
  
```  
[ExportBuildContributor("ExampleContributors.ModelStatistics", "1.0.0.0")]  
  
```  
  
В данном случае первый параметр атрибута должен быть уникальным идентификатором — он будет использоваться для идентификации участника в файлах проекта. Рекомендуется объединить пространство имен библиотеки (в данном случае ExampleContributors) с именем класса (ModelStatistics) для получения идентификатора. Далее в пошаговом руководстве будет показано, как данное пространство имен можно использовать для указания запускаемого участника.  
  
## <a name="create-a-build-contributor"></a><a name="CreateBuildContributor"></a>Создание участника сборки  
Для создания участника сборки необходимо выполнить следующие задачи:  
  
-   Создать проект библиотеки классов и добавить необходимые ссылки.  
  
-   Определите класс с именем ModelStatistics, который наследует от [BuildContributor](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.buildcontributor.aspx).  
  
-   Переопределить метод OnExecute.  
  
-   Добавьте несколько закрытых вспомогательных методов.  
  
-   Построить результирующую сборку.  
  
#### <a name="to-create-a-class-library-project"></a>Создание проекта библиотеки классов  
  
1.  Создайте проект библиотеки классов Visual C# или Visual Basic с именем MyBuildContributor.  
  
2.  Переименуйте файл Class1.cs в ModelStatistics.cs.  
  
3.  В обозревателе решений щелкните правой кнопкой мыши узел проекта, затем выберите команду **Добавить ссылку**.  
  
4.  Выберите запись **System.ComponentModel.Composition** и нажмите кнопку **ОК**.  
  
5.  Добавьте необходимые ссылки SQL. Для этого щелкните правой кнопкой мыши узел проекта и выберите **Добавить ссылку**. Нажмите кнопку **Обзор** . Перейдите в папку **C:\Program Files (x86)\Microsoft SQL Server\110\DAC\Bin** Выберите записи **Microsoft.SqlServer.Dac.dll**, **Microsoft.SqlServer.Dac.Extensions.dll**и **Microsoft.Data.Tools.Schema.Sql.dll** и нажмите кнопку **ОК**.  
  
    После этого приступайте к добавлению кода класса.  
  
#### <a name="to-define-the-modelstatistics-class"></a>Определение класса ModelStatistics  
  
1.  Класс ModelStatistics обрабатывает модель базы данных, переданную в метод OnExecute, и формирует XML-отчет, описывающий содержимое модели.  
  
    В редакторе кода обновите файл ModelStatistics.cs:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.IO;  
    using System.Linq;  
    using System.Xml.Linq;  
    using Microsoft.Data.Schema;  
    using Microsoft.Data.Schema.Build;  
    using Microsoft.Data.Schema.Extensibility;  
    using Microsoft.Data.Schema.SchemaModel;  
    using Microsoft.Data.Schema.Sql;  
  
    namespace ExampleContributors  
    {  
    /// <summary>  
        /// A BuildContributor that generates statistics about a model and saves this to the output directory.  
        /// Will only run if a "GenerateModelStatistics=true" contributor argument is set in the project file, or a targets file.   
        /// Statistics can be sorted by "none, "name" or "value", with "none" being the default sort behavior.  
        ///   
        /// To set contributor arguments in a project file, add the following:  
        ///   
        /// <PropertyGroup>  
        ///     <ContributorArguments Condition="'$(Configuration)' == 'Debug'">  
        /// $(ContributorArguments);ModelStatistics.GenerateModelStatistics=true;ModelStatistics.SortModelStatisticsBy="name";  
        ///     </ContributorArguments>  
        /// <PropertyGroup>      
        ///   
        /// This will generate model statistics when building in Debug mode only - remove the condition to generate in all build modes.  
        /// </summary>  
        [ExportBuildContributor("ExampleContributors.ModelStatistics", "1.0.0.0")]  
        public class ModelStatistics : BuildContributor  
        {  
            public const string GenerateModelStatistics = "ModelStatistics.GenerateModelStatistics";  
            public const string SortModelStatisticsBy = "ModelStatistics.SortModelStatisticsBy";  
            public const string OutDir = "ModelStatistics.OutDir";  
            public const string ModelStatisticsFilename = "ModelStatistics.xml";  
            private enum SortBy { None, Name, Value };  
            private static Dictionary<string, SortBy> SortByMap = new Dictionary<string, SortBy>(StringComparer.OrdinalIgnoreCase)  
            {  
                { "none", SortBy.None },  
                { "name", SortBy.Name },  
                { "value", SortBy.Value },  
            };  
  
            private SortBy _sortBy = SortBy.None;  
  
            /// <summary>  
            /// Override the OnExecute method to perform actions when you build a database project.  
            /// </summary>  
            protected override void OnExecute(BuildContributorContext context, IList<ExtensibilityError> errors)  
            {  
                // handle related arguments, passed in as part of  
                // the context information.  
                bool generateModelStatistics;  
                ParseArguments(context.Arguments, errors, out generateModelStatistics);  
  
                // Only generate statistics if requested to do so  
                if (generateModelStatistics)  
                {  
                    // First, output model-wide information, such  
                    // as the type of database schema provider (DSP)  
                    // and the collation.  
                    StringBuilder statisticsMsg = new StringBuilder();  
                    statisticsMsg.AppendLine(" ")  
                                 .AppendLine("Model Statistics:")  
                                 .AppendLine("===")  
                                 .AppendLine(" ");  
                    errors.Add(new ExtensibilityError(statisticsMsg.ToString(), Severity.Message));  
  
                    var model = context.Model;  
  
                    // Start building up the XML that will later  
                    // be serialized.  
                    var xRoot = new XElement("ModelStatistics");  
  
                    SummarizeModelInfo(model, xRoot, errors);  
  
                    // First, count the elements that are contained   
                    // in this model.  
                    IList<TSqlObject> elements = model.GetObjects(DacQueryScopes.UserDefined).ToList();  
                    Summarize(elements, element => element.ObjectType.Name, "UserDefinedElements", xRoot, errors);  
  
                    // Now, count the elements that are defined in  
                    // another model. Examples include built-in types,  
                    // roles, filegroups, assemblies, and any   
                    // referenced objects from another database.  
                    elements = model.GetObjects(DacQueryScopes.BuiltIn | DacQueryScopes.SameDatabase | DacQueryScopes.System).ToList();  
                    Summarize(elements, element => element.ObjectType.Name, "OtherElements", xRoot, errors);  
  
                    // Now, count the number of each type  
                    // of relationship in the model.  
                    SurveyRelationships(model, xRoot, errors);  
  
                    // Determine where the user wants to save  
                    // the serialized XML file.  
                    string outDir;  
                    if (context.Arguments.TryGetValue(OutDir, out outDir) == false)  
                    {  
                        outDir = ".";  
                    }  
                    string filePath = Path.Combine(outDir, ModelStatisticsFilename);  
                    // Save the XML file and tell the user  
                    // where it was saved.  
                    xRoot.Save(filePath);  
                    ExtensibilityError resultArg = new ExtensibilityError("Result was saved to " + filePath, Severity.Message);  
                    errors.Add(resultArg);  
                }  
            }  
  
            /// <summary>  
            /// Examine the arguments provided by the user  
            /// to determine if model statistics should be generated  
            /// and, if so, how the results should be sorted.  
            /// </summary>  
            private void ParseArguments(IDictionary<string, string> arguments, IList<ExtensibilityError> errors, out bool generateModelStatistics)  
            {  
                // By default, we don't generate model statistics  
                generateModelStatistics = false;  
  
                // see if the user provided the GenerateModelStatistics   
                // option and if so, what value was it given.  
                string valueString;  
                arguments.TryGetValue(GenerateModelStatistics, out valueString);  
                if (string.IsNullOrWhiteSpace(valueString) == false)  
                {  
                    if (bool.TryParse(valueString, out generateModelStatistics) == false)  
                    {  
                        generateModelStatistics = false;  
  
                        // The value was not valid from the end user  
                        ExtensibilityError invalidArg = new ExtensibilityError(  
                            GenerateModelStatistics + "=" + valueString + " was not valid.  It can be true or false", Severity.Error);  
                        errors.Add(invalidArg);  
                        return;  
                    }  
                }  
  
                // Only worry about sort order if the user requested  
                // that we generate model statistics.  
                if (generateModelStatistics)  
                {  
                    // see if the user provided the sort option and  
                    // if so, what value was provided.  
                    arguments.TryGetValue(SortModelStatisticsBy, out valueString);  
                    if (string.IsNullOrWhiteSpace(valueString) == false)  
                    {  
                        SortBy sortBy;  
                        if (SortByMap.TryGetValue(valueString, out sortBy))  
                        {  
                            _sortBy = sortBy;  
                        }  
                        else  
                        {  
                            // The value was not valid from the end user  
                            ExtensibilityError invalidArg = new ExtensibilityError(  
                                SortModelStatisticsBy + "=" + valueString + " was not valid.  It can be none, name, or value", Severity.Error);  
                            errors.Add(invalidArg);  
                        }  
                    }  
                }  
            }  
  
            /// <summary>  
            /// Retrieve the database schema provider for the  
            /// model and the collation of that model.  
            /// Results are output to the console and added to the XML  
            /// being constructed.  
            /// </summary>  
            private static void SummarizeModelInfo(TSqlModel model, XElement xContainer, IList<ExtensibilityError> errors)  
            {  
                // use a Dictionary to accumulate the information  
                // that will later be output.  
                var info = new Dictionary<string, string>();  
  
                // Two things of interest: the database schema  
                // provider for the model, and the language id and  
                // case sensitivity of the collation of that  
                // model  
                info.Add("Version", model.Version.ToString());  
  
                TSqlObject options = model.GetObjects(DacQueryScopes.UserDefined, DatabaseOptions.TypeClass).FirstOrDefault();  
                if (options != null)  
                {  
                    info.Add("Collation", options.GetProperty<string>(DatabaseOptions.Collation));  
                }  
  
                // Output the accumulated information and add it to   
                // the XML.  
                OutputResult("Basic model info", info, xContainer, errors);  
            }  
  
            /// <summary>  
            /// For a provided list of model elements, count the number  
            /// of elements for each class name, sorted as specified  
            /// by the user.  
            /// Results are output to the console and added to the XML  
            /// being constructed.  
            /// </summary>  
            private void Summarize<T>(IList<T> set, Func<T, string> groupValue, string category, XElement xContainer, IList<ExtensibilityError> errors)  
            { // Use a Dictionary to keep all summarized information  
                var statistics = new Dictionary<string, int>();  
  
                // For each element in the provided list,  
                // count items based on the specified grouping  
                var groups =  
                    from item in set  
                    group item by groupValue(item) into g  
                    select new { g.Key, Count = g.Count() };  
  
                // order the groups as requested by the user  
                if (this._sortBy == SortBy.Name)  
                {  
                    groups = groups.OrderBy(group => group.Key);  
                }  
                else if (this._sortBy == SortBy.Value)  
                {  
                    groups = groups.OrderBy(group => group.Count);  
                }  
  
                // build the Dictionary of accumulated statistics  
                // that will be passed along to the OutputResult method.  
                foreach (var item in groups)  
                {  
                    statistics.Add(item.Key, item.Count);  
                }  
  
                statistics.Add("subtotal", set.Count);  
                statistics.Add("total items", groups.Count());  
  
                // output the results, and build up the XML  
                OutputResult(category, statistics, xContainer, errors);  
            }  
  
            /// <summary>  
            /// Iterate over all model elements, counting the  
            /// styles and types for relationships that reference each   
            /// element  
            /// Results are output to the console and added to the XML  
            /// being constructed.  
            /// </summary>  
            private static void SurveyRelationships(TSqlModel model, XElement xContainer, IList<ExtensibilityError> errors)  
            {  
                // get a list that contains all elements in the model  
                var elements = model.GetObjects(DacQueryScopes.All);  
                // We are interested in all relationships that  
                // reference each element.  
                var entries =  
                    from element in elements  
                    from entry in element.GetReferencedRelationshipInstances(DacExternalQueryScopes.All)  
                    select entry;  
  
                // initialize our counting buckets  
                var composing = 0;  
                var hierachical = 0;  
                var peer = 0;  
  
                // process each relationship, adding to the   
                // appropriate bucket for style and type.  
                foreach (var entry in entries)  
                {  
                    switch (entry.Relationship.Type)  
                    {  
                        case RelationshipType.Composing:  
                            ++composing;  
                            break;  
                        case RelationshipType.Hierarchical:  
                            ++hierachical;  
                            break;  
                        case RelationshipType.Peer:  
                            ++peer;  
                            break;  
                        default:  
                            break;  
                    }  
                }  
  
                // build a dictionary of data to pass along  
                // to the OutputResult method.  
                var stat = new Dictionary<string, int>  
                {  
                    {"Composing", composing},  
                    {"Hierarchical", hierachical},  
                    {"Peer", peer},  
                    {"subtotal", entries.Count()}  
                };  
  
                OutputResult("Relationships", stat, xContainer, errors);  
            }  
  
            /// <summary>  
            /// Performs the actual output for this contributor,  
            /// writing the specified set of statistics, and adding any   
            /// output information to the XML being constructed.  
            /// </summary>  
            private static void OutputResult<T>(string category, Dictionary<string, T> statistics, XElement xContainer, IList<ExtensibilityError> errors)  
            {  
                var maxLen = statistics.Max(stat => stat.Key.Length) + 2;  
                var format = string.Format("{{0, {0}}}: {{1}}", maxLen);  
  
                StringBuilder resultMessage = new StringBuilder();  
                //List<ExtensibilityError> args = new List<ExtensibilityError>();  
                resultMessage.AppendLine(category);  
                resultMessage.AppendLine("-----------------");  
  
                // Remove any blank spaces from the category name  
                var xCategory = new XElement(category.Replace(" ", ""));  
                xContainer.Add(xCategory);  
  
                foreach (var item in statistics)  
                {  
                    //Console.WriteLine(format, item.Key, item.Value);  
                    var entry = string.Format(format, item.Key, item.Value);  
                    resultMessage.AppendLine(entry);  
                    // Replace any blank spaces in the element key with  
                    // underscores.  
                    xCategory.Add(new XElement(item.Key.Replace(' ', '_'), item.Value));  
                }  
                resultMessage.AppendLine(" ");  
                errors.Add(new ExtensibilityError(resultMessage.ToString(), Severity.Message));  
            }  
        }  
    }  
  
    ```  
  
    Затем необходимо выполнить сборку библиотеки классов.  
  
### <a name="to-sign-and-build-the-assembly"></a>Подписание и построение сборки  
  
1.  В меню **Проект** выберите пункт **Свойства MyBuildContributor**.  
  
2.  Откройте вкладку **Подписание** .  
  
3.  Щелкните **Подписать сборку**.  
  
4.  В окне **Выберите файл ключа строгого имени** щелкните **<New>** .  
  
5.  В диалоговом окне **Создать ключ со строгим именем** в поле **Имя файла ключа**введите **MyRefKey**.  
  
6.  (Необязательно) Можно указать пароль для файла ключа для строгого имени.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  В меню **Файл** выберите команду **Сохранить все**.  
  
9. В меню **Сборка** выберите **Построить решение**.  
  
    Затем необходимо установить сборку, чтобы она загружалась при сборке проектов SQL.  
  
## <a name="install-a-build-contributor"></a><a name="InstallBuildContributor"></a>Установка участника сборки  
Для установки участника сборки необходимо скопировать сборку и связанный файл PDB в папку Extensions.  
  
#### <a name="to-install-the-mybuildcontributor-assembly"></a>Установка сборки MyBuildContributor  
  
1.  Затем необходимо будет скопировать данные сборки в каталог Extensions. Visual Studio при запуске идентифицирует все расширения в каталоге %Program Files%\Microsoft SQL Server\110\DAC\Bin\Extensions и его подкаталогах, чтобы сделать их доступными для использования.  
  
2.  Скопируйте файл сборки **MyBuildContributor.dll** из выходного каталога в каталог %Program Files%\Microsoft SQL Server\110\DAC\Bin\Extensions.  
  
    > [!NOTE]  
    > По умолчанию путем к cкомпилированному файлу библиотеки DLL является ПутьКВашемуРешению\ПутьКВашемуПроекту\bin\Debug или ПутьКВашемуРешению\ПутьКВашемуПроекту\bin\Release.  
  
## <a name="run-or-test-your-build-contributor"></a><a name="TestBuildContributor"></a>Запуск или тестирование участника сборки  
Для выполнения или тестирования применяемого участника сборки необходимо выполнить следующие задачи:  
  
-   Добавить свойства к файлу SQLPROJ, планируемому для сборки.  
  
-   Выполнить сборку проекта базы данных с использованием MSBuild и указать соответствующие параметры.  
  
### <a name="add-properties-to-the-sql-project-sqlproj-file"></a>Добавление свойств к файлу проекта SQL (SQLPROJ)  
Необходимо всегда обновлять файл проекта SQL для указания идентификаторов участников, которые намечены для выполнения. Так как данный участник сборки принимает параметры командной строки из MSBuild, следует также изменить проект SQL, чтобы пользователи могли передавать данные параметры через MSBuild.  
  
Это можно сделать одним из двух способов.  
  
-   Можно изменить файл SQLPROJ вручную для добавления требуемых аргументов. Этим способом можно воспользоваться, если не планируется повторно использовать участник сборки вместе с большим количеством других проектов. Если выбран этот вариант, введите следующие инструкции в файл SQLPROJ после первого узла Import в файле:  
  
    ```  
    /// <PropertyGroup>  
    ///     <ContributorArguments Condition="'$(Configuration)' == 'Debug'">  
    ///         $(ContributorArguments);ModelStatistics.GenerateModelStatistics=true;ModelStatistics.SortModelStatisticsBy="name";  
    ///     </ContributorArguments>  
    /// <PropertyGroup>  
  
    ```  
  
-   Второй метод предусматривает создание целевого файла, содержащего требуемые аргументы участника. Это удобно, если один и тот же участник используется в нескольких проектах, поскольку он включает значения по умолчанию.  
  
    В этом случае создайте целевой файл в пути расширений MSBuild:  
  
    1.  Перейдите в каталог %Program Files%\MSBuild\\.  
  
    2.  Создайте папку MyContributors для сохранения своих целевых файлов.  
  
    3.  Создайте в этом каталоге файл MyContributors.targets, введите в него следующий текст и сохраните файл:  
  
        ```  
        <?xml version="1.0" encoding="utf-8"?>  
  
        <Project xmlns="https://schemas.microsoft.com/developer/msbuild/2003">  
          <PropertyGroup>  
            <BuildContributors>$(BuildContributors);ExampleContributors.ModelStatistics</BuildContributors>  
            <ContributorArguments Condition="'$(Configuration)' == 'Debug'">$(ContributorArguments);ModelStatistics.GenerateModelStatistics=true;ModelStatistics.SortModelStatisticsBy=name;</ContributorArguments>  
          </PropertyGroup>  
        </Project>  
        ```  
  
    4.  В файле SQLPROJ каждого проекта, в котором вы хотите запускать участников, импортируйте файл TARGETS, добавив следующую инструкцию в файл SQLPROJ после узла \<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.SqlTasks.targets" \/>:  
  
        ```  
        <Import Project="$(MSBuildExtensionsPath)\MyContributors\MyContributors.targets " />  
        ```  
  
После реализации одного из этих подходов можно использовать MSBuild для передачи параметров для командной строки сборки.  
  
> [!NOTE]  
> Необходимо всегда обновлять свойство BuildContributors для указания идентификатора применяемого участника. Это тот же идентификатор, что используется в атрибуте ExportBuildContributor в файле исходного кода участника. Без этого требуемый участник не будет вызываться на выполнение при сборке проекта. Свойство ContributorArguments необходимо обновлять, только если для выполнения участника требуются аргументы.  
  
### <a name="build-the-sql-project"></a>Выполните сборку проекта SQL.  
  
##### <a name="to-rebuild-your-database-project-by-using-msbuild-and-generate-statistics"></a>Повторная сборка проекта базы данных с помощью MSBuild и формирование статистики  
  
1.  В Visual Studio щелкните правой кнопкой мыши свой проект и выберите "Построить повторно". Проект будет перестроен, и откроется сформированная статистика модели, которая будет включена в вывод сборки и записана в файл ModelStatistics.xml. Заметьте, что в обозревателе решений может потребоваться перейти на вкладку "Показать все файлы", чтобы увидеть XML-файл.  
  
2.  Откройте командную строку. Для этого в меню **Пуск** щелкните **Все программы**, **Microsoft Visual Studio<Visual Studio Version>** , **Средства Visual Studio**, затем **Командная строка Visual Studio(<Visual Studio Version>)** .  
  
3.  Используя командную строку, перейдите в каталог, содержащий проект SQL.  
  
4.  В командной строке введите следующую команду:  
  
    ```  
    MSBuild /t:Rebuild MyDatabaseProject.sqlproj /p:BuildContributors=$(BuildContributors);ExampleContributors.ModelStatistics /p:ContributorArguments=$(ContributorArguments);GenerateModelStatistics=true;SortModelStatisticsBy=name;OutDir=.\;  
    ```  
  
    Замените *MyDatabaseProject* именем проекта базы данных, сборку которого необходимо выполнить. Если проект изменился с последнего момента его сборки, вместо /t:Rebuild можно использовать /t:Build.  
  
    В выходных данных можно видеть следующие сведения о сборке:  
  
```  
Model Statistics:  
===  
  
Basic model info  
-----------------  
    Version: Sql110  
  Collation: SQL_Latin1_General_CP1_CI_AS  
  
UserDefinedElements  
-----------------  
  DatabaseOptions: 1  
         subtotal: 1  
      total items: 1  
  
OtherElements  
-----------------  
                Assembly: 1  
       BuiltInServerRole: 9  
           ClrTypeMethod: 218  
  ClrTypeMethodParameter: 197  
         ClrTypeProperty: 20  
                Contract: 6  
                DataType: 34  
                Endpoint: 5  
               Filegroup: 1  
             MessageType: 14  
                   Queue: 3  
                    Role: 10  
                  Schema: 13  
                 Service: 3  
                    User: 4  
         UserDefinedType: 3  
                subtotal: 541  
             total items: 16  
  
Relationships  
-----------------  
     Composing: 477  
  Hierarchical: 6  
          Peer: 19  
      subtotal: 502  
  
```  
  
1.  Откройте файл ModelStatistics.xml и изучите его содержимое.  
  
    Полученные результаты также сохраняются в XML-файле.  
  
## <a name="next-steps"></a>Next Steps  
Можно создать дополнительные средства для обработки выходного XML-файла. Это лишь один пример применения участника сборки. Можно, например, создать участника, который в ходе сборки сформирует файл словаря данных.  
  
## <a name="see-also"></a>См. также:  
[Изменение процесса сборки и развертывания базы данных с помощью участников сборки и развертывания](../ssdt/use-deployment-contributors-to-customize-database-build-and-deployment.md)  
[Пошаговое руководство. Расширение процесса развертывания проекта базы данных для анализа плана развертывания](../ssdt/walkthrough-extend-database-project-deployment-to-analyze-the-deployment-plan.md)  
  
