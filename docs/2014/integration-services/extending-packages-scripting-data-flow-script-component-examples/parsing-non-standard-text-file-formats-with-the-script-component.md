---
title: Синтаксический анализ текстовых файлов нестандартного формата в компоненте скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
helpviewer_keywords:
- text file reading [Integration Services]
- Script component [Integration Services], non-standard text file formats
- transformations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: 1fda034d-09e4-4647-9a9f-e8d508c2cc8f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 28ee2db3094944b28cd1cbc42e25015a88b04b9f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183764"
---
# <a name="parsing-non-standard-text-file-formats-with-the-script-component"></a>Синтаксический анализ текстовых файлов нестандартного формата в компоненте скрипта
  Если исходные данные организованы в нестандартном формате, может оказаться удобнее объединить всю логику синтаксического анализа в единый скрипт вместо создания цепочки преобразований служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], приводящих к тому же результату.  
  
 [Пример 1. Синтаксический анализ записей, разделенных на строки](#example1)  
  
 [Пример 2. Разделение родительских и дочерних записей](#example2)  
  
> [!NOTE]  
>  Если нужно создать компонент, который будет полезен в нескольких задачах потока данных и нескольких пакетах, рекомендуется в качестве основы использовать этот образец компонента скрипта. Дополнительные сведения см. в разделе [Разработка пользовательского компонента потока данных](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
##  <a name="example1"></a> Пример 1. Синтаксический анализ записей, разделенных на строки  
 В этом примере берется текстовый файл, в котором каждый столбец данных размещается на новой строке, и с помощью синтаксического анализа, реализованного в компоненте скрипта, преобразуется в целевую таблицу.  
  
 Дополнительные сведения о том, как настроить компонент скрипта для использования в качестве преобразования в потоке данных см. в разделе [создание синхронного преобразования с компонентом скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)и [Создание асинхронный Преобразование бизнеса с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Настройка этого примера компонента скрипта  
  
1.  Создайте и сохраните под именем **rowdelimiteddata.txt** текстовый файл, содержащий следующие исходные данные:  
  
    ```  
    FirstName: Nancy  
    LastName: Davolio  
    Title: Sales Representative  
    City: Seattle  
    StateProvince: WA  
  
    FirstName: Andrew  
    LastName: Fuller  
    Title: Vice President, Sales  
    City: Tacoma  
    StateProvince: WA  
  
    FirstName: Steven  
    LastName: Buchanan  
    Title: Sales Manager  
    City: London  
    StateProvince:  
  
    ```  
  
2.  Откройте среду [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] и установите соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Выберите целевую базу данных и откройте окно нового запроса. Чтобы создать целевую таблицу, выполните в окне запросов следующий скрипт.  
  
    ```  
    create table RowDelimitedData  
    (  
    FirstName varchar(32),  
    LastName varchar(32),  
    Title varchar(32),  
    City varchar(32),  
    StateProvince varchar(32)  
    )  
  
    ```  
  
4.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] создайте новый пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с именем ParseRowDelim.dtsx.  
  
5.  Добавьте в пакет диспетчер соединений с неструктурированными файлами, назовите этот диспетчер «RowDelimitedData» и настройте на соединение с файлом rowdelimiteddata.txt, созданным на предыдущем шаге.  
  
6.  Добавьте в пакет диспетчер соединений OLE DB и настройте его на соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и базой данных, в которой создана целевая таблица.  
  
7.  Добавьте в пакет задачу потока данных и щелкните вкладку **Поток данных** конструктора служб SSIS.  
  
8.  Добавьте к потоку данных источник «Неструктурированный файл» и настройте его на использование диспетчера соединений RowDelimitedData. На странице **Столбцы** в редакторе источника **Неструктурированный файл** выберите единственный доступный внешний столбец.  
  
9. Добавьте в поток данных компонент скрипта и настройте его в качестве преобразования. Соедините выход источника «Неструктурированный файл» с компонентом скрипта.  
  
10. Дважды щелкните компонент скрипта, чтобы открыть **редактор преобразования "Скрипт"**.  
  
11. На странице **Входные столбцы** в **редакторе преобразования "Скрипт"** выберите единственный доступный входной столбец.  
  
12. На **входы и выходы** странице **редактор преобразования "скрипт"** выберите выход 0 и задайте его `SynchronousInputID` значение None. Создайте 5 выходных столбцов со строковым типом [DT_STR] и длиной 32:  
  
    -   FirstName  
  
    -   LastName  
  
    -   Title  
  
    -   Город  
  
    -   StateProvince  
  
13. На **сценарий** странице **редактор преобразования "скрипт"**, нажмите кнопку **изменить скрипт** и введите код, показанный на `ScriptMain` класс примера. Закройте среду разработки скриптов и **редактор преобразования "Скрипт"**.  
  
14. Добавьте в поток данных назначение «SQL Server». Настройте его на использование диспетчера соединений OLE DB и таблицы RowDelimitedData. Настройте выход компонента скрипта на это назначение.  
  
15. Запустите пакет. По завершении работы пакета исследуйте записи в целевой таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
    Dim columnName As String  
    Dim columnValue As String  
  
    ' Check for an empty row.  
    If Row.Column0.Trim.Length > 0 Then  
        columnName = Row.Column0.Substring(0, Row.Column0.IndexOf(":"))  
        ' Check for an empty value after the colon.  
        If Row.Column0.Substring(Row.Column0.IndexOf(":")).TrimEnd.Length > 1 Then  
            ' Extract the column value from after the colon and space.  
            columnValue = Row.Column0.Substring(Row.Column0.IndexOf(":") + 2)  
            Select Case columnName  
                Case "FirstName"  
                    ' The FirstName value indicates a new record.  
                    Me.Output0Buffer.AddRow()  
                    Me.Output0Buffer.FirstName = columnValue  
                Case "LastName"  
                    Me.Output0Buffer.LastName = columnValue  
                Case "Title"  
                    Me.Output0Buffer.Title = columnValue  
                Case "City"  
                    Me.Output0Buffer.City = columnValue  
                Case "StateProvince"  
                    Me.Output0Buffer.StateProvince = columnValue  
            End Select  
        End If  
    End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
        string columnName;  
        string columnValue;  
  
        // Check for an empty row.  
        if (Row.Column0.Trim().Length > 0)  
        {  
            columnName = Row.Column0.Substring(0, Row.Column0.IndexOf(":"));  
            // Check for an empty value after the colon.  
            if (Row.Column0.Substring(Row.Column0.IndexOf(":")).TrimEnd().Length > 1)  
            // Extract the column value from after the colon and space.  
            {  
                columnValue = Row.Column0.Substring(Row.Column0.IndexOf(":") + 2);  
                switch (columnName)  
                {  
                    case "FirstName":  
                        // The FirstName value indicates a new record.  
                        this.Output0Buffer.AddRow();  
                        this.Output0Buffer.FirstName = columnValue;  
                        break;  
                    case "LastName":  
                        this.Output0Buffer.LastName = columnValue;  
                        break;  
                    case "Title":  
                        this.Output0Buffer.Title = columnValue;  
                        break;  
                    case "City":  
                        this.Output0Buffer.City = columnValue;  
                        break;  
                    case "StateProvince":  
                        this.Output0Buffer.StateProvince = columnValue;  
                        break;  
                }  
            }  
        }  
  
    }  
```  
  
##  <a name="example2"></a> Пример 2. Разделение родительских и дочерних записей  
 В этом примере берется текстовый файл, в котором за строкой-разделителем следует родительская строка, а за ней — неопределенное количество дочерних строк, и с помощью синтаксического анализа, реализованного в компоненте скрипта, преобразуется в две правильным образом нормализованные целевые таблицы — родительскую и дочернюю. Этот простой пример легко адаптировать для исходных файлов, использующих несколько строк или столбцов для каждой родительской и дочерней записи: главное, чтобы начало и конец каждой записи были как-то обозначены.  
  
> [!CAUTION]  
>  Данный образец предназначен только для демонстрационных целей. Если запустить образец несколько раз, он вставит в целевую таблицу повторяющиеся ключевые значения.  
  
 Дополнительные сведения о том, как настроить компонент скрипта для использования в качестве преобразования в потоке данных см. в разделе [создание синхронного преобразования с компонентом скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)и [Создание асинхронный Преобразование бизнеса с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Настройка этого примера компонента скрипта  
  
1.  Создайте и сохраните под именем **parentchilddata.txt** текстовый файл, содержащий следующие исходные данные:  
  
    ```  
    **********  
    PARENT 1 DATA  
    child 1 data  
    child 2 data  
    child 3 data  
    child 4 data  
    **********  
    PARENT 2 DATA  
    child 5 data  
    child 6 data  
    child 7 data  
    child 8 data  
    **********  
  
    ```  
  
2.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Выберите целевую базу данных и откройте окно нового запроса. Чтобы создать целевые таблицы, выполните в окне запросов следующий скрипт.  
  
    ```  
    CREATE TABLE [dbo].[Parents]([ParentID] [int] NOT NULL,  
    [ParentRecord] [varchar](32) NOT NULL,  
     CONSTRAINT [PK_Parents] PRIMARY KEY CLUSTERED   
    ([ParentID] ASC))  
    GO  
    CREATE TABLE [dbo].[Children]([ChildID] [int] NOT NULL,  
    [ParentID] [int] NOT NULL,  
    [ChildRecord] [varchar](32) NOT NULL,  
     CONSTRAINT [PK_Children] PRIMARY KEY CLUSTERED   
    ([ChildID] ASC))  
    GO  
    ALTER TABLE [dbo].[Children] ADD CONSTRAINT [FK_Children_Parents] FOREIGN KEY([ParentID])  
    REFERENCES [dbo].[Parents] ([ParentID])  
  
    ```  
  
4.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] создайте новый пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с именем «SplitParentChild.dtsx».  
  
5.  Добавьте в пакет диспетчер соединений с неструктурированными файлами, назовите этот диспетчер «ParentChildData» и настройте на соединение с файлом parentchilddata.txt, созданным на предыдущем шаге.  
  
6.  Добавьте в пакет диспетчер соединений OLE DB и настройте его на соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и базой данных, в которой созданы целевые таблицы.  
  
7.  Добавьте в пакет задачу потока данных и щелкните вкладку **Поток данных** конструктора служб SSIS.  
  
8.  Добавьте к потоку данных источник «Неструктурированный файл» и настройте его на использование диспетчера соединений ParentChildData. На странице **Столбцы** в редакторе источника **Неструктурированный файл** выберите единственный доступный внешний столбец.  
  
9. Добавьте в поток данных компонент скрипта и настройте его в качестве преобразования. Соедините выход источника «Неструктурированный файл» с компонентом скрипта.  
  
10. Дважды щелкните компонент скрипта, чтобы открыть **редактор преобразования "Скрипт"**.  
  
11. На странице **Входные столбцы** в **редакторе преобразования "Скрипт"** выберите единственный доступный входной столбец.  
  
12. На **входы и выходы** странице **редактор преобразования "скрипт"**, выберите выход 0, переименуйте его в ParentRecords и задайте его `SynchronousInputID` значение None. Создайте 2 выходных столбца.  
  
    -   ParentID (первичный ключ), имеющий тип четырехбайтового целого числа со знаком [DT_I4].  
  
    -   ParentRecord, строкового типа [DT_STR], длиной 32 символа.  
  
13. Создайте второй вывод и установите для него имя ChildRecords. Параметр `SynchronousInputID` для нового вывода уже установлен в значение «Нет». Создайте 3 выходных столбца.  
  
    -   ChildID (первичный ключ), имеющий тип четырехбайтового целого числа со знаком [DT_I4].  
  
    -   ParentID (внешний ключ), также типа «четырехбайтовое целое число со знаком» [DT_I4].  
  
    -   ChildRecord, строкового типа [DT_STR], длиной 50 символов.  
  
14. На странице **Скрипт** **редактора преобразования "Скрипт"** нажмите кнопку **Изменить скрипт**. Вставьте код, приведенный в примере, в класс `ScriptMain`. Закройте среду разработки скриптов и **редактор преобразования "Скрипт"**.  
  
15. Добавьте в поток данных назначение «SQL Server». Подключите выход ParentRecords компонента скрипта к этому назначению. Настройте его на использование диспетчера соединений OLE DB и таблицы Parents.  
  
16. Добавьте к потоку данных еще одно назначение «SQL Server». Настройте выход ChildRecords компонента скрипта на это назначение. Настройте его на использование диспетчера соединений OLE DB и таблицы Children.  
  
17. Запустите пакет. По завершении работы пакета исследуйте записи в двух целевых таблицах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
    Static nextRowIsParent As Boolean = False  
    Static parentCounter As Integer = 0  
    Static childCounter As Integer = 0  
  
    ' If current row starts with separator characters,  
    '  then following row contains new parent record.  
    If Row.Column0.StartsWith("***") Then  
        nextRowIsParent = True  
    Else  
        If nextRowIsParent Then  
            ' Current row contains parent record.  
            parentCounter += 1  
            Me.ParentRecordsBuffer.AddRow()  
            Me.ParentRecordsBuffer.ParentID = parentCounter  
            Me.ParentRecordsBuffer.ParentRecord = Row.Column0  
            nextRowIsParent = False  
        Else  
            ' Current row contains child record.  
            childCounter += 1  
            Me.ChildRecordsBuffer.AddRow()  
            Me.ChildRecordsBuffer.ChildID = childCounter  
            Me.ChildRecordsBuffer.ParentID = parentCounter  
            Me.ChildRecordsBuffer.ChildRecord = Row.Column0  
        End If  
    End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
    int static_Input0_ProcessInputRow_childCounter = 0;  
    int static_Input0_ProcessInputRow_parentCounter = 0;  
    bool static_Input0_ProcessInputRow_nextRowIsParent = false;  
  
        // If current row starts with separator characters,   
        // then following row contains new parent record.   
        if (Row.Column0.StartsWith("***"))  
        {  
            static_Input0_ProcessInputRow_nextRowIsParent = true;  
        }  
        else  
        {  
            if (static_Input0_ProcessInputRow_nextRowIsParent)  
            {  
                // Current row contains parent record.   
                static_Input0_ProcessInputRow_parentCounter += 1;  
                this.ParentRecordsBuffer.AddRow();  
                this.ParentRecordsBuffer.ParentID = static_Input0_ProcessInputRow_parentCounter;  
                this.ParentRecordsBuffer.ParentRecord = Row.Column0;  
                static_Input0_ProcessInputRow_nextRowIsParent = false;  
            }  
            else  
            {  
                // Current row contains child record.   
                static_Input0_ProcessInputRow_childCounter += 1;  
                this.ChildRecordsBuffer.AddRow();  
                this.ChildRecordsBuffer.ChildID = static_Input0_ProcessInputRow_childCounter;  
                this.ChildRecordsBuffer.ParentID = static_Input0_ProcessInputRow_parentCounter;  
                this.ChildRecordsBuffer.ChildRecord = Row.Column0;  
            }  
        }  
  
    }  
```  
  
![Значок служб Integration Services (маленький)](../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services** <br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Создание синхронного преобразования с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
 [Создание асинхронного преобразования с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
  
  
