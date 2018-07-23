---
title: Практическое руководство. Обновление пользовательского условия теста Visual Studio 2010 с предыдущего выпуска до SQL Server Data Tools | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44c895a3-dee0-4032-a60f-812f5fe3c713
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1104d58abf423ff5e6f8c0f88029933c8cb606f6
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094863"
---
# <a name="how-to-upgrade-a-visual-studio-2010-custom-test-condition-from-a-previous-release-to-sql-server-data-tools"></a>Практическое руководство. Обновление нестандартного условия теста Visual Studio 2010 с предыдущего выпуска до SQL Server Data Tools
Чтобы использовать условие модульного теста, созданное в версии до SQL Server Data Tools, его необходимо обновить.  
  
-   [Обновление ссылок](#UpdateReferences)  
  
-   [Обновление атрибутов классов и ссылок на типы](#UpdateClassAttributesandTypeReference)  
  
-   [Установка обновленного условия теста](#ApplytheNewRegistrationProcess)  
  
## <a name="UpdateReferences"></a>Обновление ссылок  
Обновления ссылок проекта  
  
1.  Только для Visual Basic: в **обозревателе решений** щелкните **Показать все файлы**.  
  
2.  В **обозревателе решений** разверните узел **Ссылки**.  
  
3.  Щелкните правой кнопкой мыши следующие ссылки на сборки и выберите команду **Удалить**.  
  
    1.  Microsoft.Data.Schema.UnitTesting  
  
    2.  Microsoft.Data.Schema  
  
4.  В меню **Проект** или в контекстном меню, которое можно открыть, щелкнув правой кнопкой мыши папку проекта в **обозревателе решений**, выберите команду **Добавить ссылку**.  
  
5.  Перейдите на вкладку **.NET**.  
  
6.  В списке **Имя компонента** выберите **System.ComponentModel.Composition** и щелкните **ОК**.  
  
7.  Добавьте необходимые ссылки на сборки. Щелкните правой кнопкой мыши узел проекта и выберите команду **Добавить ссылку**. Щелкните **Обзор** и перейдите к папке C:\Program Files (x86)\\Microsoft SQL Server\110\DAC\Bin. Выберите Microsoft.Data.Tools.Schema.Sql.dll и нажмите «Добавить», а затем нажмите кнопку «ОК».  
  
8.  В меню **Проект** выберите пункт **Выгрузить проект**.  
  
9. Щелкните **проект** правой кнопкой мыши в **обозревателе решений** и выберите **Изменить**`project_name`**.csproj**.  
  
10. После импорта `Microsoft.CSharp.targets` добавьте следующую инструкцию Import:  
  
    ```  
    <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SSDT\Microsoft.Data.Tools.Schema.Sql.UnitTesting.targets" Condition="'$(VisualStudioVersion)' == ''" />  
  
    <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.Sql.UnitTesting.targets" Condition="'$(VisualStudioVersion)' != ''" />  
    ```  
  
11. Сохраните файл и закройте его. Щелкните проект правой кнопкой мыши в **обозревателе решений** и выберите **Перезагрузить проект**.  
  
12. Откройте класс условий теста и удалите все инструкции Using, которые начинаются с **Microsoft.Data.Schema**. Сделать это проще всего, щелкнув файл правой кнопкой мыши и выбрав **Упорядочение Using** и **Удалить и сортировать**. Необходимо удалить следующие инструкции Using:  
  
    ```  
    using Microsoft.Data.Schema.UnitTesting;  
    using Microsoft.Data.Schema.UnitTesting.Conditions;  
    using Microsoft.Data.Schema.Extensibility;  
    using Microsoft.Data.Schema;  
    ```  
  
13. Добавьте в файл следующие инструкции Using (если их там нет):  
  
    ```  
    using System.ComponentModel;  
    using Microsoft.Data.Tools.Schema.Sql.UnitTesting;  
    using Microsoft.Data.Tools.Schema.Sql.UnitTesting.Conditions;  
    ```  
  
Теперь условие теста будет использовать ссылки на сборки модульного тестирования SQL Server.  
  
## <a name="UpdateClassAttributesandTypeReference"></a>Обновление атрибутов классов и ссылок на типы  
Замените старые атрибуты класса модульного тестирования на новый атрибут. Расширяемость модульного тестирования SQL Server теперь основывается на Managed Extensibility Framework (MEF). Также необходимо обносить некоторые ссылки на типы.  
  
### <a name="update-class-attributes"></a>Обновление атрибутов классов  
Внесите в код следующие изменения.  
  
1.  Удалите атрибуты `DatabaseSchemaProviderCompatibility`. Они были необходимы для компонента расширяемости предыдущей версии и не поддерживаются в модульном тестировании SQL Server.  
  
2.  Удалите атрибут `DisplayName`. Отображаемое имя включается в новый атрибут.  
  
3.  Добавьте новый атрибут `ExportTestCondition`. Этот атрибут нужен для обнаружения и использования условия теста в модульном тестировании SQL Server. `ExportTestCondition` заменяет собой атрибуты `DatabaseSchemaProviderCompatibility`. `ExportTestCondition` принимает два параметра:  
  
    -   `DisplayName` является первым параметром. Он заменяет атрибут `DisplayName` и используется для описания всех условий теста этого типа.  
  
    -   Второй параметр используется для того, чтобы уникально определять расширение. Можно просто передать тип с помощью `typeof(NewTestCondition)`, поскольку он должен быть уникальным. Однако, если вам больше нравится, строковый идентификатор также можно передать.  
  
4.  Определение класса должно измениться следующим образом.  
  
    Перед следующей операцией.  
  
    ```  
    [DatabaseSchemaProviderCompatibility(typeof(DatabaseSchemaProvider))]  
    [DatabaseSchemaProviderCompatibility(null)]  
    [DisplayName("NewTestCondition")]  
    public class NewTestCondition:TestCondition  
    {  
       // Additional implementation to be added here  
    }  
    ```  
  
    После следующих операций.  
  
    ```  
    [ExportTestCondition("NewTestCondition ", typeof(NewTestCondition))]  
    public class NewTestCondition:TestCondition  
    {  
       // Additional implementation to be added here  
    }  
    ```  
  
### <a name="update-type-references"></a>Обновление ссылок на типы  
На платформе модульного тестирования SQL Server изменились имена некоторых типов. Чтобы обновить эти имена в существующем коде, используйте команду **Найти и заменить** в меню **Правка**. Теперь имена типов начинаются с **Sql**. Имена классов необходимо изменить следующим образом.  
  
|Старое имя типа|Новое имя типа|  
|-----------------|-----------------|  
|`ExecutionResult`|`SqlExecutionResult`|  
  
## <a name="ApplytheNewRegistrationProcess"></a>Установка обновленного условия теста  
В предыдущих версиях модульного тестирования баз данных иногда требовалось устанавливать условия тестов в глобальный кэш сборок либо создавать XML-файл, содержащий данные сборки. В модульном тестировании SQL Server этот дополнительный процесс больше не требуется. (Дополнительные сведения см. в статье [Компиляция проекта и установка условия теста](../ssdt/walkthrough-use-custom-test-condition-to-verify-stored-procedure-results.md#xxx).)  
  
После обновления ссылок подпишите и скомпилируйте свою сборку.  
  
Затем скопируйте файл сборки из выходного каталог (по умолчанию это "Мои документы\Visual Studio 2010\Projects\\<yoursolutionname>\\<yourprojectname>bin\Debug\\") в каталог %Program Files%\Microsoft Visual Studio <Version>\Common7\IDE\Extensions\Microsoft\SQLDB\TestConditions. При запуске Visual Studio программа определяет расширения в каталоге TestConditions и позволяет использовать их в рамках сеанса.  
  
## <a name="upgrade-existing-tests-that-need-to-use-the-new-test-condition"></a>Обновление существующих тестов, которым требуется использовать новое условие теста  
Найдите все проекты тестов, которые используют старое условие теста и которым требуется использовать новое условие. Выполните обновление этих проектов. Дополнительные сведения см. в статье [Обновление старого тестового проекта, содержащего модульные тесты базы данных](../ssdt/upgrade-an-older-test-project-containing-database-unit-tests.md).  
  
Удалите ссылку на сборку на старое условие теста.  
  
Добавьте в проект новый модульный тест SQL Server, чтобы создать в проекте ссылку на сборку с обновленным условием теста. Для создания ссылки необходимо добавить класс теста. После добавления ссылки класс теста можно будет удалить.  
  
## <a name="see-also"></a>См. также:  
[Пользовательские условия теста для модульных тестов SQL Server](../ssdt/custom-test-conditions-for-sql-server-unit-tests.md)  
  
