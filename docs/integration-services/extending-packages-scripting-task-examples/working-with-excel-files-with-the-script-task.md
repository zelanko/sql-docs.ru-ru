---
title: Работа с файлами Excel в задаче "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 05/15/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Excel files
- Script task [Integration Services], examples
- Excel [Integration Services]
ms.assetid: b8fa110a-2c9c-4f5a-8fe1-305555640e44
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e39c96672016f19ecc6506d48266da70e0edf1b5
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58274882"
---
# <a name="working-with-excel-files-with-the-script-task"></a>Работа с файлами Excel в задаче "Скрипт"
  Службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляют диспетчер соединений Excel, источник «Excel» и назначение «Excel» для работы с данными, хранящимися в электронных таблицах в формате [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel. Технологии, описанные в этом разделе, используют задачу «Скрипт» для получения сведений о доступных базах данных Excel (файлах книги) и таблицах (листах и именованных диапазонах).
  
> [!IMPORTANT]
> Дополнительные сведения о подключении к файлам Excel, а также об ограничениях и известных проблемах, связанных с загрузкой данных в файлы этого приложения и из них, см. в разделе [Загрузка данных в приложение Excel или из него с помощью служб SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md).
 
> [!TIP]  
>  Если нужно создать задачу, которую будет удобно использовать в нескольких пакетах, рекомендуется начать разработку пользовательской задачи с этого образца задачи "Скрипт". Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  

##  <a name="configuring"></a> Настройка пакета для проверки образцов  
 Для тестирования всех образцов этого раздела можно настроить отдельный пакет. В них используется много одинаковых переменных пакета и классов платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
### <a name="to-configure-a-package-for-use-with-the-examples-in-this-topic"></a>Настройка пакета для использования с примерами этого раздела  
  
1.  Создайте новый проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] и откройте пакет по умолчанию для изменения.  
  
2.  **Переменные**. Откройте окно **Переменные** и определите следующие переменные:  
  
    -   `ExcelFile`, тип **String**. Введите полный путь и имя файла существующей книги Excel.  
  
    -   `ExcelTable`, тип **String**. Введите имя существующего листа или именованного диапазона в книге, имя которой было указано в качестве значения переменной `ExcelFile`. Это значение учитывает регистр.  
  
    -   `ExcelFileExists`, тип **Boolean**.  
  
    -   `ExcelTableExists`, тип **Boolean**.  
  
    -   `ExcelFolder`, тип **String**. Введите полный путь к папке, содержащей, по меньшей мере, одну книгу Excel.  
  
    -   `ExcelFiles`, тип **Object**.  
  
    -   `ExcelTables`, тип **Object**.  
  
3.  **Инструкции импорта**. Для большинства образцов кода необходимо импортировать одно из следующих пространств имен платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] либо оба пространства в начале файла скрипта:  
  
    -   **System.IO** для операций с файловой системой.  
  
    -   **System.Data.OleDb** для открытия файлов Excel как источников данных.  
  
4.  **Ссылки**. Для образцов кода, выполняющих чтение данных схемы из файлов Excel, в проекте скрипта требуется дополнительная ссылка на пространство имен **System.Xml**.  
  
5.  Установите язык скрипта по умолчанию для компонента скрипта, воспользовавшись параметром **Язык скрипта** страницы **Общие** диалогового окна **Параметры**. Дополнительные сведения см. в разделе [General Page](../general-page-of-integration-services-designers-options.md).  
  
##  <a name="example1"></a> Описание примера 1. Проверка существования файла Excel  
 В этом примере определяется, существует ли файл книги Excel, указанной в переменной `ExcelFile`, а затем присваивается логическое значение переменной `ExcelFileExists` в соответствии с результатом. С помощью этого логического значения можно реализовать ветвление в рабочем процессе пакета.  
  
### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
1.  Добавьте в пакет новую задачу "Скрипт" и измените ее имя на **ExcelFileExists**.  
  
2.  В **редакторе задачи "Скрипт"** на вкладке **Скрипт** щелкните свойство **ReadOnlyVariables** и введите значение свойства одним из следующих способов:  
  
    -   Введите **ExcelFile**.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...**) рядом с полем свойства и в диалоговом окне **Выбор переменных** выберите переменную **ExcelFile**.  
  
3.  Щелкните свойство **ReadWriteVariables** и введите значение свойства одним из следующих способов:  
  
    -   Введите **ExcelFileExists**.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...**) рядом с полем свойства и в диалоговом окне **Выбор переменных** выберите переменную **ExcelFileExists**.  
  
4.  Нажмите кнопку **Изменить скрипт**, чтобы открыть редактор скриптов.  
  
5.  В верхней части файла скрипта добавьте инструкцию **Imports** для пространства имен **System.IO**.  
  
6.  Добавьте следующий код.  
  
### <a name="example-1-code"></a>Код примера 1  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    If File.Exists(fileToTest) Then  
      Dts.Variables("ExcelFileExists").Value = True  
    Else  
      Dts.Variables("ExcelFileExists").Value = False  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    string fileToTest;  
  
    fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
    if (File.Exists(fileToTest))  
    {  
      Dts.Variables["ExcelFileExists"].Value = true;  
    }  
    else  
    {  
      Dts.Variables["ExcelFileExists"].Value = false;  
    }  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
##  <a name="example2"></a> Описание примера 2. Проверка существования таблицы Excel  
 В этом примере определяется, существует ли лист или именованный диапазон Excel, указанный в переменной `ExcelTable`, в книге Excel, указанной в переменной `ExcelFile`, а затем присваивается логическое значение переменной `ExcelTableExists` в соответствии с результатом. С помощью этого логического значения можно реализовать ветвление в рабочем процессе пакета.  
  
### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
1.  Добавьте в пакет новую задачу "Скрипт" и измените ее имя на **ExcelTableExists**.  
  
2.  В **редакторе задачи "Скрипт"** на вкладке **Скрипт** щелкните свойство **ReadOnlyVariables** и введите значение свойства одним из следующих способов:  
  
    -   Введите значения **ExcelTable** и **ExcelFile**, разделенные запятыми **.**  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...**) рядом с полем свойства и в диалоговом окне **Выбор переменных** выберите переменные **ExcelTable** и **ExcelFile**.  
  
3.  Щелкните свойство **ReadWriteVariables** и введите значение свойства одним из следующих способов:  
  
    -   Введите **ExcelTableExists**.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...**) рядом с полем свойства и в диалоговом окне **Выбор переменных** выберите переменную **ExcelTableExists**.  
  
4.  Нажмите кнопку **Изменить скрипт**, чтобы открыть редактор скриптов.  
  
5.  Добавьте ссылку на сборку **System.Xml** в проект скрипта.  
  
6.  В верхней части файла скрипта добавьте инструкции **Imports** для пространств имен **System.IO** и **System.Data.OleDb**.  
  
7.  Добавьте следующий код.  
  
### <a name="example-2-code"></a>Код примера 2  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
    Dim tableToTest As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim excelTables As DataTable  
    Dim excelTable As DataRow  
    Dim currentTable As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    tableToTest = Dts.Variables("ExcelTable").Value.ToString  
  
    Dts.Variables("ExcelTableExists").Value = False  
    If File.Exists(fileToTest) Then  
      connectionString = "Provider=Microsoft.ACE.OLEDB.12.0;" & _  
        "Data Source=" & fileToTest & _  
        ";Extended Properties=Excel 12.0"  
      excelConnection = New OleDbConnection(connectionString)  
      excelConnection.Open()  
      excelTables = excelConnection.GetSchema("Tables")  
      For Each excelTable In excelTables.Rows  
        currentTable = excelTable.Item("TABLE_NAME").ToString  
        If currentTable = tableToTest Then  
          Dts.Variables("ExcelTableExists").Value = True  
        End If  
      Next  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
    public void Main()  
        {  
            string fileToTest;  
            string tableToTest;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable excelTables;  
            string currentTable;  
  
            fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
            tableToTest = Dts.Variables["ExcelTable"].Value.ToString();  
  
            Dts.Variables["ExcelTableExists"].Value = false;  
            if (File.Exists(fileToTest))  
            {  
                connectionString = "Provider=Microsoft.ACE.OLEDB.12.0;" +  
                "Data Source=" + fileToTest + ";Extended Properties=Excel 12.0";  
                excelConnection = new OleDbConnection(connectionString);  
                excelConnection.Open();  
                excelTables = excelConnection.GetSchema("Tables");  
                foreach (DataRow excelTable in excelTables.Rows)  
                {  
                    currentTable = excelTable["TABLE_NAME"].ToString();  
                    if (currentTable == tableToTest)  
                    {  
                        Dts.Variables["ExcelTableExists"].Value = true;  
                    }  
                }  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
}  
```  
  
##  <a name="example3"></a> Описание примера 3. Получение списка файлов Excel в папке  
 В этом примере массив заполняется списком файлов Excel, найденных в папке, которая была указана в качестве значения переменной `ExcelFolder`, а затем этот массив копируется в переменную `ExcelFiles`. Можно использовать перечислитель по объекту из переменной, чтобы выполнить итерацию по файлам в массиве.  
  
### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
1.  Добавьте в пакет новую задачу "Скрипт" и измените ее имя на **GetExcelFiles**.  
  
2.  В **редакторе задачи "Скрипт"** на вкладке **Скрипт** щелкните свойство **ReadOnlyVariables** и введите значение свойства одним из следующих способов:  
  
    -   Введите **ExcelFolder**  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...**) рядом с полем свойства и в диалоговом окне **Выбор переменных** выберите переменную ExcelFolder.  
  
3.  Щелкните свойство **ReadWriteVariables** и введите значение свойства одним из следующих способов:  
  
    -   Введите **ExcelFiles**.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...**) рядом с полем свойства и в диалоговом окне **Выбор переменных** выберите переменную ExcelFiles.  
  
4.  Нажмите кнопку **Изменить скрипт**, чтобы открыть редактор скриптов.  
  
5.  В верхней части файла скрипта добавьте инструкцию **Imports** для пространства имен **System.IO**.  
  
6.  Добавьте следующий код.  
  
### <a name="example-3-code"></a>Пример кода 3  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const FILE_PATTERN As String = "*.xlsx"  
  
    Dim excelFolder As String  
    Dim excelFiles As String()  
  
    excelFolder = Dts.Variables("ExcelFolder").Value.ToString  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN)  
  
    Dts.Variables("ExcelFiles").Value = excelFiles  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    const string FILE_PATTERN = "*.xlsx";  
  
    string excelFolder;  
    string[] excelFiles;  
  
    excelFolder = Dts.Variables["ExcelFolder"].Value.ToString();  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN);  
  
    Dts.Variables["ExcelFiles"].Value = excelFiles;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
### <a name="alternate-solution"></a>Альтернативное решение  
 Вместо того чтобы использовать задачу «Скрипт» для сбора списка файлов Excel в массив, можно применить перечислитель с циклом по каждому файлу для выполнения итерации по всем файлам Excel в папке. Дополнительные сведения см. в разделе [Просмотр файлов и таблиц Excel с помощью контейнера "цикл по каждому элементу"](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md).  
  
##  <a name="example4"></a> Описание примера 4. Получение списка таблиц в файле Excel  
 В этом примере массив заполняется списком листов и именованных диапазонов, найденных в файле книги Excel, которая была указана в переменной `ExcelFile`, а затем этот массив копируется в переменную `ExcelTables`. Можно использовать перечислитель по объекту из переменной, чтобы выполнить итерацию по таблицам в массиве.  
  
> [!NOTE]  
>  Список таблиц в книге Excel включает в себя и листы (которые имеют суффикс $), и именованные диапазоны. Если нужно отфильтровать список только по листам или только по именованным диапазонам, то, возможно, понадобится добавить дополнительный код.  
  
### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
1.  Добавьте в пакет новую задачу "Скрипт" и измените ее имя на **GetExcelTables**.  
  
2.  В **редакторе задачи "Скрипт"** на вкладке **Скрипт** щелкните свойство **ReadOnlyVariables** и введите значение свойства одним из следующих способов:  
  
    -   Введите **ExcelFile**.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...**) рядом с полем свойства и в диалоговом окне **Выбор переменных** выберите переменную ExcelFile.  
  
3.  Щелкните свойство **ReadWriteVariables** и введите значение свойства одним из следующих способов:  
  
    -   Введите **ExcelTables**.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...**) рядом с полем свойства и в диалоговом окне **Выбор переменных** выберите переменную ExcelTablesvariable.  
  
4.  Нажмите кнопку **Изменить скрипт**, чтобы открыть редактор скриптов.  
  
5.  Добавьте ссылку на пространство имен **System.Xml** в проект скрипта.  
  
6.  В верхней части файла скрипта добавьте инструкцию **Imports** для пространства имен **System.Data.OleDb**.  
  
7.  Добавьте следующий код.  
  
### <a name="example-4-code"></a>Код примера 4  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim excelFile As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim tablesInFile As DataTable  
    Dim tableCount As Integer = 0  
    Dim tableInFile As DataRow  
    Dim currentTable As String  
    Dim tableIndex As Integer = 0  
  
    Dim excelTables As String()  
  
    excelFile = Dts.Variables("ExcelFile").Value.ToString  
    connectionString = "Provider=Microsoft.ACE.OLEDB.12.0;" & _  
        "Data Source=" & excelFile & _  
        ";Extended Properties=Excel 12.0"  
    excelConnection = New OleDbConnection(connectionString)  
    excelConnection.Open()  
    tablesInFile = excelConnection.GetSchema("Tables")  
    tableCount = tablesInFile.Rows.Count  
    ReDim excelTables(tableCount - 1)  
    For Each tableInFile In tablesInFile.Rows  
      currentTable = tableInFile.Item("TABLE_NAME").ToString  
      excelTables(tableIndex) = currentTable  
      tableIndex += 1  
    Next  
  
    Dts.Variables("ExcelTables").Value = excelTables  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            string excelFile;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable tablesInFile;  
            int tableCount = 0;  
            string currentTable;  
            int tableIndex = 0;  
  
            string[] excelTables = new string[5];  
  
            excelFile = Dts.Variables["ExcelFile"].Value.ToString();  
            connectionString = "Provider=Microsoft.ACE.OLEDB.12.0;" +  
                "Data Source=" + excelFile + ";Extended Properties=Excel 12.0";  
            excelConnection = new OleDbConnection(connectionString);  
            excelConnection.Open();  
            tablesInFile = excelConnection.GetSchema("Tables");  
            tableCount = tablesInFile.Rows.Count;  
  
            foreach (DataRow tableInFile in tablesInFile.Rows)  
            {  
                currentTable = tableInFile["TABLE_NAME"].ToString();  
                excelTables[tableIndex] = currentTable;  
                tableIndex += 1;  
            }  
  
            Dts.Variables["ExcelTables"].Value = excelTables;  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
### <a name="alternate-solution"></a>Альтернативное решение  
 Вместо того чтобы использовать задачу «Скрипт» для сбора списка таблиц Excel в массив, можно применить перечислитель по набору строк схемы ADO.NET для перебора всех таблиц (т.е. листов и именованных диапазонов) в файле книги Excel. Дополнительные сведения см. в разделе [Просмотр файлов и таблиц Excel с помощью контейнера "цикл по каждому элементу"](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md).  
  
##  <a name="testing"></a> Отображение результатов образцов  
 Если все образцы в этом разделе были настроены для использования с одним пакетом, можно соединить все задачи «Скрипт» с дополнительной задачей «Скрипт», отображающей выход всех образцов.  
  
### <a name="to-configure-a-script-task-to-display-the-output-of-the-examples-in-this-topic"></a>Настройка задачи «Скрипт» для отображения выхода всех образцов в этом разделе  
  
1.  Добавьте в пакет новую задачу "Скрипт" и измените ее имя на **DisplayResults**.  
  
2.  Соедините каждую задачу "Скрипт" всех четырех образцов друг с другом, чтобы каждая задача выполнялась после успешного завершения предыдущей, и соедините задачу четвертого образца с задачей **DisplayResults**.  
  
3.  Откройте задачу **DisplayResults** в **редакторе задачи "Скрипт"**.  
  
4.  На вкладке **Скрипт** щелкните **ReadOnlyVariables** и используйте один из следующих методов, чтобы добавить все семь переменных, перечисленных в разделе [Настройка пакета для тестирования образцов](#configuring):  
  
    -   Введите имена переменных, разделенные запятыми.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...**) рядом с полем свойства и в диалоговом окне **Выбор переменных** выберите переменные.  
  
5.  Нажмите кнопку **Изменить скрипт**, чтобы открыть редактор скриптов.  
  
6.  В верхней части файла скрипта добавьте инструкции **Imports** для пространств имен **Microsoft.VisualBasic** и **System.Windows.Forms**.  
  
7.  Добавьте следующий код.  
  
8.  Выполните пакет и просмотрите результаты, отобразившиеся в окне сообщения.  
  
### <a name="code-to-display-the-results"></a>Код для отображения результатов  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const EOL As String = ControlChars.CrLf  
  
    Dim results As String  
    Dim filesInFolder As String()  
    Dim fileInFolder As String  
    Dim tablesInFile As String()  
    Dim tableInFile As String  
  
    results = _  
      "Final values of variables:" & EOL & _  
      "ExcelFile: " & Dts.Variables("ExcelFile").Value.ToString & EOL & _  
      "ExcelFileExists: " & Dts.Variables("ExcelFileExists").Value.ToString & EOL & _  
      "ExcelTable: " & Dts.Variables("ExcelTable").Value.ToString & EOL & _  
      "ExcelTableExists: " & Dts.Variables("ExcelTableExists").Value.ToString & EOL & _  
      "ExcelFolder: " & Dts.Variables("ExcelFolder").Value.ToString & EOL & _  
      EOL  
  
    results &= "Excel files in folder: " & EOL  
    filesInFolder = DirectCast(Dts.Variables("ExcelFiles").Value, String())  
    For Each fileInFolder In filesInFolder  
      results &= " " & fileInFolder & EOL  
    Next  
    results &= EOL  
  
    results &= "Excel tables in file: " & EOL  
    tablesInFile = DirectCast(Dts.Variables("ExcelTables").Value, String())  
    For Each tableInFile In tablesInFile  
      results &= " " & tableInFile & EOL  
    Next  
  
    MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information)  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            const string EOL = "\r";  
  
            string results;  
            string[] filesInFolder;  
            //string fileInFolder;  
            string[] tablesInFile;  
            //string tableInFile;  
  
            results = "Final values of variables:" + EOL + "ExcelFile: " + Dts.Variables["ExcelFile"].Value.ToString() + EOL + "ExcelFileExists: " + Dts.Variables["ExcelFileExists"].Value.ToString() + EOL + "ExcelTable: " + Dts.Variables["ExcelTable"].Value.ToString() + EOL + "ExcelTableExists: " + Dts.Variables["ExcelTableExists"].Value.ToString() + EOL + "ExcelFolder: " + Dts.Variables["ExcelFolder"].Value.ToString() + EOL + EOL;  
  
            results += "Excel files in folder: " + EOL;  
            filesInFolder = (string[])(Dts.Variables["ExcelFiles"].Value);  
            foreach (string fileInFolder in filesInFolder)  
            {  
                results += " " + fileInFolder + EOL;  
            }  
            results += EOL;  
  
            results += "Excel tables in file: " + EOL;  
            tablesInFile = (string[])(Dts.Variables["ExcelTables"].Value);  
            foreach (string tableInFile in tablesInFile)  
            {  
                results += " " + tableInFile + EOL;  
            }  
  
            MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Загрузка данных в приложение Excel или из него с помощью служб SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md)  
 [Просмотр файлов и таблиц Excel с помощью контейнера «цикл по каждому элементу»](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  
