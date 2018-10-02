---
title: Программная загрузка и запуск удаленного пакета | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- remote packages [Integration Services]
ms.assetid: 9f6ef376-3408-46bf-b5fa-fc7b18c689c9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 47b3ca2abf53fe93a24eb23650c1b741a2445988
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684401"
---
# <a name="loading-and-running-a-remote-package-programmatically"></a>Программная загрузка и запуск удаленного пакета
  Чтобы выполнить удаленные пакеты с локального компьютера, на котором не установлены службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], запустите пакеты таким образом, чтобы они выполнялись на удаленном компьютере, на котором установлены службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Чтобы запустить пакеты на удаленном компьютере с локального компьютера, понадобится агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], веб-служба или удаленный компонент. Если попытаться запустить удаленные пакеты непосредственно с локального компьютера, пакеты будут загружены на локальный компьютер и будут запущены оттуда. Если на локальном компьютере не установлены службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], запуск пакетов окажется невозможен.  
  
> [!NOTE]  
>  Невозможно выполнять пакеты вне среды [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] на клиентском компьютере, если не установлены службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Условия вашей лицензии на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут не допускать установку служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на дополнительных компьютерах. Службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] являются серверным компонентом и не могут устанавливаться на клиентских компьютерах.  
  
 В качестве альтернативы можно запустить удаленный пакет с локального компьютера, на котором установлены службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Дополнительные сведения см. в разделе [Программная загрузка и запуск локального пакета](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md).  
  
##  <a name="top"></a> Запуск удаленного пакета на удаленном компьютере  
 Как упоминалось выше, существует несколько способов выполнения удаленного пакета на удаленном сервере.  
  
-   [Использовать агент SQL Server, чтобы запустить удаленный пакет программным способом](#agent)  
  
-   [Использовать веб-службы или удаленный компонент, чтобы запустить удаленный пакет программным способом](#service)  
  
 Практически все методы, которые используются в этом разделе для загрузки и сохранения пакетов, требуют наличия ссылки на сборку **Microsoft.SqlServer.ManagedDTS**. Исключение составляет подход ADO.NET, продемонстрированный в этом разделе, к выполнению хранимой процедуры **sp_start_job**, для которой необходима только ссылка на сборку **System.Data**. После добавления ссылки на сборку **Microsoft.SqlServer.ManagedDTS** в новый проект импортируйте пространство имен <xref:Microsoft.SqlServer.Dts.Runtime> с помощью инструкции **using** или **Imports**.  
  
###  <a name="agent"></a> Использование агента SQL Server для выполнения удаленного пакета программным способом на сервере  
 В следующем образце кода демонстрируется, как программным способом использовать агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения удаленного пакета на сервере. В образце кода вызывается системная хранимая процедура **sp_start_job**, которая запускает задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Задание, запускаемое процедурой, называется `RunSSISPackage` и расположено на удаленном компьютере. Затем задание `RunSSISPackage` запускает пакет на удаленном компьютере.  
  
> [!NOTE]  
>  Значение возврата хранимой процедуры **sp_start_job** указывает, удалось ли хранимой процедуре успешно запустить задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Значение возврата не указывает на успешное или неуспешное выполнение пакета.  
  
 Сведения об устранении неполадок в пакетах, запускаемых из агента заданий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье базы знаний [Пакет служб SSIS не выполняется при вызове пакета из шага задания агента SQL Server](http://support.microsoft.com/kb/918760).  
  
### <a name="sample-code"></a>Образец кода  
  
```vb  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
  
    Dim jobConnection As SqlConnection  
    Dim jobCommand As SqlCommand  
    Dim jobReturnValue As SqlParameter  
    Dim jobParameter As SqlParameter  
    Dim jobResult As Integer  
  
    jobConnection = New SqlConnection("Data Source=(local);Initial Catalog=msdb;Integrated Security=SSPI")  
    jobCommand = New SqlCommand("sp_start_job", jobConnection)  
    jobCommand.CommandType = CommandType.StoredProcedure  
  
    jobReturnValue = New SqlParameter("@RETURN_VALUE", SqlDbType.Int)  
    jobReturnValue.Direction = ParameterDirection.ReturnValue  
    jobCommand.Parameters.Add(jobReturnValue)  
  
    jobParameter = New SqlParameter("@job_name", SqlDbType.VarChar)  
    jobParameter.Direction = ParameterDirection.Input  
    jobCommand.Parameters.Add(jobParameter)  
    jobParameter.Value = "RunSSISPackage"  
  
    jobConnection.Open()  
    jobCommand.ExecuteNonQuery()  
    jobResult = DirectCast(jobCommand.Parameters("@RETURN_VALUE").Value, Integer)  
    jobConnection.Close()  
  
    Select Case jobResult  
      Case 0  
        Console.WriteLine("SQL Server Agent job, RunSISSPackage, started successfully.")  
      Case Else  
        Console.WriteLine("SQL Server Agent job, RunSISSPackage, failed to start.")  
    End Select  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace LaunchSSISPackageAgent_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      SqlConnection jobConnection;  
      SqlCommand jobCommand;  
      SqlParameter jobReturnValue;  
      SqlParameter jobParameter;  
      int jobResult;  
  
      jobConnection = new SqlConnection("Data Source=(local);Initial Catalog=msdb;Integrated Security=SSPI");  
      jobCommand = new SqlCommand("sp_start_job", jobConnection);  
      jobCommand.CommandType = CommandType.StoredProcedure;  
  
      jobReturnValue = new SqlParameter("@RETURN_VALUE", SqlDbType.Int);  
      jobReturnValue.Direction = ParameterDirection.ReturnValue;  
      jobCommand.Parameters.Add(jobReturnValue);  
  
      jobParameter = new SqlParameter("@job_name", SqlDbType.VarChar);  
      jobParameter.Direction = ParameterDirection.Input;  
      jobCommand.Parameters.Add(jobParameter);  
      jobParameter.Value = "RunSSISPackage";  
  
      jobConnection.Open();  
      jobCommand.ExecuteNonQuery();  
      jobResult = (Int32)jobCommand.Parameters["@RETURN_VALUE"].Value;  
      jobConnection.Close();  
  
      switch (jobResult)  
      {  
        case 0:  
          Console.WriteLine("SQL Server Agent job, RunSISSPackage, started successfully.");  
          break;  
        default:  
          Console.WriteLine("SQL Server Agent job, RunSISSPackage, failed to start.");  
          break;  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
###  <a name="service"></a> Использование веб-службы или удаленного компонента для запуска удаленного пакета программным способом  
 В предыдущем решении для запуска пакетов программным способом на сервере не требовалось размещать какой-либо пользовательский код на сервере. Однако, возможно, предпочтительным окажется решение, не зависящее от агента SQL Server для выполнения пакетов. В следующем примере демонстрируется веб-служба, которая может быть создана на сервере для локального запуска пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], и тестовое приложение, которое можно использовать для вызова веб-службы с клиентского компьютера. Если предпочтительней создать удаленный компонент вместо веб-службы, можно использовать ту же логику кода после внесения незначительных изменений в удаленный компонент. Однако для удаленного компонента может потребоваться более сложная настройка, чем для веб-службы.  
  
> [!IMPORTANT]  
>  Веб-служба (с настройками по умолчанию для проверки подлинности и авторизации) обычно не имеет достаточных разрешений для доступа к SQL Server или файловой системе, чтобы загрузить и выполнить пакеты. Возможно, потребуется назначить соответствующие разрешения для веб-службы путем настройки ее проверки подлинности и авторизации в файле **web.config** и назначения необходимых разрешений для доступа к базе данных и файловой системе. Подробное обсуждение разрешений на доступ к базе данных и файловой системе из Интернета выходит за область этого раздела.  
  
> [!IMPORTANT]  
>  Методы класса <xref:Microsoft.SqlServer.Dts.Runtime.Application> для работы с хранилищем пакетов служб SSIS поддерживают только имена «.», localhost и имя сервера для локального сервера. Нельзя использовать имя «(local)».  
  
### <a name="sample-code"></a>Образец кода  
 В следующем образце кода демонстрируется, как создать и проверить веб-службу.  
  
#### <a name="creating-the-web-service"></a>Создание веб-службы  
 Пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может быть загружен непосредственно из файла, непосредственно с сервера SQL Server либо из хранилища пакетов служб SSIS, которое управляет хранением пакетов в SQL Server и специальных папках файловой системы. Этот образец поддерживает все доступные параметры с помощью конструкции **Select Case** или **switch**, чтобы выбрать подходящий синтаксис для запуска пакета и соответствующего объединения его входных аргументов. Метод веб-службы LaunchPackage возвращает результат выполнения пакета как целое число вместо значения <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>, чтобы для клиентских компьютеров не требовалась ссылка на какие-либо сборки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
###### <a name="to-create-a-web-service-to-run-packages-on-the-server-programmatically"></a>Создание веб-службы для запуска пакетов на сервере программным способом  
  
1.  Откройте среду Visual Studio и создайте проект веб-службы на предпочитаемом языке программирования. В образце кода для проекта используется имя LaunchSSISPackageService.  
  
2.  Добавьте ссылку на **Microsoft.SqlServer.ManagedDTS** и затем добавьте инструкцию **Imports** или **using** в файл кода для пространства имен **Microsoft.SqlServer.Dts.Runtime**.  
  
3.  Вставьте образец кода из метода веб-службы LaunchPackage в класс. (В этом образце приводится полное содержимое окна кода.)  
  
4.  Постройте и проверьте веб-службу, предоставив набор допустимых значений для входных аргументов метода LaunchPackage, указывающих на существующий пакет. Например, если пакет package1.dtsx хранится на сервере в папке C:\My Packages, передайте «file» в качестве значения sourceType, «C:\My Packages» в качестве значения sourceLocation и «package1» (без расширения файла) в качестве значения packageName.  
  
```vb  
Imports System.Web  
Imports System.Web.Services  
Imports System.Web.Services.Protocols  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.IO  
  
<WebService(Namespace:="http://dtsue/")> _  
<WebServiceBinding(ConformsTo:=WsiProfiles.BasicProfile1_1)> _  
<Global.Microsoft.VisualBasic.CompilerServices.DesignerGenerated()> _  
Public Class LaunchSSISPackageService  
  Inherits System.Web.Services.WebService  
  
  ' LaunchPackage Method Parameters:  
  ' 1. sourceType: file, sql, dts  
  ' 2. sourceLocation: file system folder, (none), logical folder  
  ' 3. packageName: for file system, ".dtsx" extension is appended  
  
  <WebMethod()> _  
  Public Function LaunchPackage( _  
    ByVal sourceType As String, _  
    ByVal sourceLocation As String, _  
    ByVal packageName As String) As Integer 'DTSExecResult  
  
    Dim packagePath As String  
    Dim myPackage As Package  
    Dim integrationServices As New Application  
  
    ' Combine path and file name.  
    packagePath = Path.Combine(sourceLocation, packageName)  
  
    Select Case sourceType  
      Case "file"  
        ' Package is stored as a file.  
        ' Add extension if not present.  
        If String.IsNullOrEmpty(Path.GetExtension(packagePath)) Then  
          packagePath = String.Concat(packagePath, ".dtsx")  
        End If  
        If File.Exists(packagePath) Then  
          myPackage = integrationServices.LoadPackage(packagePath, Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid file location: " & packagePath)  
        End If  
      Case "sql"  
        ' Package is stored in MSDB.  
        ' Combine logical path and package name.  
        If integrationServices.ExistsOnSqlServer(packagePath, ".", String.Empty, String.Empty) Then  
          myPackage = integrationServices.LoadFromSqlServer( _  
            packageName, "(local)", String.Empty, String.Empty, Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid package name or location: " & packagePath)  
        End If  
      Case "dts"  
        ' Package is managed by SSIS Package Store.  
        ' Default logical paths are File System and MSDB.  
        If integrationServices.ExistsOnDtsServer(packagePath, ".") Then  
          myPackage = integrationServices.LoadFromDtsServer(packagePath, "localhost", Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid package name or location: " & packagePath)  
        End If  
      Case Else  
        Throw New ApplicationException( _  
          "Invalid sourceType argument: valid values are 'file', 'sql', and 'dts'.")  
    End Select  
  
    Return myPackage.Execute()  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using System.Web;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.IO;  
  
[WebService(Namespace = "http://dtsue/")]  
[WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
public class LaunchSSISPackageServiceCS : System.Web.Services.WebService  
{  
  public LaunchSSISPackageServiceCS()  
  {  
    }  
  
  // LaunchPackage Method Parameters:  
  // 1. sourceType: file, sql, dts  
  // 2. sourceLocation: file system folder, (none), logical folder  
  // 3. packageName: for file system, ".dtsx" extension is appended  
  
  [WebMethod]  
  public int LaunchPackage(string sourceType, string sourceLocation, string packageName)  
  {   
  
    string packagePath;  
    Package myPackage;  
    Application integrationServices = new Application();  
  
    // Combine path and file name.  
    packagePath = Path.Combine(sourceLocation, packageName);  
  
    switch(sourceType)  
    {  
      case "file":  
        // Package is stored as a file.  
        // Add extension if not present.  
        if (String.IsNullOrEmpty(Path.GetExtension(packagePath)))  
        {  
          packagePath = String.Concat(packagePath, ".dtsx");  
        }  
        if (File.Exists(packagePath))  
        {  
          myPackage = integrationServices.LoadPackage(packagePath, null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid file location: "+packagePath);  
        }  
        break;  
      case "sql":  
        // Package is stored in MSDB.  
        // Combine logical path and package name.  
        if (integrationServices.ExistsOnSqlServer(packagePath, ".", String.Empty, String.Empty))  
        {  
          myPackage = integrationServices.LoadFromSqlServer(packageName, "(local)", String.Empty, String.Empty, null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid package name or location: "+packagePath);  
        }  
        break;  
      case "dts":  
        // Package is managed by SSIS Package Store.  
        // Default logical paths are File System and MSDB.  
        if (integrationServices.ExistsOnDtsServer(packagePath, "."))  
        {  
          myPackage = integrationServices.LoadFromDtsServer(packagePath, "localhost", null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid package name or location: "+packagePath);  
        }  
        break;  
      default:  
        throw new ApplicationException("Invalid sourceType argument: valid values are 'file', 'sql', and 'dts'.");  
    }  
  
    return (Int32)myPackage.Execute();  
  
  }  
  
}  
```  
  
#### <a name="testing-the-web-service"></a>Проверка веб-службы  
 В следующем образце приложения командной строки для запуска пакета используется веб-служба. Метод веб-службы LaunchPackage возвращает результат выполнения пакета как целое число вместо значения <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>, чтобы для клиентских компьютеров не требовалась ссылка на какие-либо сборки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В образце создается закрытое перечисление, значения которого отражают значения <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>, составляя отчет о результатах выполнения.  
  
###### <a name="to-create-a-console-application-to-test-the-web-service"></a>Создание приложения командной строки для проверки веб-службы  
  
1.  В среде Visual Studio добавьте новое приложение командной строки на предпочитаемом языке программирования в то же решение, в котором содержится проект веб-службы. В образце кода для проекта используется имя LaunchSSISPackageTest.  
  
2.  Определите новое приложение командной строки как автоматически загружаемый проект в решении.  
  
3.  Добавьте веб-ссылку в проект веб-службы. При необходимости измените декларацию переменной в образце кода на имя, назначенное для объекта учетной записи-посредника веб-службы.  
  
4.  Вставьте образец кода для подпрограммы Main и закрытого перечисления в код. (В этом образце приводится полное содержимое окна кода.)  
  
5.  Измените строку кода, которой вызывается метод LaunchPackage, и укажите допустимые значения для входных аргументов, которые указывают на существующий пакет. Например, если пакет package1.dtsx хранится на сервере в папке C:\My Packages, передайте «file» в качестве значения параметра `sourceType`, «C:\My Packages» — в качестве значения параметра `sourceLocation` и «package1» (без расширения файла) — в качестве значения параметра `packageName`.  
  
```vb  
Module LaunchSSISPackageTest  
  
  Sub Main()  
  
    Dim launchPackageService As New LaunchSSISPackageService.LaunchSSISPackageService  
    Dim packageResult As Integer  
  
    Try  
      packageResult = launchPackageService.LaunchPackage("sql", String.Empty, "SimpleTestPackage")  
    Catch ex As Exception  
      ' The type of exception returned by a Web service is:  
      '  System.Web.Services.Protocols.SoapException  
      Console.WriteLine("The following exception occurred: " & ex.Message)  
    End Try  
  
    Console.WriteLine(CType(packageResult, PackageExecutionResult).ToString)  
    Console.ReadKey()  
  
  End Sub  
  
  Private Enum PackageExecutionResult  
    PackageSucceeded  
    PackageFailed  
    PackageCompleted  
    PackageWasCancelled  
  End Enum  
  
End Module  
```  
  
```csharp  
using System;  
  
namespace LaunchSSISPackageSvcTestCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      LaunchSSISPackageServiceCS.LaunchSSISPackageServiceCS launchPackageService = new LaunchSSISPackageServiceCS.LaunchSSISPackageServiceCS();  
      int packageResult = 0;  
  
      try  
      {  
        packageResult = launchPackageService.LaunchPackage("sql", String.Empty, "SimpleTestPackage");  
      }  
      catch (Exception ex)  
      {  
        // The type of exception returned by a Web service is:  
        //  System.Web.Services.Protocols.SoapException  
        Console.WriteLine("The following exception occurred: " + ex.Message);  
      }  
  
      Console.WriteLine(((PackageExecutionResult)packageResult).ToString());  
      Console.ReadKey();  
  
    }  
  
    private enum PackageExecutionResult  
    {  
      PackageSucceeded,  
      PackageFailed,  
      PackageCompleted,  
      PackageWasCancelled  
    };  
  
  }  
}  
```  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Видеоролик [Как автоматизировать выполнение пакета служб SSIS с помощью агента SQL Server (видеоматериалы по SQL Server)](http://technet.microsoft.com/sqlserver/ff686764.aspx) на сайте technet.microsoft.com  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения об отличиях между локальным и удаленным выполнением](../../integration-services/run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)   
 [Программная загрузка и запуск локального пакета](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [Загрузка выхода локального пакета](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
