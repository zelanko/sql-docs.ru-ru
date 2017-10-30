---
title: "Загрузка выхода локального пакета | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow [Integration Services], loading results
- loading data flow results
ms.assetid: aba8ecb7-0dcf-40d0-a2a8-64da0da94b93
caps.latest.revision: 66
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 41de742c987d9f043f3dd247ee84af6a3eaf365b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="loading-the-output-of-a-local-package"></a>Загрузка выхода локального пакета
  Клиентские приложения могут читать выходные данные [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакетов при сохранении выходные данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначения с помощью [!INCLUDE[vstecado](../../includes/vstecado-md.md)], или когда выходные данные сохраняются в неструктурированный файл с помощью классов в **System.IO** пространства имен. Кроме того, клиентское приложение может считывать выход пакета непосредственно из памяти, без необходимости промежуточного шага для сохранения данных. Это решение лежат **Microsoft.SqlServer.Dts.DtsClient** пространства имен, которое содержит специализированные реализации **IDbConnection**, **IDbCommand**, и **IDbDataParameter** интерфейсы из **System.Data** пространства имен. Сборка Microsoft.SqlServer.Dts.DtsClient.dll устанавливается по умолчанию в **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.  
  
> [!NOTE]  
>  Процедуры, описанной в этом разделе необходимо, свойства DelayValidation задачи потока данных и любых родительских объектов было присвоено значение по умолчанию **False**.  
  
## <a name="description"></a>Description  
 В этой процедуре демонстрируется, как разработать на управляемом коде клиентское приложение, которое загружает выход пакета с назначением DataReader непосредственно из памяти. Описанные здесь шаги демонстрируются в следующем образце кода.  
  
#### <a name="to-load-data-package-output-into-a-client-application"></a>Загрузка данных с выхода пакета в клиентское приложение  
  
1.  В пакете настройте назначение DataReader для получения выхода, который необходимо считать в клиентском приложении. Дайте назначению DataReader описательное имя, поскольку оно понадобится в дальнейшем для использования в клиентском приложении. Запомните имя назначения DataReader.  
  
2.  В проекте разработки необходимо задать ссылку на **Microsoft.SqlServer.Dts.DtsClient** пространства имен, найдя сборку **Microsoft.SqlServer.Dts.DtsClient.dll**. По умолчанию эта сборка устанавливается в **C:\Program Files\Microsoft SQL Server\100\DTS\Binn**. Импорт пространства имен в коде на языке C# **использование** или [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] **Imports** инструкции.  
  
3.  В коде создайте объект типа **DtsClient.DtsConnection** со строкой соединения, который содержит параметры командной строки, необходимые для **dtexec.exe** для запуска пакета. Дополнительные сведения см. в статье [dtexec Utility](../../integration-services/packages/dtexec-utility.md). Затем откройте соединение с помощью этой строки подключения. Можно также использовать **dtexecui** программы для визуального создания необходимой строки подключения.  
  
    > [!NOTE]  
    >  В образце кода демонстрируется загрузка пакета из файловой системы с использованием синтаксиса `/FILE <path and filename>`. Однако можно также загрузить пакет из базы данных MSDB с помощью синтаксиса `/SQL <package name>` или из хранилища пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с помощью синтаксиса `/DTS \<folder name>\<package name>`.  
  
4.  Создайте объект типа **DtsClient.DtsCommand** , использующий ранее созданный **DtsConnection** и задайте его **CommandText** на имя назначения DataReader назначения в пакете. Затем вызовите **ExecuteReader** метод объекта команды, чтобы загрузить результаты пакета в новое назначение DataReader.  
  
5.  При необходимости можно косвенно параметризовать выход пакета с помощью коллекции **DtsDataParameter** объектов на **DtsCommand** объектов для передачи значений в переменных, определенных в пакете. В рамках пакета можно использовать эти переменные в качестве параметров запроса или в выражениях для воздействия на результаты, возвращаемые в назначение DataReader. Необходимо определить эти переменные в пакете в **DtsClient** пространства имен, прежде чем использовать их с **DtsDataParameter** объекта из клиентского приложения. (Может потребоваться щелкните **Выбор столбцов переменных** кнопки панели инструментов в **переменных** окно для отображения **имен** столбца.) В коде клиента, при добавлении **DtsDataParameter** для **параметры** коллекцию **DtsCommand**, пропустите DtsClient ссылку на пространство имен из имени переменной . Например:  
  
    ```  
    command.Parameters.Add(new DtsDataParameter("MyVariable", 1));  
    ```  
  
6.  Вызовите **чтения** метод назначения DataReader повторно по мере необходимости для прохождения цикла по строкам выходных данных. Используйте эти данные или сохраните их для дальнейшего использования в клиентском приложении.  
  
    > [!IMPORTANT]  
    >  **Чтения** метод этой реализации назначения DataReader возвращает **true** еще раз после считывания последней строки данных. Это затрудняет использование обычного кода, который выполняет цикл по назначению DataReader, пока **чтения** возвращает **true**. Если в коде предпринимается попытка закрыть назначение DataReader или соединение после считывания ожидаемого числа строк, без дополнительного итогового вызова для **чтения** метод, код будет выдано необработанное исключение. Тем не менее, если код пытается выполнить чтение данных в этой последней итерации по циклу, когда **чтения** по-прежнему возвращает **true** , но был передан последней строки, будет выдано необработанное  **ApplicationException** с сообщением, «объект IDataReader служб SSIS находится за пределами результирующего набора.» Это поведение отличается от остальных реализаций назначения DataReader. Таким образом при использовании цикла для считывания строк в назначении DataReader, когда **чтения** возвращает **true**, необходимо написать код для захвата, тестирования и отмены ожидаемого исключения  **ApplicationException** на последнего успешного вызова **чтения** метод. Или, если заранее известно число ожидаемых строк, можно обработать строки, а затем вызвать **чтения** еще раз перед закрытием назначения DataReader и соединения.  
  
7.  Вызовите **Dispose** метод **DtsCommand** объекта. Это особенно важно при использовании любого **DtsDataParameter** объектов.  
  
8.  Закройте назначение DataReader и объекты соединения.  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется пакет, который вычисляет единственное статистическое значение и сохраняет его в назначение DataReader, а затем считывает значение из DataReader и отображает его в текстовом поле в форме Windows.  
  
 Использование параметров не требуется при загрузке выхода пакета в клиентское приложение. Если вы не хотите использовать параметр, можно опустить использование переменной в **DtsClient** пространства имен, а также код, использующий **DtsDataParameter** объекта.  
  
#### <a name="to-create-the-test-package"></a>Создание тестового пакета  
  
1.  Создайте новый пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В образце кода в качестве имени пакета используется «DtsClientWParamPkg.dtsx».  
  
2.  Добавьте переменную типа String в пространство имен DtsClient. В образце кода в качестве имени переменной используется «Country». (Может потребоваться щелкните **Выбор столбцов переменных** кнопки панели инструментов в **переменных** окно для отображения **имен** столбца.)  
  
3.  Добавьте диспетчер соединений OLE DB, соединяющийся с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
4.  Добавьте задачу потока данных в пакет и переключитесь в область конструктора потока данных.  
  
5.  Добавьте источник OLE DB в поток данных и настройте его для использования ранее созданного диспетчера соединений OLE DB, затем выполните следующую команду SQL:  
  
    ```  
    SELECT * FROM Sales.vIndividualCustomer WHERE CountryRegionName = ?  
    ```  
  
6.  Нажмите кнопку **параметры** и в **Установка параметров запроса** диалоговое окно сопоставьте единственный входной параметр в запросе, Parameter0, с переменной DtsClient::Country.  
  
7.  Добавьте преобразование «Статистическая обработка» в поток данных и соедините выход источника OLE DB с этим преобразованием. Откройте редактор преобразования «Статистическая обработка» и настройте его для выполнения операции «Count all» для всех входных столбцов (*) и для вывода статистического значения с псевдонимом CustomerCount.  
  
8.  Добавьте назначение DataReader в поток данных и соедините выход преобразования «Статистическая обработка» с назначением DataReader. В образце кода в качестве имени назначения DataReader используется «DataReaderDest». Укажите единственный доступный входной столбец, CustomerCount, в качестве назначения.  
  
9. Сохраните пакет. Тестовое приложение, которое создается далее, выполнит пакет и извлечет его выход непосредственно из памяти.  
  
#### <a name="to-create-the-test-application"></a>Создание тестового приложения  
  
1.  Создайте новое приложение Windows Forms.  
  
2.  Добавьте ссылку на **Microsoft.SqlServer.Dts.DtsClient** пространства имен, перейдя к сборке с тем же именем в **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.  
  
3.  Скопируйте и вставьте следующий образец кода в программный модуль формы.  
  
4.  Изменить значение **dtexecArgs** переменной при необходимости чтобы оно содержало параметры командной строки, необходимые для **dtexec.exe** для запуска пакета. В образце кода пакет загружается из файловой системы.  
  
5.  Изменить значение **dataReaderName** переменной при необходимости чтобы оно содержало имя назначения DataReader в пакете.  
  
6.  Поместите в форму кнопку и текстовое поле. В примере кода используется **btnRun** как имя кнопки и **txtResults** как имя текстового поля.  
  
7.  Запустите приложение и нажмите кнопку. После небольшой паузы, связанной с выполнением пакета, статистическое значение, вычисленное пакетом (количество клиентов в Канаде), должно отобразиться в текстовом поле формы.  
  
### <a name="sample-code"></a>Образец кода  
  
```vb  
Imports System.Data  
Imports Microsoft.SqlServer.Dts.DtsClient  
  
Public Class Form1  
  
  Private Sub btnRun_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRun.Click  
  
    Dim dtexecArgs As String  
    Dim dataReaderName As String  
    Dim countryName As String  
  
    Dim dtsConnection As DtsConnection  
    Dim dtsCommand As DtsCommand  
    Dim dtsDataReader As IDataReader  
    Dim dtsParameter As DtsDataParameter  
  
    Windows.Forms.Cursor.Current = Cursors.WaitCursor  
  
    dtexecArgs = "/FILE ""C:\...\DtsClientWParamPkg.dtsx"""  
    dataReaderName = "DataReaderDest"  
    countryName = "Canada"  
  
    dtsConnection = New DtsConnection()  
    With dtsConnection  
      .ConnectionString = dtexecArgs  
      .Open()  
    End With  
  
    dtsCommand = New DtsCommand(dtsConnection)  
    dtsCommand.CommandText = dataReaderName  
  
    dtsParameter = New DtsDataParameter("Country", DbType.String)  
    dtsParameter.Direction = ParameterDirection.Input  
    dtsCommand.Parameters.Add(dtsParameter)  
  
    dtsParameter.Value = countryName  
  
    dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default)  
  
    With dtsDataReader  
      .Read()  
      txtResults.Text = .GetInt32(0).ToString("N0")  
    End With  
  
    'After reaching the end of data rows,  
    ' call the Read method one more time.  
    Try  
      dtsDataReader.Read()  
    Catch ex As Exception  
      MessageBox.Show("Exception on final call to Read method:" & ControlChars.CrLf & _  
      ex.Message & ControlChars.CrLf & _  
      ex.InnerException.Message, "Exception on final call to Read method", _  
      MessageBoxButtons.OK, MessageBoxIcon.Error)  
    End Try  
  
    ' The following method is a best practice, and is  
    '  required when using DtsDataParameter objects.  
    dtsCommand.Dispose()  
  
    Try  
      dtsDataReader.Close()  
    Catch ex As Exception  
      MessageBox.Show("Exception closing DataReader:" & ControlChars.CrLf & _  
      ex.Message & ControlChars.CrLf & _  
      ex.InnerException.Message, "Exception closing DataReader", _  
      MessageBoxButtons.OK, MessageBoxIcon.Error)  
    End Try  
  
    Try  
      dtsConnection.Close()  
    Catch ex As Exception  
      MessageBox.Show("Exception closing connection:" & ControlChars.CrLf & _  
      ex.Message & ControlChars.CrLf & _  
      ex.InnerException.Message, "Exception closing connection", _  
      MessageBoxButtons.OK, MessageBoxIcon.Error)  
    End Try  
  
    Windows.Forms.Cursor.Current = Cursors.Default  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Data;  
using Microsoft.SqlServer.Dts.DtsClient;  
  
namespace DtsClientWParamCS  
{  
  public partial class Form1 : Form  
  {  
    public Form1()  
    {  
      InitializeComponent();  
      this.btnRun.Click += new System.EventHandler(this.btnRun_Click);  
    }  
  
    private void btnRun_Click(object sender, EventArgs e)  
    {  
      string dtexecArgs;  
      string dataReaderName;  
      string countryName;  
  
      DtsConnection dtsConnection;  
      DtsCommand dtsCommand;  
      IDataReader dtsDataReader;  
      DtsDataParameter dtsParameter;  
  
      Cursor.Current = Cursors.WaitCursor;  
  
      dtexecArgs = @"/FILE ""C:\...\DtsClientWParamPkg.dtsx""";  
      dataReaderName = "DataReaderDest";  
      countryName = "Canada";  
  
      dtsConnection = new DtsConnection();  
      {  
        dtsConnection.ConnectionString = dtexecArgs;  
        dtsConnection.Open();  
      }  
  
      dtsCommand = new DtsCommand(dtsConnection);  
      dtsCommand.CommandText = dataReaderName;  
  
      dtsParameter = new DtsDataParameter("Country", DbType.String);  
      dtsParameter.Direction = ParameterDirection.Input;  
      dtsCommand.Parameters.Add(dtsParameter);  
  
      dtsParameter.Value = countryName;  
  
      dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default);  
  
      {  
        dtsDataReader.Read();  
        txtResults.Text = dtsDataReader.GetInt32(0).ToString("N0");  
      }  
  
      //After reaching the end of data rows,  
      // call the Read method one more time.  
      try  
      {  
        dtsDataReader.Read();  
      }  
      catch (Exception ex)  
      {  
        MessageBox.Show(  
          "Exception on final call to Read method:\n" + ex.Message + "\n" + ex.InnerException.Message,  
          "Exception on final call to Read method", MessageBoxButtons.OK, MessageBoxIcon.Error);  
      }  
  
      // The following method is a best practice, and is  
      //  required when using DtsDataParameter objects.  
      dtsCommand.Dispose();  
  
      try  
      {  
        dtsDataReader.Close();  
      }  
      catch (Exception ex)  
      {  
        MessageBox.Show(  
          "Exception closing DataReader:\n" + ex.Message + "\n" + ex.InnerException.Message,  
          "Exception closing DataReader", MessageBoxButtons.OK, MessageBoxIcon.Error);  
      }  
  
      try  
      {  
        dtsConnection.Close();  
      }  
      catch (Exception ex)  
      {  
        MessageBox.Show(  
          "Exception closing connection:\n" + ex.Message + "\n" + ex.InnerException.Message,  
          "Exception closing connection", MessageBoxButtons.OK, MessageBoxIcon.Error);  
      }  
  
      Cursor.Current = Cursors.Default;  
  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о различиях между локальным и удаленным выполнением](../../integration-services/run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)   
 [Программная загрузка и запуск локального пакета](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [Программная загрузка и запуск удаленного пакета](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
  

