---
title: "Работа с файлами Excel с помощью задачи «скрипт» | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting-task-examples
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Excel files
- Script task [Integration Services], examples
- Excel [Integration Services]
ms.assetid: b8fa110a-2c9c-4f5a-8fe1-305555640e44
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 46bf53c35663393ad600f02600961cf0295386bf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="working-with-excel-files-with-the-script-task"></a>Работа с файлами Excel в задаче "Скрипт"
  Службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляют диспетчер соединений Excel, источник «Excel» и назначение «Excel» для работы с данными, хранящимися в электронных таблицах в формате [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel. Технологии, описанные в этом разделе, используют задачу «Скрипт» для получения сведений о доступных базах данных Excel (файлах книги) и таблицах (листах и именованных диапазонах). Эти образцы можно легко изменить для работы с любыми другими источниками данных на основе файлов, поддерживаемыми поставщиком OLE DB [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet.  
  
 [Настройка пакета для проверки образцов](#configuring)  
  
 [Пример 1: Проверьте, существует ли файл Excel](#example1)  
  
 [Пример 2: Проверка существования таблицы Excel](#example2)  
  
 [Пример 3: Получение списка файлов Excel в папке](#example3)  
  
 [Пример 4: Получение списка таблиц в файле Excel](#example4)  
  
 [Отображение результатов образцов](#testing)  
  
> [!NOTE]  
>  Если нужно создать задачу, которую будет удобно использовать в нескольких пакетах, рекомендуется начать разработку пользовательской задачи с этого образца задачи «Скрипт». Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
##  <a name="configuring"></a>Настройка пакета для проверки образцов  
 Для тестирования всех образцов этого раздела можно настроить отдельный пакет. В них используется много одинаковых переменных пакета и классов платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
#### <a name="to-configure-a-package-for-use-with-the-examples-in-this-topic"></a>Настройка пакета для использования с примерами этого раздела  
  
1.  Создайте новый проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] и откройте пакет по умолчанию для изменения.  
  
2.  **Переменные**. Откройте **переменных** окна и определите следующие переменные:  
  
    -   `ExcelFile`, типа **строка**. Введите полный путь и имя файла существующей книги Excel.  
  
    -   `ExcelTable`, типа **строка**. Введите имя существующего листа или именованного диапазона в книге, имя которой было указано в качестве значения переменной `ExcelFile`. Это значение учитывает регистр.  
  
    -   `ExcelFileExists`, типа **логическое**.  
  
    -   `ExcelTableExists`, типа **логическое**.  
  
    -   `ExcelFolder`, типа **строка**. Введите полный путь к папке, содержащей, по меньшей мере, одну книгу Excel.  
  
    -   `ExcelFiles`, типа **объекта**.  
  
    -   `ExcelTables`, типа **объекта**.  
  
3.  **Инструкции импорта**. Для большинства образцов кода необходимо импортировать одно из следующих пространств имен платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] либо оба пространства в начале файла скрипта:  
  
    -   **System.IO**, для операций файловой системы.  
  
    -   **System.Data.OleDb**, чтобы открыть файлы Excel как источников данных.  
  
4.  **Ссылки на**. Образцы кода, которые считывают данные схемы из файлов Excel требуется дополнительная ссылка на проект скрипта **System.Xml** пространства имен.  
  
5.  Значение по умолчанию языка скрипта для компонента скрипта с помощью **язык сценариев** параметр **Общие** страница **параметры** диалоговое окно. Дополнительные сведения см. в разделе [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
##  <a name="example1"></a>Описание для примера 1: Проверьте, существует ли файл Excel  
 В этом примере определяется, существует ли файл книги Excel, указанной в переменной `ExcelFile`, а затем присваивается логическое значение переменной `ExcelFileExists` в соответствии с результатом. С помощью этого логического значения можно реализовать ветвление в рабочем процессе пакета.  
  
#### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
1.  Добавьте в пакет новую задачу скрипта и измените ее имя на **ExcelFileExists**.  
  
2.  В **редактор задачи «скрипт»**на **сценарий** щелкните **ReadOnlyVariables** и введите значение свойства, с помощью одного из следующих методов:  
  
    -   Тип **ExcelFile**.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...** ) рядом с полем свойства и в **Выбор переменных** выберите **ExcelFile** переменной.  
  
3.  Нажмите кнопку **ReadWriteVariables** и введите значение свойства, с помощью одного из следующих методов:  
  
    -   Тип **ExcelFileExists**.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...** ) рядом с полем свойства и в **Выбор переменных** выберите **ExcelFileExists** переменной.  
  
4.  Нажмите кнопку **изменить скрипт** , чтобы открыть редактор скриптов.  
  
5.  Добавить **Imports** инструкции для **System.IO** пространства имен в верхней части файла скрипта.  
  
6.  Добавьте следующий код.  
  
### <a name="example-1-code"></a>Пример 1  
  
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
  
##  <a name="example2"></a>Описание примера 2: Проверка существования таблицы Excel  
 В этом примере определяется, существует ли лист или именованный диапазон Excel, указанный в переменной `ExcelTable`, в книге Excel, указанной в переменной `ExcelFile`, а затем присваивается логическое значение переменной `ExcelTableExists` в соответствии с результатом. С помощью этого логического значения можно реализовать ветвление в рабочем процессе пакета.  
  
#### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
1.  Добавьте в пакет новую задачу скрипта и измените ее имя на **ExcelTableExists**.  
  
2.  В **редактор задачи «скрипт»**на **сценарий** щелкните **ReadOnlyVariables** и введите значение свойства, с помощью одного из следующих методов:  
  
    -   Тип **ExcelTable** и **ExcelFile** через запятую**.**  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...** ) рядом с полем свойства и в **Выбор переменных** выберите **ExcelTable** и **ExcelFile** переменных.  
  
3.  Нажмите кнопку **ReadWriteVariables** и введите значение свойства, с помощью одного из следующих методов:  
  
    -   Тип **ExcelTableExists**.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...** ) рядом с полем свойства и в **Выбор переменных** выберите **ExcelTableExists** переменной.  
  
4.  Нажмите кнопку **изменить скрипт** , чтобы открыть редактор скриптов.  
  
5.  Добавьте ссылку на **System.Xml** сборки в проекте скрипта.  
  
6.  Добавить **Imports** инструкции для **System.IO** и **System.Data.OleDb** пространства имен в верхней части файла скрипта.  
  
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
      connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & fileToTest & _  
        ";Extended Properties=Excel 8.0"  
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
                connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + fileToTest + ";Extended Properties=Excel 8.0";  
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
  
##  <a name="example3"></a>Описание примера 3: Получение списка файлов Excel в папке  
 В этом примере массив заполняется списком файлов Excel, найденных в папке, которая была указана в качестве значения переменной `ExcelFolder`, а затем этот массив копируется в переменную `ExcelFiles`. Можно использовать перечислитель по объекту из переменной, чтобы выполнить итерацию по файлам в массиве.  
  
#### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
1.  Добавьте в пакет новую задачу скрипта и измените ее имя на **GetExcelFiles**.  
  
2.  Откройте **редактор задачи «скрипт»**на **сценарий** щелкните **ReadOnlyVariables** и введите значение свойства, с помощью одного из следующих методов:  
  
    -   Тип **ExcelFolder**  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...** ) рядом с полем свойства и в **Выбор переменных** диалогового окна выберите переменную ExcelFolder.  
  
3.  Нажмите кнопку **ReadWriteVariables** и введите значение свойства, с помощью одного из следующих методов:  
  
    -   Тип **ExcelFiles**.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...** ) рядом с полем свойства и в **Выбор переменных** диалогового окна выберите переменную ExcelFiles.  
  
4.  Нажмите кнопку **изменить скрипт** , чтобы открыть редактор скриптов.  
  
5.  Добавить **Imports** инструкции для **System.IO** пространства имен в верхней части файла скрипта.  
  
6.  Добавьте следующий код.  
  
### <a name="example-3-code"></a>Пример 3  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const FILE_PATTERN As String = "*.xls"  
  
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
    const string FILE_PATTERN = "*.xls";  
  
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
 Вместо того чтобы использовать задачу «Скрипт» для сбора списка файлов Excel в массив, можно применить перечислитель с циклом по каждому файлу для выполнения итерации по всем файлам Excel в папке. Дополнительные сведения см. в разделе [цикла по файлам Excel и таблицы с использованием контейнер цикла Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md).  
  
##  <a name="example4"></a>Описание примера 4: Получение списка таблиц в файл Excel  
 В этом примере массив заполняется списком листов и именованных диапазонов, найденных в файле книги Excel, которая была указана в переменной `ExcelFile`, а затем этот массив копируется в переменную `ExcelTables`. Можно использовать перечислитель по объекту из переменной, чтобы выполнить итерацию по таблицам в массиве.  
  
> [!NOTE]  
>  Список таблиц в книге Excel включает в себя и листы (которые имеют суффикс $), и именованные диапазоны. Если нужно отфильтровать список только по листам или только по именованным диапазонам, то, возможно, понадобится добавить дополнительный код.  
  
#### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
1.  Добавьте в пакет новую задачу скрипта и измените ее имя на **GetExcelTables**.  
  
2.  Откройте **редактор задачи «скрипт»**на **сценарий** щелкните **ReadOnlyVariables** и введите значение свойства, с помощью одного из следующих методов:  
  
    -   Тип **ExcelFile**.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...** ) рядом с полем свойства и в **Выбор переменных** диалогового окна выберите переменную ExcelFile.  
  
3.  Нажмите кнопку **ReadWriteVariables** и введите значение свойства, с помощью одного из следующих методов:  
  
    -   Тип **ExcelTables**.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...** ) рядом с полем свойства и в **Выбор переменных** диалогового окна выберите ExcelTablesvariable.  
  
4.  Нажмите кнопку **изменить скрипт** , чтобы открыть редактор скриптов.  
  
5.  Добавьте ссылку на **System.Xml** пространства имен в проекте скрипта.  
  
6.  Добавить **Imports** инструкции для **System.Data.OleDb** пространства имен в верхней части файла скрипта.  
  
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
    connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & excelFile & _  
        ";Extended Properties=Excel 8.0"  
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
            connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + excelFile + ";Extended Properties=Excel 8.0";  
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
 Вместо того чтобы использовать задачу «Скрипт» для сбора списка таблиц Excel в массив, можно применить перечислитель по набору строк схемы ADO.NET для перебора всех таблиц (т.е. листов и именованных диапазонов) в файле книги Excel. Дополнительные сведения см. в разделе [цикла по файлам Excel и таблицы с использованием контейнер цикла Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md).  
  
##  <a name="testing"></a>Отображение результатов образцов  
 Если все образцы в этом разделе были настроены для использования с одним пакетом, можно соединить все задачи «Скрипт» с дополнительной задачей «Скрипт», отображающей выход всех образцов.  
  
#### <a name="to-configure-a-script-task-to-display-the-output-of-the-examples-in-this-topic"></a>Настройка задачи «Скрипт» для отображения выхода всех образцов в этом разделе  
  
1.  Добавьте в пакет новую задачу скрипта и измените ее имя на **DisplayResults**.  
  
2.  Подключаться каждый из четырех задач «скрипт» друг с другом, чтобы каждая задача выполнялась после успешного завершения предыдущей и четвертого образца с задачей **DisplayResults** задачи.  
  
3.  Откройте **DisplayResults** задач в **редактор задачи «скрипт»**.  
  
4.  На **сценарий** щелкните **ReadOnlyVariables** и используйте один из следующих методов для добавления все семь переменных, перечисленных в [Настройка пакета для проверки образцов](#configuring):  
  
    -   Введите имена переменных, разделенные запятыми.  
  
         -или-  
  
    -   Нажмите кнопку с многоточием (**...** ) рядом с полем свойства и в **Выбор переменных** диалоговое окно, выберите переменные.  
  
5.  Нажмите кнопку **изменить скрипт** , чтобы открыть редактор скриптов.  
  
6.  Добавить **Imports** инструкции для **Microsoft.VisualBasic** и **System.Windows.Forms** пространства имен в верхней части файла скрипта.  
  
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
 [Диспетчер соединений с Excel](../../integration-services/connection-manager/excel-connection-manager.md)   
 [Просмотр файлов и таблиц Excel с помощью контейнера «цикл по каждому элементу»](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  

