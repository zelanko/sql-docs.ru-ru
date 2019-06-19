---
title: Руководство. Создание условий теста для конструктора модульных тестов SQL Server | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 48076062-1ef5-419a-8a55-3c7b4234cc35
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 52975d96b6db206b4cdd2b6b201bc55eb572131c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65090266"
---
# <a name="how-to-create-test-conditions-for-the-sql-server-unit-test-designer"></a>Руководство. создать условия теста для конструктора модульных тестов SQL Server
Создавать условия теста можно с помощью расширяемого класса [TestCondition](https://msdn.microsoft.com/library/microsoft.data.tools.schema.sql.unittesting.conditions.testcondition(v=vs.103).aspx). Например, можно создать новое условие теста, которое проверяет число столбцов или значений в результирующем наборе.  
  
## <a name="to-create-a-test-condition"></a>Создание условия теста  
В этой процедуре объясняется, как создать условие теста, которое появится в конструкторе модульных тестов SQL Server.  
  
1.  Создайте проект библиотеки классов в Visual Studio.  
  
2.  В меню **Проект** выберите пункт **Добавить ссылку**.  
  
3.  Перейдите на вкладку **.NET**.  
  
4.  В списке **Имя компонента** выберите **System.ComponentModel.Composition** и щелкните **ОК**.  
  
5.  Добавьте необходимые ссылки на сборки. Щелкните правой кнопкой мыши узел проекта и выберите команду **Добавить ссылку**. Щелкните **Обзор** и перейдите к папке C:\Program Files (x86)\\Microsoft SQL Server\110\DAC\Bin. Выберите Microsoft.Data.Tools.Schema.Sql.dll и нажмите «Добавить», а затем нажмите кнопку «ОК».  
  
6.  В меню **Проект** выберите **Выгрузить проект**.  
  
7.  Щелкните проект правой кнопкой мыши в **обозревателе решений** и выберите **Изменить <project name>.csproj**.  
  
8.  После импорта Microsoft.CSharp.targets добавьте следующие инструкции Import:  
  
    ```  
    <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SSDT\Microsoft.Data.Tools.Schema.Sql.UnitTesting.targets" Condition="'$(VisualStudioVersion)' == ''" />  
    <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.Sql.UnitTesting.targets" Condition="'$(VisualStudioVersion)' != ''" />  
    ```  
  
9. Сохраните файл и закройте его. Щелкните проект правой кнопкой мыши в **обозревателе решений** и выберите **Перезагрузить проект**.  
  
10. Создайте класс производный от класса [TestCondition](https://msdn.microsoft.com/library/microsoft.data.tools.schema.sql.unittesting.conditions.testcondition(v=vs.103).aspx).  
  
11. Подпишите сборку строгим именем. Дополнительные сведения см. в разделе [Как подписать сборку строгим именем](https://msdn.microsoft.com/library/xc31ft41.aspx).  
  
12. Постройте библиотеку классов.  
  
13. Чтобы новое условие теста можно было использовать, скопируйте подписанную сборку в папку "%Program Files%\Microsoft Visual Studio <Version>\Common7\IDE\Extensions\Microsoft\SQLDB\TestConditions". Если такой папки не существует, создайте ее. Для копирования файлов в этот каталог пользователь должен обладать правами доступа администратора на компьютере.  
  
14. Установите условие теста. Дополнительные сведения см. в статье [о пользовательских условиях теста для модульных тестов SQL Server](../ssdt/custom-test-conditions-for-sql-server-unit-tests.md).  
  
15. Добавьте в проект новый модульный тест SQL Server, чтобы создать в проекте ссылку на условие теста, которое требуется добавить в проект. Можно вручную добавить ссылку на сборку условий теста в проекте. Перезагрузите конструктор после выполнения этого шага.  
  
    > [!NOTE]  
    > Для создания ссылки необходимо добавить класс теста. После добавления ссылки класс теста можно будет удалить.  
  
В следующем примере создается простое условие теста, которое проверяет число столбцов, возвращенных в ResultSet. С помощью этого простого условия теста можно проверять правильность контракта для хранимой процедуры.  
  
```  
using System;  
using System.ComponentModel;  
using System.Data;  
using System.Data.Common;  
using Microsoft.Data.Tools.Schema.Sql.UnitTesting;  
using Microsoft.Data.Tools.Schema.Sql.UnitTesting.Conditions;  
  
namespace Ssdt.Samples.SqlUnitTesting  
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
  
        // method you need to override  
        // to perform the condition verification  
        public override void Assert(DbConnection validationConnection, SqlExecutionResult[] results)  
        {  
            // call base for parameter validation  
            base.Assert(validationConnection, results);  
  
            // verify batch exists  
            if (results.Length < _batch)  
                throw new DataException(String.Format("Batch {0} does not exist", _batch));  
  
            SqlExecutionResult result = results[_batch - 1];  
  
            // verify resultset exists  
            if (result.DataSet.Tables.Count < ResultSet)  
                throw new DataException(String.Format("ResultSet {0} does not exist", ResultSet));  
  
            DataTable table = result.DataSet.Tables[ResultSet - 1];  
  
            // actual condition verification  
            // verify resultset column count matches expected  
            if (table.Columns.Count != Count)  
                throw new DataException(String.Format(  
                    "ResultSet {0}: {1} columns did not match the {2} columns expected",  
                    ResultSet, table.Columns.Count, Count));  
        }  
  
        // this method is called to provide the string shown in the  
        // test conditions panel grid describing what the condition tests  
        public override string ToString()  
        {  
            return String.Format(  
                "Condition fails if ResultSet {0} does not contain {1} columns",  
                ResultSet, Count);  
        }  
  
        // below are the test condition properties  
        // that are exposed to the user in the property browser  
        #region Properties  
  
        // property specifying the resultset for which  
        // you want to check the column count  
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
  
        // property specifying  
        // expected column count  
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
  
Класс для пользовательского условия теста является производным от базового класса [TestCondition](https://msdn.microsoft.com/library/microsoft.data.tools.schema.sql.unittesting.conditions.testcondition(v=vs.103).aspx). Поскольку у нестандартного условия теста есть дополнительные свойства, пользователи могут настраивать условие в окне «Свойства» после его установки.  
  
[ExportTestConditionAttribute](https://msdn.microsoft.com/library/microsoft.data.tools.schema.sql.unittesting.conditions.exporttestconditionattribute(v=vs.103).aspx) необходимо добавить во все классы, являющиеся расширением [TestCondition](https://msdn.microsoft.com/library/microsoft.data.tools.schema.sql.unittesting.conditions.testcondition(v=vs.103).aspx). Этот атрибут позволяет SQL Server Data Tools обнаруживать этот класс и использовать его при проектировании и выполнении модульных тестов. Этот атрибут принимает два параметра.  
  
|Параметр атрибута|Положение|Описание|  
|-----------------------|------------|---------------|  
|DisplayName|1|Определяет строку в поле со списком "Условия теста". Имя должно быть уникальным. Если у двух условий одинаковое отображаемое имя, пользователю будет показано первое условие, при этом в диспетчере ошибок Visual Studio будет показано предупреждение.|  
|ImplementingType|2|Используется для уникального определения расширения. Это значение необходимо изменить, чтобы оно совпадало с типом, которому задается этот атрибут. В этом примере используется тип **ResultSetColumnCountCondition**, поэтому нужно указать **typeof(ResultSetColumnCountCondition)**. Если вы используете тип **NewTestCondition**, укажите вместо этого **typeof(NewTestCondition)**.|  
  
В этом примере добавляются два свойства. Пользователи нестандартного условия теста могут использовать свойство ResultSet, чтобы указать, для какого результирующего набора следует выполнять проверку числа столбцов. Затем с помощью свойства Count пользователи могут указать ожидаемое число столбцов.  
  
Для каждого свойства добавляется по три атрибута:  
  
-   Имя категории, которое помогает в организации свойств.  
  
-   Отображаемое имя свойства.  
  
-   Описание свойства.  
  
Проверка выполняется по свойствам: проверяется, чтобы значение свойства ResultSet не было меньше одного, а значение свойства Count было больше нуля.  
  
Метод Assert выполняет основную задачу условия теста. Вы переопределяете метод Assert, чтобы проверить соблюдение ожидаемого условия. Этот метод предоставляет два параметра.  
  
-   Первым параметром является подключение к базе данных, которое используется для проверки условия теста.  
  
-   Вторым и более важным параметром является массив результатов, который возвращает один элемент массива для каждого выполнявшегося пакета.  
  
Для каждого скрипта теста поддерживается только один пакет. Поэтому условия теста всегда анализируют первый элемент массива. Элемент массива содержит DataSet, который, в свою очередь, содержит возвращаемые результирующие наборы для скрипта теста. В этом примере код проверяет наличие в таблице данных из DataSet соответствующего числа столбцов. Дополнительные сведения см. в разделе «DataSet».  
  
Необходимо подписать библиотеку классов, которая содержит условие теста. Сделать это можно на вкладке «Подписание» страницы свойств проекта.  
  
## <a name="see-also"></a>См. также:  
[Пользовательские условия теста для модульных тестов SQL Server](../ssdt/custom-test-conditions-for-sql-server-unit-tests.md)  
  
