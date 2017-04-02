---
title: "Развертывание пакетов на сервере служб Integration Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c26ce7f4-7b34-4c9a-8649-ba767d30c827
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Развертывание пакетов на сервере служб Integration Services
  Функция добавочного развертывания пакетов, представленная в  [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] , позволяет развертывать один или несколько пакетов в существующем или новом проекте без развертывания всего проекта.  
  
##  <a name="DeployWizard"></a> Развертывание пакетов с помощью мастера развертывания служб Integration Services  
  
1.  Из командной строки запустите **isdeploymentwizard.exe**, расположенный в каталоге **%ProgramFiles%\Microsoft SQL Server\130\DTS\Binn**. На 64-разрядных компьютерах есть также 32-разрядная версия средства в каталоге **%ProgramFiles(x86)%\Microsoft SQL Server\130\DTS\Binn**.  
  
2.  На странице **Выбор источника** переключитесь к **модели развертывания пакета**. Затем выберите папку, которая содержит исходные пакеты, и настройте их.  
  
3.  Завершите работу мастера. Выполните оставшиеся действия, описанные в статье [Package Deployment Model](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel).  
  
##  <a name="SSMS"></a> Развертывание пакетов с помощью среды SQL Server Management Studio  
  
1.  В обозревателе объектов среды SQL Server Management Studio разверните узел **Каталоги служб Integration Services** > **SSISDB**.  
  
2.  Щелкните папку **Проекты** правой кнопкой мыши и выберите команду **Deploy Projects** (Развернуть проекты).  
  
3.  Если появится страница **Введение** , нажмите кнопку **Далее** , чтобы продолжить.  
  
4.  На странице **Выбор источника** переключитесь к **модели развертывания пакета**. Затем выберите папку, которая содержит исходные пакеты, и настройте их.  
  
5.  Завершите работу мастера. Выполните оставшиеся действия, описанные в статье [Package Deployment Model](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel).  
  
##  <a name="SSDT"></a> Развертывание пакетов с помощью SQL Server Data Tools (Visual Studio)  
  
1.  В Visual Studio откройте проект служб Integration Services, выберите пакет или пакеты, которые требуется развернуть.  
  
2.  Щелкните правой кнопкой мыши и выберите пункт **Развернуть пакет**. Откроется мастер развертывания, в котором выбранные пакеты будут настроены в качестве исходных.  
  
3.  Завершите работу мастера. Выполните оставшиеся действия, описанные в статье [Package Deployment Model](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel).  
  
##  <a name="StoredProcedure"></a> Развертывание пакетов с помощью хранимой процедуры deploy_packages  
 Чтобы развернуть один или несколько пакетов служб SSIS в каталоге служб SSIS, можно использовать хранимую процедуру **[catalog].[deploy_packages]**. В следующем примере кода показано использование этой хранимой процедуры для развертывания пакетов на сервере служб SSIS. Дополнительные сведения см. в разделе [catalog.deploy_packages](../../integration-services/system-stored-procedures/catalog-deploy-packages.md).  
  
```  
  
private static void Main(string[] args)  
{  
    // Connection string to SSISDB  
    var connectionString = "Data Source=.;Initial Catalog=SSISDB;Integrated Security=True;MultipleActiveResultSets=false";  
  
    using (var sqlConnection = new SqlConnection(connectionString))  
    {  
        sqlConnection.Open();  
  
        var sqlCommand = new SqlCommand  
        {  
            Connection = sqlConnection,  
            CommandType = CommandType.StoredProcedure,  
            CommandText = "[catalog].[deploy_packages]"  
        };  
  
        var packageData = Encoding.UTF8.GetBytes(File.ReadAllText(@"C:\Test\Package.dtsx"));  
  
        // DataTable: name is the package name without extension and package_data is byte array of package.  
        var packageTable = new DataTable();  
        packageTable.Columns.Add("name", typeof(string));  
        packageTable.Columns.Add("package_data", typeof(byte[]));  
        packageTable.Rows.Add("Package", packageData);  
  
        // Set the destination project and folder which is named Folder and Project.  
        sqlCommand.Parameters.Add(new SqlParameter("@folder_name", SqlDbType.NVarChar, ParameterDirection.Input, "Folder", -1));  
        sqlCommand.Parameters.Add(new SqlParameter("@project_name", SqlDbType.NVarChar, ParameterDirection.Input, "Project", -1));  
        sqlCommand.Parameters.Add(new SqlParameter("@packages_table", SqlDbType.Structured, ParameterDirection.Input, packageTable, -1));  
  
        var result = sqlCommand.Parameters.Add("RetVal", SqlDbType.Int);  
        result.Direction = ParameterDirection.ReturnValue;  
  
        sqlCommand.ExecuteNonQuery();  
    }  
}  
  
```  
  
##  <a name="MOMApi"></a> Развертывание пакетов с помощью API объектной модели управления  
 В следующем примере кода показано использование API объектной модели управления для развертывания пакетов на сервере.  
  
```  
  
static void Main()  
 {  
     // Before deploying packages, make sure the destination project exists in SSISDB.  
     var connectionString = "Data Source=.;Integrated Security=True;MultipleActiveResultSets=false";  
     var catalogName = "SSISDB";  
     var folderName = "Folder";  
     var projectName = "Project";  
  
     // Get the folder instance.  
     var sqlConnection = new SqlConnection(connectionString);  
     var store = new Microsoft.SqlServer.Management.IntegrationServices.IntegrationServices(sqlConnection);  
     var folder = store.Catalogs[catalogName].Folders[folderName];  
  
     // Key is package name without extension and value is package binaries.  
     var packageDict = new Dictionary<string, string>();  
  
     var packageData = File.ReadAllText(@"C:\Folder\Package.dtsx");  
     packageDict.Add("Package", packageData);  
  
     // Deploy package to the destination project.  
     folder.DeployPackages(projectName, packageDict);  
 }  
  
```  
  
  