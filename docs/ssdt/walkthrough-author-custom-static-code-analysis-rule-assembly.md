---
title: Разработка сборки пользовательского правила анализа статического кода для SQL Server
description: Узнайте, как создавать правила анализа кода SQL Server. Настройте правило, чтобы избегать инструкций WAITFOR DELAY в хранимых процедурах, триггерах и функциях.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: f7b6ed8c-a4e0-4e33-9858-a8aa40aef309
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 31d183a212ea18f681724d06834041b0a50f752c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896240"
---
# <a name="walkthrough-authoring-a-custom-static-code-analysis-rule-assembly-for-sql-server"></a>Пошаговое руководство по созданию сборки настраиваемого правила анализа статического кода для SQL Server

В этом пошаговом руководстве демонстрируются этапы создания правила анализа кода SQL Server. Правило, создаваемое в этом пошаговом руководстве, используется для предотвращения инструкций WAITFOR DELAY в хранимых процедурах, триггерах и функциях.  
  
В рамках этого пошагового руководства вы создадите настраиваемое правило для анализа статического кода Transact\-SQL с использованием следующих процессов:  
  
1. Создание библиотеки классов, включение подписи для этого проекта и добавление необходимых ссылок.  
  
2. Создание класса настраиваемого правила Visual C\#.  
  
3. Создание двух вспомогательных классов Visual C\#.  
  
4. Копирование созданного DLL-файла в каталог Extensions для установки.  
  
5. Проверка создания нового правила анализа кода.  
  
**Предварительные требования**
  
Для выполнения этого пошагового руководства требуются следующие компоненты:  
  
- Вам потребуется установленная версия Visual Studio, которая включает SQL Server Data Tools и поддерживает разработку на Visual C\# или Visual Basic.  
  
- Также нужен проект SQL Server, который содержит объекты SQL Server.  
  
- Экземпляр SQL Server, на котором можно развернуть проект базы данных.  
  
> [!NOTE]  
> Это пошаговое руководство предназначено для пользователей, уже знакомых с функциями SQL Server пакета SQL Server Data Tools. Предполагается также знакомство с основными концепциями Visual Studio, такими как создание библиотеки классов и использование редактора кода для добавления кода в класс.  
  
## <a name="creating-a-custom-code-analysis-rule-for-sql-server"></a>Создание настраиваемого правила анализа кода для SQL Server  

Сначала создайте библиотеку классов. Создание проекта библиотеки классов  
  
1. Создайте проект библиотеки классов Visual C\# или Visual Basic с именем SampleRules.  
  
2. Переименуйте файл Class1.cs в AvoidWaitForDelayRule.cs.  
  
3. В обозревателе решений щелкните правой кнопкой мыши узел проекта, затем выберите команду **Добавить ссылку**.  
  
4. Выберите System.ComponentModel.Composition на вкладке «Платформы».  
  
5. Щелкните **Обзор**, перейдите к каталогу C:\Program Files (x86)\\Microsoft SQL Server\120\SDK\Assemblies, выберите файл Microsoft.SqlServer.TransactSql.ScriptDom.dll и нажмите кнопку "ОК".  
  
6. Затем установите необходимые ссылки DACFx. Щелкните **Обзор** и перейдите к каталогу <Visual Studio Install Dir>\Common7\IDE\Extensions\\Microsoft\SQLDB\DAC\120. Выберите записи Microsoft.SqlServer.Dac.dll, Microsoft.SqlServer.Dac.Extensions.dll и Microsoft.Data.Tools.Schema.Sql.dll, щелкните **Добавить** и нажмите кнопку **ОК**.  
  
    Двоичные файлы DACFx устанавливаются в каталог установки Visual Studio. В Visual Studio 2012 для <Visual Studio Install Dir> обычно используется папка C:\Program Files (x86)\\MicrosoftVisual Studio 11.0. В Visual Studio 2013 это обычно будет папка C:\Program Files (x86)\\MicrosoftVisual Studio 12.0.  
  
Далее вы добавите вспомогательные классы, которые будут использоваться этим правилом.  
  
## <a name="creating-the-custom-code-analysis-rule-supporting-classes"></a>Создание вспомогательных классов настраиваемого правила анализа

Перед созданием класса для самого правила в проект будут добавлены класс посетителей и класс атрибутов. Эти классы могут использоваться для создания дополнительных настраиваемых правил.  
  
Сначала необходимо определить класс WaitForDelayVisitor, производный от [TSqlConcreteFragmentVisitor](https://docs.microsoft.com/dotnet/api/microsoft.sqlserver.transactsql.scriptdom.tsqlconcretefragmentvisitor). Этот класс предоставляет доступ к инструкциям WAITFOR DELAY в модели. Классы посетителей используют API-интерфейсы [ScriptDom](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.aspx), предоставленные SQL Server. В этом API код Transact\-SQL представлен в виде дерева абстрактного синтаксиса (AST), поэтому классы посетителей удобны для поиска особых объектов синтаксиса, таких как инструкции WAITFORDELAY. Их может быть трудно найти с помощью объектной модели, так как они не связаны с каким-либо специальным свойством или отношением объекта, но их легко найти, используя шаблон посетителя и API [ScriptDom](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.aspx).  
  
### <a name="defining-the-waitfordelayvisitor-class"></a>Определение класса WaitForDelayVisitor  
  
1. В **обозревателе решений** выберите проект SampleRules.  
  
2. В меню **Проект** выберите команду **Добавить класс**. Откроется диалоговое окно **Добавление нового элемента**.  
  
3. В текстовом поле **Имя** введите WaitForDelayVisitor.cs и нажмите кнопку **Добавить**. Файл WaitForDelayVisitor.cs добавляется в проект в **Обозревателе решений**.  
  
4. Откройте файл WaitForDelayVisitor.cs и обновите его содержимое, чтобы оно соответствовало следующему коду:  
  
    ```  
    using System.Collections.Generic;  
    using Microsoft.SqlServer.TransactSql.ScriptDom;  
    namespace SampleRules {  
        class WaitForDelayVistor {}  
    }  
    ```  
  
5. В объявлении класса замените модификатор доступа на внутренний и задайте этот класс, как производный от класса TSqlConcreteFragmentVisitor:  
  
    ```  
    internal class WaitForDelayVisitor : TSqlConcreteFragmentVisitor {}  
    ```  
  
6. Добавьте следующий код для определения переменной элемента списка.  
  
    ```  
    public IList<WaitForStatement> WaitForDelayStatements { get; private set; }  
    ```  
  
7. Задайте конструктор класса, добавив следующий код:  
  
    ```  
    public WaitForDelayVisitor() {  
       WaitForDelayStatments = new List<WaitForStatement>();  
    }  
    ```  
  
8. Переопределите метод ExplicitVisit, добавив следующий код:  
  
    ```  
    public override void ExplicitVisit(WaitForStatement node) {  
       // We are only interested in WAITFOR DELAY occurrences  
       if (node.WaitForOption == WaitForOption.Delay)  
          WaitForDelayStatments.Add(node);  
    }  
    ```  
  
    Этот метод считывает инструкции WAITFOR в модели и добавляет те, которые имеют параметр DELAY, в список инструкций WAITFOR DELAY. Здесь указана ссылка на ключевой класс [WaitForStatement](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.waitforstatement.aspx).  
  
9. В меню **Файл** выберите пункт **Сохранить**.  
  
Второй класс — LocalizedExportCodeAnalysisRuleAttribute.cs. Это расширение встроенного класса Microsoft.SqlServer.Dac.CodeAnalysis.ExportCodeAnalysisRuleAttribute, предоставляемого платформой. Он поддерживает чтение отображаемого имени DisplayName и описания Description, используемых правилом, из файла ресурсов. Этот класс особенно полезен, если вы планируете использование ваших правил на нескольких языках.  
  
### <a name="defining-the-localizedexportcodeanalysisruleattribute-class"></a>Определение класса LocalizedExportCodeAnalysisRuleAttribute  
  
1. В **обозревателе решений** выберите проект SampleRules.  
  
2. В меню **Проект** выберите команду **Добавить класс**. Откроется диалоговое окно **Добавление нового элемента**.  
  
3. В текстовом поле **Имя** введите LocalizedExportCodeAnalysisRuleAttribute.cs и нажмите кнопку **Добавить**. Файл будет добавлен в проект в **Обозревателе решений**.  
  
4. Откройте файл и обновите его содержимое, чтобы оно соответствовало следующему коду.  
  
    ```  
    using Microsoft.SqlServer.Dac.CodeAnalysis;  
    using System;  
    using System.Globalization;  
    using System.Reflection;  
    using System.Resources;  
  
    namespace SampleRules  
    {  
  
        internal class LocalizedExportCodeAnalysisRuleAttribute : ExportCodeAnalysisRuleAttribute  
        {  
            private readonly string _resourceBaseName;  
            private readonly string _displayNameResourceId;  
            private readonly string _descriptionResourceId;  
  
            private ResourceManager _resourceManager;  
            private string _displayName;  
            private string _descriptionValue;  
  
            /// <summary>  
            /// Creates the attribute, with the specified rule ID, the fully qualified  
            /// name of the resource file that will be used for looking up display name  
            /// and description, and the Ids of those resources inside the resource file.  
            /// </summary>  
            public LocalizedExportCodeAnalysisRuleAttribute(  
                string id,  
                string resourceBaseName,  
                string displayNameResourceId,  
                string descriptionResourceId)  
                : base(id, null)  
            {  
                _resourceBaseName = resourceBaseName;  
                _displayNameResourceId = displayNameResourceId;  
                _descriptionResourceId = descriptionResourceId;  
            }  
  
            /// <summary>  
            /// Rules in a different assembly would need to overwrite this  
            /// </summary>  
            /// <returns></returns>  
            protected virtual Assembly GetAssembly()  
            {  
                return GetType().Assembly;  
            }  
  
            private void EnsureResourceManagerInitialized()  
            {  
                var resourceAssembly = GetAssembly();  
  
                try  
                {  
                    _resourceManager = new ResourceManager(_resourceBaseName, resourceAssembly);  
                }  
                catch (Exception ex)  
                {  
                    var msg = String.Format(CultureInfo.CurrentCulture, RuleResources.CannotCreateResourceManager, _resourceBaseName, resourceAssembly);  
                    throw new RuleException(msg, ex);  
                }  
            }  
  
            private string GetResourceString(string resourceId)  
            {  
                EnsureResourceManagerInitialized();  
                return _resourceManager.GetString(resourceId, CultureInfo.CurrentUICulture);  
            }  
  
            /// <summary>  
            /// Overrides the standard DisplayName and looks up its value inside a resources file  
            /// </summary>  
            public override string DisplayName  
            {  
                get  
                {  
                    if (_displayName == null)  
                    {  
                        _displayName = GetResourceString(_displayNameResourceId);  
                    }  
                    return _displayName;  
                }  
            }  
  
            /// <summary>  
            /// Overrides the standard Description and looks up its value inside a resources file  
            /// </summary>  
            public override string Description  
            {  
                get  
                {  
                    if (_descriptionValue == null)  
                    {   
                        _descriptionValue = GetResourceString(_descriptionResourceId);  
                    }  
                    return _descriptionValue;  
                }  
            }  
        }  
    }  
    ```  
  
Затем добавьте файл ресурсов, который будет определять имя правила, описание правила и категорию, в которой будет отображаться это правило в интерфейсе конфигурации правил.  
  
### <a name="to-add-a-resource-file-and-three-resource-strings"></a>Добавление файла ресурсов и трех строк ресурса  
  
1. В **обозревателе решений** выберите проект SampleRules.  
  
2. В меню **Проект** выберите команду **Добавить новый элемент**. Откроется диалоговое окно **Добавление нового элемента**.  
  
3. В списке **Установленные шаблоны**, щелкните **Общие**.  
  
4. В области сведений щелкните **Файл ресурсов**.  
  
5. В поле **Имя** введите RuleResources.resx. Откроется редактор ресурсов без каких-либо заданных ресурсов.  
  
6. Задайте четыре строки ресурса следующим образом:  
  
    |Имя|Значение|  
    |--------|---------|  
    |AvoidWaitForDelay_ProblemDescription|Инструкция WAITFORDELAY обнаружена в {0}.|  
    |AvoidWaitForDelay_RuleName|Избегайте использования инструкций WaitFor Delay в хранимых процедурах, функциях и триггерах.|  
    |CategorySamples|SamplesCategory|  
    |CannotCreateResourceManager|Не удается создать диспетчер ресурсов для {0} из {1}.|  
  
7. В меню **Файл** выберите пункт **RuleResources.resx**.  
  
Затем определите класс, который ссылается на ресурсы в файле ресурсов, используемые Visual Studio для отображения сведений о правиле в пользовательском интерфейсе.  
  
### <a name="defining-the-sampleconstants-class"></a>Определение класса SampleConstants  
  
1. В **обозревателе решений** выберите проект SampleRules.  
  
2. В меню **Проект** выберите команду **Добавить класс**. Откроется диалоговое окно **Добавление нового элемента**.  
  
3. В текстовом поле **Имя** введите SampleRuleConstants.cs и нажмите кнопку **Добавить**. Файл SampleRuleConstants.cs будет добавлен в проект в **Обозревателе решений**.  
  
4. Откройте файл SampleRuleConstants.cs и добавьте в него следующие инструкции Using.  
  
    ```  
    namespace SampleRules  
    {   
        internal static class RuleConstants  
        {  
            /// <summary>  
            /// The name of the resources file to use when looking up rule resources  
            /// </summary>  
            public const string ResourceBaseName = "Public.Dac.Samples.Rules.RuleResources";  
  
            /// <summary>  
            /// Lookup name inside the resources file for the select asterisk rule name  
            /// </summary>  
            public const string AvoidWaitForDelay_RuleName = "AvoidWaitForDelay_RuleName";  
            /// <summary>  
            /// Lookup ID inside the resources file for the select asterisk description  
            /// </summary>  
            public const string AvoidWaitForDelay_ProblemDescription = "AvoidWaitForDelay_ProblemDescription";  
  
            /// <summary>  
            /// The design category (should not be localized)  
            /// </summary>  
            public const string CategoryDesign = "Design";  
  
            /// <summary>  
            /// The performance category (should not be localized)  
            /// </summary>  
            public const string CategoryPerformance = "Design";  
        }  
    }  
    ```  
  
5. Щелкните пункты **Файл** > **Сохранить**.  
  
## <a name="creating-the-custom-code-analysis-rule-class"></a>Создание класса настраиваемого правила анализа кода

Теперь, когда добавлены вспомогательные классы, которые будут использоваться настраиваемым правилом анализа кода, необходимо создать класс настраиваемого правила с именем AvoidWaitForDelayRule. Настраиваемое правило AvoidWaitForDelayRule будет помогать разработчикам баз данных избежать использования инструкций WAITFOR DELAY в хранимых процедурах, триггерах и функциях.  
  
### <a name="creating-the-avoidwaitfordelayrule-class"></a>Создание класса AvoidWaitForDelayRule  
  
1. В **обозревателе решений** выберите проект SampleRules.  
  
2. В меню **Проект** выберите команду **Добавить класс**. Откроется диалоговое окно **Добавление нового элемента**.  
  
3. В текстовом поле **Имя** введите AvoidWaitForDelayRule.cs и нажмите кнопку **Добавить**. Файл AvoidWaitForDelayRule.cs будет добавлен в проект в **Обозревателе решений**.  
  
4. Откройте файл AvoidWaitForDelayRule.cs и добавьте в него следующие инструкции Using.  
  
    ```  
    using Microsoft.SqlServer.Dac.CodeAnalysis;  
    using Microsoft.SqlServer.Dac.Model;  
    using Microsoft.SqlServer.TransactSql.ScriptDom;  
    using System;  
    using System.Collections.Generic;  
    using System.Globalization;   
    namespace SampleRules {  
        class AvoidWaitForDelayRule {}  
    }  
    ```  
  
5. В объявлении класса AvoidWaitForDelayRule измените модификатор доступа на public:  
  
    ```  
    /// <summary>  
    /// This is a rule that returns a warning message   
    /// whenever there is a WAITFOR DELAY statement appears inside a subroutine body.  
    /// This rule only applies to stored procedures, functions and triggers.  
    /// </summary>  
    public sealed class AvoidWaitForDelayRule  
    ```  
  
6. Создайте класс AvoidWaitForDelayRule как производный от базового класса Microsoft.SqlServer.Dac.CodeAnalysis.SqlCodeAnalysisRule.  
  
    ```  
    public sealed class AvoidWaitForDelayRule : SqlCodeAnalysisRule  
    ```  
  
7. Добавьте в свой класс атрибут LocalizedExportCodeAnalysisRuleAttribute.  
  
    LocalizedExportCodeAnalysisRuleAttribute позволяет службе анализа кода обнаруживать настраиваемые правила анализа кода. При анализе кода можно использовать только классы, помеченные атрибутом ExportCodeAnalysisRuleAttribute (или атрибутом, наследуемым от этого атрибута).  
  
    Атрибут LocalizedExportCodeAnalysisRuleAttribute предоставляет некоторые необходимые метаданные, используемые этой службой. Такие метаданные включают уникальный идентификатор для этого правила, имя, отображаемое в пользовательском интерфейсе Visual Studio, и описание, которое может использоваться правилом при выявлении проблем.  
  
    ```  
    [LocalizedExportCodeAnalysisRule(AvoidWaitForDelayRule.RuleId,  
        RuleConstants.ResourceBaseName,  
        RuleConstants.AvoidWaitForDelay_RuleName,   
        RuleConstants.AvoidWaitForDelay_ProblemDescription  
        Category = RuleConstants.CategoryPerformance,   
        RuleScope = SqlRuleScope.Element)]   
    public sealed class AvoidWaitForDelayRule : SqlCodeAnalysisRule  
    {  
       /// <summary>  
       /// The Rule ID should resemble a fully-qualified class name. In the Visual Studio UI  
       /// rules are grouped by "Namespace + Category", and each rule is shown using "Short ID: DisplayName".  
       /// For this rule, that means the grouping will be "Public.Dac.Samples.Performance", with the rule  
       /// shown as "SR1004: Avoid using WaitFor Delay statements in stored procedures, functions and triggers."  
       /// </summary>  
       public const string RuleId = "RuleSamples.SR1004";  
    }  
    ```  
  
    Свойство RuleScope должно иметь значение Microsoft.SqlServer.Dac.CodeAnalysis.SqlRuleScope.Element, так как это правило будет анализировать определенные элементы. Правило будет вызываться по одному разу для каждого соответствующего элемента в модели. Если вы хотите анализировать всю модель, вместо этого значения можно использовать значение Microsoft.SqlServer.Dac.CodeAnalysis.SqlRuleScope.Model.  
  
8. Добавьте конструктор, который устанавливает Microsoft.SqlServer.Dac.CodeAnalysis.SqlAnalysisRule.SupportedElementTypes. Это необходимо для правила области элемента. Этот объект определяет типы элементов, к которым будет применяться это правило. В данном случае правило будет применяться в хранимых процедурах, триггерах и функциях. Обратите внимание, что класс Microsoft.SqlServer.Dac.Model.ModelSchema перечисляет все доступные типы элементов, которые могут быть проанализированы.  
  
    ```  
    public AvoidWaitForDelayRule()  
    {  
       // This rule supports Procedures, Functions and Triggers. Only those objects will be passed to the Analyze method  
       SupportedElementTypes = new[]  
       {  
          // Note: can use the ModelSchema definitions, or access the TypeClass for any of these types  
          ModelSchema.ExtendedProcedure,  
          ModelSchema.Procedure,  
          ModelSchema.TableValuedFunction,  
          ModelSchema.ScalarFunction,  
  
          ModelSchema.DatabaseDdlTrigger,  
          ModelSchema.DmlTrigger,  
          ModelSchema.ServerDdlTrigger  
       };  
    }  
    ```  
  
9. Добавьте переопределение для метода Microsoft.SqlServer.Dac.CodeAnalysis.SqlAnalysisRule.Analyze(Microsoft.SqlServer.Dac.CodeAnalysis.SqlRuleExecutionContext), которое использует Microsoft.SqlServer.Dac.CodeAnalysis.SqlRuleExecutionContext в качестве входных параметров. Этот метод возвращает список потенциальных проблем.  
  
    Метод получает Microsoft.SqlServer.Dac.Model.TSqlModel, Microsoft.SqlServer.Dac.Model.TSqlObject и [TSqlFragment](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.tsqlfragment.aspx) из параметра контекста. Затем используется класс WaitForDelayVisitor для получения списка всех инструкций WAITFOR DELAY в модели.  
  
    Для каждого [WaitForStatement](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.waitforstatement.aspx) в этом списке создается Microsoft.SqlServer.Dac.CodeAnalysis.SqlRuleProblem.  
  
    ```  
    /// <summary>  
    /// For element-scoped rules the Analyze method is executed once for every matching   
    /// object in the model.   
    /// </summary>  
    /// <param name="ruleExecutionContext">The context object contains the TSqlObject being   
    /// analyzed, a TSqlFragment  
    /// that's the AST representation of the object, the current rule's descriptor, and a   
    /// reference to the model being  
    /// analyzed.  
    /// </param>  
    /// <returns>A list of problems should be returned. These will be displayed in the Visual   
    /// Studio error list</returns>  
    public override IList<SqlRuleProblem> Analyze(  
        SqlRuleExecutionContext ruleExecutionContext)  
    {  
         IList<SqlRuleProblem> problems = new List<SqlRuleProblem>();  
  
         TSqlObject modelElement = ruleExecutionContext.ModelElement;  
  
         // this rule does not apply to inline table-valued function  
         // we simply do not return any problem in that case.  
         if (IsInlineTableValuedFunction(modelElement))  
         {  
             return problems;  
         }  
  
         string elementName = GetElementName(ruleExecutionContext, modelElement);  
  
         // The rule execution context has all the objects we'll need, including the   
         // fragment representing the object,  
         // and a descriptor that lets us access rule metadata  
         TSqlFragment fragment = ruleExecutionContext.ScriptFragment;  
         RuleDescriptor ruleDescriptor = ruleExecutionContext.RuleDescriptor;  
  
         // To process the fragment and identify WAITFOR DELAY statements we will use a   
         // visitor   
         WaitForDelayVisitor visitor = new WaitForDelayVisitor();  
         fragment.Accept(visitor);  
         IList<WaitForStatement> waitforDelayStatements = visitor.WaitForDelayStatements;  
  
         // Create problems for each WAITFOR DELAY statement found   
         // When creating a rule problem, always include the TSqlObject being analyzed. This   
         // is used to determine  
         // the name of the source this problem was found in and a best guess as to the   
         // line/column the problem was found at.  
         //  
         // In addition if you have a specific TSqlFragment that is related to the problem   
         //also include this  
         // since the most accurate source position information (start line and column) will   
         // be read from the fragment  
         foreach (WaitForStatement waitForStatement in waitforDelayStatements)  
         {  
            SqlRuleProblem problem = new SqlRuleProblem(  
                String.Format(CultureInfo.CurrentCulture,   
                    ruleDescriptor.DisplayDescription, elementName),  
                modelElement,  
                waitForStatement);  
            problems.Add(problem);  
        }  
        return problems;  
    }  
  
    private static string GetElementName(  
        SqlRuleExecutionContext ruleExecutionContext,   
        TSqlObject modelElement)  
    {  
        // Get the element name using the built in DisplayServices. This provides a number of   
        // useful formatting options to  
        // make a name user-readable  
        var displayServices = ruleExecutionContext.SchemaModel.DisplayServices;  
        string elementName = displayServices.GetElementName(  
            modelElement, ElementNameStyle.EscapedFullyQualifiedName);  
        return elementName;  
    }  
  
    private static bool IsInlineTableValuedFunction(TSqlObject modelElement)  
    {  
        return TableValuedFunction.TypeClass.Equals(modelElement.ObjectType)  
                       && FunctionType.InlineTableValuedFunction ==   
            modelElement.GetMetadata<FunctionType>(TableValuedFunction.FunctionType);  
    }  
    ```  
  
10. Щелкните пункты **Файл** > **Сохранить**.  
  
### <a name="building-the-class-library"></a>Создание библиотеки классов  
  
1. В меню **Проект** щелкните **Свойства SampleRules**.  
  
2. Откройте вкладку **Подписание** .  
  
3. Щелкните **Подписать сборку**.  
  
4. В окне **Выберите файл ключа строгого имени** щелкните **<New>** .  
  
5. В диалоговом окне **Создание ключа строгого имени** в поле **Имя файла ключей** введите MyRefKey.  
  
6. (Необязательно) Можно указать пароль для файла ключа для строгого имени.  
  
7. Нажмите кнопку **ОК**.  
  
8. В меню **Файл** выберите команду **Сохранить все**.  
  
9. В меню **Сборка** выберите **Построить решение**.  
  
Затем необходимо установить сборку, чтобы она загружалась при создании и развертывании проектов SQL Server.  
  
## <a name="install-a-static-code-analysis-rule"></a>Установка правила анализа статического кода

Для установки правила необходимо скопировать сборку и связанный PDB-файл в папку Extensions.  
  
### <a name="to-install-the-samplerules-assembly"></a>Установка сборки SampleRules

Затем необходимо будет скопировать данные сборки в каталог Extensions. Visual Studio при запуске идентифицирует все расширения в каталоге <Visual Studio Install Dir>\Common7\IDE\Extensions\\Microsoft\SQLDB\DAC\120\Extensions и его подкаталогах, чтобы сделать их доступными для использования.  
  
В Visual Studio 2012 для <Visual Studio Install Dir> обычно используется папка C:\Program Files (x86)\\MicrosoftVisual Studio 11.0. В Visual Studio 2013 это обычно будет папка C:\Program Files (x86)\\MicrosoftVisual Studio 12.0.  
  
Скопируйте файл сборки SampleRules.dll из выходного каталога в каталог <Visual Studio Install Dir>\Common7\IDE\Extensions\\Microsoft\SQLDB\DAC\120\Extensions. По умолчанию путем к cкомпилированному файлу библиотеки DLL является ПутьКВашемуРешению\ПутьКВашемуПроекту\bin\Debug или ПутьКВашемуРешению\ПутьКВашемуПроекту\bin\Release.  
  
Теперь ваше правило должно быть установлено и появится после перезапуска Visual Studio. Затем запустите новый сеанс Visual Studio и создайте проект базы данных.  
  
### <a name="starting-a-new-visual-studio-session-and-creating-a-database-project"></a>Запуск нового сеанса Visual Studio и создание проекта базы данных  
  
1. Запустите второй сеанс работы Visual Studio.  
  
2. Последовательно выберите пункты **Файл** > **Создать** > **Проект**.  
  
3. В диалоговом окне **Создание проекта** в списке **Установленные шаблоны** разверните узел **SQL Server**, а затем выберите узел **Проект базы данных SQL Server**.  
  
4. В текстовом поле **Имя** введите SampleRulesDB и нажмите кнопку **ОK**.  
  
Теперь вы увидите, что новое правило отображается в проекте SQL Server. Чтобы просмотреть новое правило анализа кода AvoidWaitForRule, выполните следующие действия.  
  
1. В **Обозревателе решений** выберите проект SampleRulesDB.  
  
2. В меню **Проект** выберите **Свойства**. Откроется страница свойств SampleRulesDB.  
  
3. Щелкните **Анализ кода**. Вы увидите новую категорию с именем RuleSamples.CategorySamples.  
  
4. Разверните категорию RuleSamples. CategorySamples. Вы должны увидеть следующее: SR1004: Avoid WAITFOR DELAY statement in stored procedures, triggers, and functions (избегать инструкции WAITFOR DELAY в хранимых процедурах, триггерах и функциях).  
  
## <a name="see-also"></a>См. также:

[Общие сведения о расширяемости для правил анализа кода базы данных](../ssdt/overview-of-extensibility-for-database-code-analysis-rules.md)