---
title: Общие сведения о расширяемости для правил анализа кода базы данных | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 62f5c980-18d5-43fe-b443-c9e149d01fc7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 42896bb62b5566c955c86c43618a8f64e4968b5a
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52405871"
---
# <a name="overview-of-extensibility-for-database-code-analysis-rules"></a>Общие сведения о расширяемости для правил анализа кода базы данных
Выпуски Visual Studio, содержащие SQL Server Data Tools, включают правила анализа кода, возвращающие предупреждения о проектировании, именовании и производительности Transact\-SQL в отношении кода базы данных. Дополнительные сведения см. в статье [Analyzing Database Code to Improve Code Quality](https://msdn.microsoft.com/library/dd172133(v=vs.100).aspx) (Анализ кода базы данных для улучшения качества кода).  
  
Если встроенные правила анализа кода не охватывают конкретную проблему Transact\-SQL, которую вы хотите учесть, можно создать настраиваемые правила анализа кода базы данных. Например, вы можете создать настраиваемое правило, позволяющее избежать оператора WAITFORDELAY, как показано в [пошаговом руководстве по созданию сборки настраиваемого правила анализа статического кода для SQL Server](../ssdt/walkthrough-author-custom-static-code-analysis-rule-assembly.md). Для создания настраиваемых правил анализа кода базы данных используются классы в пространстве имен [CodeAnalysis](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.codeanalysis.aspx).  
  
Прежде чем создавать настраиваемые правила анализа кода, необходимо понять базовую архитектуру различных компонентов правил анализа кода базы данных.  
  
## <a name="database-code-analysis-rules-components"></a>Компоненты правил анализа кода базы данных  
На следующей схеме показано, как взаимодействуют компоненты правил анализа кода базы данных.  
  
![Компоненты правил для анализа кода базы данных](../ssdt/media/ssdt-database-code-analysis-rules-components.jpg "Database Code Analysis Rules Components")  
  
Когда вы используете компонент правил анализа кода базы данных, выполняя анализ статического кода напрямую (дополнительные сведения см. в статье [Практическое руководство. Анализ кода Transact-SQL для поиска дефектов](https://msdn.microsoft.com/library/dd172119(v=vs.100).aspx)), или выполняя сборку, правила загружаются и используются в соответствии с их настройкой в вашем проекте. Дополнительные сведения см. в статье [How to: Enable and Disable Specific Rules for Static Analysis of Database Code](https://msdn.microsoft.com/library/dd172131(v=vs.100).aspx) (Практическое руководство. Включение и отключение определенных правил для статического анализа кода базы данных). Диспетчер расширений также будет загружать все сборки настраиваемых правил, которые вы создали и зарегистрировали. Дополнительные сведения см. в статье [Практическое руководство. Установка расширений компонентов и управление ими](../ssdt/how-to-install-and-manage-feature-extensions.md).  
  
Класс для настраиваемого правила анализа кода наследуется от [SqlCodeAnalysisRule](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.codeanalysis.sqlcodeanalysisrule.aspx). Класс настраиваемых правил может обращаться к ряду полезных объектов через свой контекст выполнения правил. К ним относятся следующие объекты.  
  
-   Метаданные о самом правиле.  
  
-   Модель Dac.Model.TSqlModel, представляющая схему базы данных, включая все элементы модели, связи между ними и все свойства элементов.  
  
-   Для правил, которые анализируют конкретные элементы, в контекст включается объект Dac.Model.TSqlObject, представляющий этот элемент схемы в модели.  
  
-   Многие объекты схемы также имеют представление [ScriptDom](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.aspx), доступ к которому можно получить через этот контекст. Это основанное на AST представление элемента, который может быть полезен при просмотре потенциальных проблем синтаксиса, таких как наличие [SelectStarExpression](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.selectstarexpression.aspx).  
  
Правило создает объект Dac.CodeAnalysis.SqlRuleProblem для представления всех обнаруженных проблем. При его создании соответствующий объект Dac.Model.TSqlObject и, возможно, элемент представления [ScriptDom](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.aspx) передаются в конструктор, а затем используются для определения источника проблемы в файлах исходного кода. В конце анализа все эти проблемы передаются в диспетчер ошибок и отображаются в списке ошибок.  
  
## <a name="see-also"></a>См. также:  
[Расширение функций баз данных](../ssdt/extending-the-database-features.md)  
  
