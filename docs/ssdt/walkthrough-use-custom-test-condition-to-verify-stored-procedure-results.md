---
title: Пошаговое руководство. Использование пользовательского условия теста для проверки результатов выполнения хранимой процедуры | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4c33b494-a85e-4dd2-97b6-c88ee858a99c
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1dcc845c366b912f762e9bbf805c54c5de920fca
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085836"
---
# <a name="walkthrough-using-a-custom-test-condition-to-verify-the-results-of-a-stored-procedure"></a>Пошаговое руководство. Использование пользовательского условия теста для проверки результатов выполнения хранимой процедуры
В этом пошаговом руководстве по расширению компонента описано, как создать условие теста и проверить его работоспособность, создав модульный тест SQL Server. Частью этого процесса является создание проекта библиотеки классов для условия теста, а также его подписание и установка. Если у вас уже есть условие теста и вы хотите обновить его, воспользуйтесь документом [Практическое руководство. Обновление пользовательского условия теста Visual Studio 2010 с предыдущего выпуска до SQL Server Data Tools](../ssdt/how-to-upgrade-visual-studio-2010-custom-test-condition-to-ssdt.md).  
  
В этом пошаговом руководстве описаны следующие задачи:  
  
-   Создание условия теста.  
  
-   Подписание сборки строгим именем.  
  
-   Добавление необходимых ссылок в проект.  
  
-   Построение условия теста.  
  
-   Установка нового условия теста.  
  
-   Проверка нового условия теста.  
  
Для работы с этим пошаговым руководством вам потребуется Visual Studio 2010 или Visual Studio 2012 с последней версии SQL Server Data Tools. Дополнительные сведения см. в руководстве по [установке SQL Server Data Tools](../ssdt/install-sql-server-data-tools.md).  
  
## <a name="creating-a-custom-test-condition"></a>Создание пользовательского условия теста  
Сначала будет создана библиотека классов.  
  
1.  В меню **Файл** выберите пункт **Создать**, а затем щелкните **Проект**.  
  
2.  В диалоговом окне **Создание проекта** в разделе **Типы проектов** щелкните Visual C\#.  
  
3.  В разделе **Шаблоны** выберите пункт **Библиотека классов**.  
  
4.  В текстовое поле **Имя** введите **ColumnCountCondition** и щелкните **ОК**.  
  
Затем подпишите проект.  
  
1.  В меню **Проект** выберите пункт **Свойства ColumnCountCondition**.  
  
2.  На вкладке **Подпись** установите флажок **Подписать сборку**.  
  
3.  В поле **Выберите файл ключа строгого имени** щелкните **\<Создать>**.  
  
    Откроется диалоговое окно **Создание ключа строгого имени**.  
  
4.  В поле **Имя файла ключа** введите **SampleKey**.  
  
5.  Введите и подтвердите пароль, а затем щелкните **ОК**. При построении решения файл ключа используется для подписания сборки.  
  
6.  В меню **Файл** выберите команду **Сохранить все**.  
  
7.  В меню **Сборка** выберите **Построить решение**.  
  
Затем выполняется добавление необходимых ссылок в проект.  
  
1.  В **обозревателе решений** выберите проект **ColumnCountCondition**.  
  
2.  В меню **Проект** щелкните **Добавить ссылку**, чтобы открыть диалоговое окно **Добавление ссылки**.  
  
3.  Перейдите на вкладку **.NET**.  
  
4.  В столбце **Имя компонента** найдите и выберите компонент **System.ComponentModel.Composition**. Выбрав этот компонент, щелкните **ОК**.  
  
5.  Добавьте необходимые ссылки на сборки. Щелкните правой кнопкой мыши узел проекта и выберите команду **Добавить ссылку**. Щелкните **Обзор** и перейдите к папке C:\Program Files (x86)\\Microsoft SQL Server\110\DAC\Bin. Выберите Microsoft.Data.Tools.Schema.Sql.dll и нажмите «Добавить», а затем нажмите кнопку «ОК».  
  
6.  В меню **Проект** выберите **Выгрузить проект**.  
  
7.  Щелкните проект правой кнопкой мыши в **обозревателе решений** и выберите **Изменить <project name>.csproj**.  
  
8.  После импорта **Microsoft.CSharp.targets** добавьте следующие инструкции Import:  
  
    ```  
    <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SSDT\Microsoft.Data.Tools.Schema.Sql.UnitTesting.targets" Condition="'$(VisualStudioVersion)' == ''" />  
  
    <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.Sql.UnitTesting.targets" Condition="'$(VisualStudioVersion)' != ''" />  
    ```  
  
9. Сохраните файл и закройте его. Щелкните проект правой кнопкой мыши в **обозревателе решений** и выберите **Перезагрузить проект**.  
  
    Требуемые ссылки будут показаны в узле **Ссылки** для проекта в **обозревателе решений**.  
  
## <a name="creating-the-resultsetcolumncountcondition-class"></a>Создание класса ResultSetColumnCountCondition  
Теперь переименуйте **Class1** в **ResultSetColumnCountCondition** и настройте наследование от [testcondition](https://msdn.microsoft.com/en-us/library/microsoft.data.tools.schema.sql.unittesting.conditions.testcondition(v=vs.103).aspx). Класс **ResultSetColumnCountCondition** является простым условием теста, которое проверяет число столбцов, возвращенных в наборе ResultSet. С помощью этого условия теста можно проверять правильность контракта для хранимой процедуры.  
  
1.  В **обозревателе решений** щелкните правой кнопкой мыши Class1.cs, выберите команду **Переименовать** и введите **ResultSetColumnCountCondition.cs**.  
  
2.  Нажмите кнопку **Да**, чтобы подтвердить переименование всех ссылок на Class1.  
  
3.  Откройте файл **ResultSetColumnCountCondition.cs** и добавьте в него следующие инструкции Using.  
  
    ```  
    using System;  
    using System.ComponentModel;  
    using System.Data;  
    using System.Data.Common;  
    using Microsoft.Data.Tools.Schema.Sql.UnitTesting;  
    using Microsoft.Data.Tools.Schema.Sql.UnitTesting.Conditions;  
  
    namespace ColumnCountCondition {  
        public class ResultSetColumnCountCondition  
    ```  
  
4.  Сделайте этот класс производным от класса [testcondition](https://msdn.microsoft.com/en-us/library/microsoft.data.tools.schema.sql.unittesting.conditions.testcondition(v=vs.103).aspx).  
  
    ```  
    public class ResultSetColumnCountCondition : TestCondition  
    ```  
  
5.  Добавьте [ExportTestConditionAttribute](https://msdn.microsoft.com/en-us/library/microsoft.data.tools.schema.sql.unittesting.conditions.exporttestconditionattribute(v=vs.103).aspx). В статье [Практическое руководство. Создание условия теста для конструктора модульных тестов SQL Server](../ssdt/how-to-create-test-conditions-for-the-sql-server-unit-test-designer.md) вы найдете дополнительные сведения об атрибуте UnitTesting.Conditions.ExportTestConditionAttribute.  
  
    ```  
    [ExportTestCondition("ResultSet Column Count", typeof(ResultSetColumnCountCondition))]  
        public class ResultSetColumnCountCondition : TestCondition  
    ```  
  
6.  Создайте переменные и конструктор.  
  
    ```  
            private int _resultSet;  
            private int _count;  
            private int _batch;  
  
            public ResultSetColumnCountCondition() {  
                _resultSet = 1;  
                _count = 0;  
                _batch = 1;  
            }  
    ```  
  
7.  Переопределите метод **Assert**. Этот метод включает аргументы для объектов **IDbConnection**, который представляет подключение к базе данных, и **SqlExecutionResult**. Этот метод использует **DataSchemaException** для обработки ошибок:  
  
    ```  
           //method you need to override  
            //to perform the condition verification  
            public override void Assert(DbConnection validationConnection, SqlExecutionResult[] results)  
            {  
                //call base for parameter validation  
                base.Assert(validationConnection, results);  
  
                //verify batch exists  
                if (results.Length < _batch)  
                    throw new DataException(String.Format("Batch {0} does not exist", _batch));  
  
                SqlExecutionResult result = results[_batch - 1];  
  
                //verify resultset exists  
                if (result.DataSet.Tables.Count < ResultSet)  
                    throw new DataException(String.Format("ResultSet {0} does not exist", ResultSet));  
  
                DataTable table = result.DataSet.Tables[ResultSet - 1];  
  
                //actual condition verification  
                //verify resultset column count matches expected  
                if (table.Columns.Count != Count)  
                    throw new DataException(String.Format(  
                        "ResultSet {0}: {1} columns did not match the {2} columns expected",  
                        ResultSet, table.Columns.Count, Count));  
            }  
  
    Add the following method, which overrides the ToString method:  
    C#  
            //this method is called to provide the string shown in the  
            //test conditions panel grid describing what the condition tests  
            public override string ToString()  
            {  
                return String.Format(  
                    "Condition fails if ResultSet {0} does not contain {1} columns",  
                    ResultSet, Count);  
            }  
    ```  
  
8.  Добавьте следующие свойства для условий теста с помощью атрибутов **CategoryAttribute**, **DisplayNameAttribute** и **DescriptionAttribute**:  
  
    ```  
            //below are the test condition properties  
            //that are exposed to the user in the property browser  
            #region Properties  
  
            //property specifying the resultset for which  
            //you want to check the column count  
            [Category("Test Condition")]  
            [DisplayName("ResultSet")]  
            [Description("ResultSet Number")]  
            public int ResultSet  
            {  
                get { return _resultSet; }  
  
                set  
                {  
                    //basic validation  
                    if (value < 1)  
                        throw new ArgumentException("ResultSet cannot be less than 1");  
  
                    _resultSet = value;  
                }  
            }  
  
            //property specifying  
            //expected column count  
            [Category("Test Condition")]  
            [DisplayName("Count")]  
            [Description("Column Count")]  
            public int Count  
            {  
                get { return _count; }  
  
                set  
                {  
                    //basic validation  
                    if (value < 0)  
                        throw new ArgumentException("Count cannot be less than 0");  
  
                    _count = value;  
                }  
            }  
             #endregion  
    ```  
  
Далее приведен итоговый код:  
  
```  
using System;  
using System.ComponentModel;  
using System.Data;  
using System.Data.Common;  
using Microsoft.Data.Tools.Schema.Sql.UnitTesting;  
using Microsoft.Data.Tools.Schema.Sql.UnitTesting.Conditions;  
  
namespace ColumnCountCondition  
{  
  
    [ExportTestCondition("ResultSet Column Count", typeof(ResultSetColumnCountCondition))]  
    public class ResultSetColumnCountCondition : TestCondition  
    {  
        private int _resultSet;  
        private int _count;  
        private int _batch;  
  
        public ResultSetColumnCountCondition()  
        {  
            _resultSet = 1;  
            _count = 0;  
            _batch = 1;  
        }  
  
        //method you need to override  
        //to perform the condition verification  
        public override void Assert(DbConnection validationConnection, SqlExecutionResult[] results)  
        {  
            //call base for parameter validation  
            base.Assert(validationConnection, results);  
  
            //verify batch exists  
            if (results.Length < _batch)  
                throw new DataException(String.Format("Batch {0} does not exist", _batch));  
  
            SqlExecutionResult result = results[_batch - 1];  
  
            //verify resultset exists  
            if (result.DataSet.Tables.Count < ResultSet)  
                throw new DataException(String.Format("ResultSet {0} does not exist", ResultSet));  
  
            DataTable table = result.DataSet.Tables[ResultSet - 1];  
  
            //actual condition verification  
            //verify resultset column count matches expected  
            if (table.Columns.Count != Count)  
                throw new DataException(String.Format(  
                    "ResultSet {0}: {1} columns did not match the {2} columns expected",  
                    ResultSet, table.Columns.Count, Count));  
        }  
  
        //this method is called to provide the string shown in the  
        //test conditions panel grid describing what the condition tests  
        public override string ToString()  
        {  
            return String.Format(  
                "Condition fails if ResultSet {0} does not contain {1} columns",  
                ResultSet, Count);  
        }  
  
        //below are the test condition properties  
        //that are exposed to the user in the property browser  
        #region Properties  
  
        //property specifying the resultset for which  
        //you want to check the column count  
        [Category("Test Condition")]  
        [DisplayName("ResultSet")]  
        [Description("ResultSet Number")]  
        public int ResultSet  
        {  
            get { return _resultSet; }  
  
            set  
            {  
                //basic validation  
                if (value < 1)  
                    throw new ArgumentException("ResultSet cannot be less than 1");  
  
                _resultSet = value;  
            }  
        }  
  
        //property specifying  
        //expected column count  
        [Category("Test Condition")]  
        [DisplayName("Count")]  
        [Description("Column Count")]  
        public int Count  
        {  
            get { return _count; }  
  
            set  
            {  
                //basic validation  
                if (value < 0)  
                    throw new ArgumentException("Count cannot be less than 0");  
  
                _count = value;  
            }  
        }  
  
        #endregion  
    }  
}  
  
```  
  
Теперь выполним построение проекта.  
  
## <a name="xxx"></a>Компиляция проекта и установка условия теста  
В меню **Сборка** выберите **Построить решение**.  
  
Затем необходимо будет скопировать данные сборки в каталог Extensions. При запуске Visual Studio программа обнаруживает все расширения в папке %Program Files%\Microsoft Visual Studio <Version>\Common7\IDE\Extensions\Microsoft\SQLDB\TestConditions и вложенных папках, позволяя использовать их.  
  
Скопируйте файл сборки **ColumnCountCondition.dll** из выходного каталога в каталог %Program Files%\Microsoft Visual Studio <Version>\Common7\IDE\Extensions\Microsoft\SQLDB\TestConditions.  
  
По умолчанию cкомпилированный файл библиотеки DLL помещается в папку *путь_к_решению*\\*путь_к_проекту*bin\Debug или *путь_к_решению*\\*путь_к_проекту*bin\Release.  
  
Затем запустите новый сеанс Visual Studio и создайте проект базы данных. Чтобы запустить новый сеанс работы Visual Studio и создать проект базы данных, сделайте следующее:  
  
1.  Запустите второй сеанс работы Visual Studio.  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем щелкните **Проект**.  
  
3.  В диалоговом окне **Создание проекта** выберите в списке установленных шаблонов узел **SQL Server**.  
  
4.  На панели сведений щелкните **Проект базы данных SQL Server**.  
  
5.  В текстовое поле **Имя** введите **SampleConditionDB** и щелкните **ОК**.  
  
Теперь необходимо создать модульный тест. Чтобы создать модульный тест SQL Server в новом тестовом классе, сделайте следующее:  
  
1.  В меню **Тест** выберите команду **Создать тест**, чтобы открыть диалоговое окно **Добавление нового теста**.  
  
    Также можно открыть **обозреватель решений**, щелкнуть правой кнопкой мыши тестовый проект, выбрать **Добавить** и щелкнуть **Создать тест**.  
  
2.  В списке шаблонов щелкните **Модульный тест SQL Server**.  
  
3.  В поле **Имя теста** введите **SampleUnitTest**.  
  
4.  В разделе **Добавить в тестовый проект** щелкните **Создать тестовый проект Visual C\#**. Затем нажмите кнопку **ОК**, чтобы отобразить диалоговое окно **Новый тестовый проект**.  
  
5.  Введите имя проекта **SampleUnitTest**.  
  
6.  Чтобы создать модульный тест, не настраивая в тестовом проекте подключение к базе данных, нажмите кнопку **Отмена**. Пустой тест откроется в конструкторе модульных тестов SQL Server. В проект тестов будет добавлен файл с исходным кодом на Visual C\#.  
  
    Сведения о создании и настройке подключений к базе данных в модульных тестах баз данных см. в статье [Практическое руководство. Создание пустого модульного теста SQL Server](../ssdt/how-to-create-an-empty-sql-server-unit-test.md).  
  
7.  Щелкните **Щелкните здесь, чтобы создать** и завершите создание модульного теста. Новое условие теста будет отображено в проекте SQL Server.  
  
> [!NOTE]  
> Чтобы использовать созданное условие теста в существующих проектах модульных тестов, необходимо создать хотя бы один класс модульных тестов SQL Server. Требуемая ссылка на сборку условия теста добавляется в проект тестов во время создания класса тестов.  
  
Просмотр нового условия теста  
  
1.  В **конструкторе модульных тестов SQL Server** в разделе **Условия тестов** в столбце **Имя** щелкните тест inconclusiveCondition1.  
  
2.  Нажмите кнопку **Удалить условие теста** на панели инструментов, чтобы удалить тест inconclusiveCondition1.  
  
3.  Щелкните раскрывающийся список **Условия теста** и выберите **Число столбцов ResultSet**.  
  
4.  Нажмите кнопку **Добавить условие теста** на панели инструментов, чтобы добавить пользовательское условие теста.  
  
5.  В окне **Свойства** задайте значения для свойств Count, Enabled и ResultSet.  
  
    Дополнительные сведения см. в статье [Практическое руководство. Добавление условий теста в модульные тесты SQL Server](../ssdt/how-to-add-test-conditions-to-sql-server-unit-tests.md).  
  
## <a name="see-also"></a>См. также:  
[Пользовательские условия теста для модульных тестов SQL Server](../ssdt/custom-test-conditions-for-sql-server-unit-tests.md)  
  
