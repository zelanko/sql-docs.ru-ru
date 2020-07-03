---
title: Настройка SQL Server в SMO
ms.custom: seo-dt-2019
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server, configuring
- configuration options [SMO]
ms.assetid: 0a372643-15cb-45a7-8665-04f1215df8ed
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 63d520192b0366819b5be59aa73c90f192aa8643
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85900058"
---
# <a name="configuring-sql-server-in-smo"></a>Настройка SQL Server в SMO
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw.md)]

  В объектах SMO объект, объект, объект <xref:Microsoft.SqlServer.Management.Smo.Information> <xref:Microsoft.SqlServer.Management.Smo.Settings> <xref:Microsoft.SqlServer.Management.Smo.UserOptions> и <xref:Microsoft.SqlServer.Management.Smo.Configuration> объект содержат параметры и сведения для экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] имеется множество свойств, описывающих поведение установленного экземпляра. Эти свойства описывают параметры запуска, используемые по умолчанию параметры сервера, файлы и каталоги, сведения о системе и процессоре, о продукте и версиях, сведения о соединении, параметры памяти, выбранные язык и параметры сортировки, а также режим проверки подлинности.  
  
## <a name="sql-server-configuration"></a>Настройка SQL Server  
 В свойствах объекта <xref:Microsoft.SqlServer.Management.Smo.Information> содержатся такие сведения об экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], как процессор и платформа.  
  
 Свойства объекта <xref:Microsoft.SqlServer.Management.Smo.Settings> содержат сведения об экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Помимо свойств Mail Profile и Server Account можно изменить используемые по умолчанию файл базы данных и каталог. Эти свойства сохраняются на протяжении всего соединения.  
  
 В свойствах объекта <xref:Microsoft.SqlServer.Management.Smo.UserOptions> содержатся сведения о текущем поведении соединения, связанном с выполняемыми вычислениями, применяемыми стандартами ANSI и осуществляемыми транзакциями.  
  
 Помимо этого имеется также ряд параметров конфигурации, представленных объектом <xref:Microsoft.SqlServer.Management.Smo.Configuration>. Он содержит набор свойств, представляющих параметры, которые можно изменить с помощью хранимой процедуры **sp_configure** . Такие параметры, как **повышение приоритета**, **интервал восстановления** и **Размер сетевого пакета**, контролируют производительность экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Многие из этих параметров можно менять динамически, но в некоторых случаях значение сначала надо настроить, а затем изменить при перезапуске экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Для каждого параметра конфигурации существует свойство объекта <xref:Microsoft.SqlServer.Management.Smo.Configuration>. С помощью объекта <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> можно изменить глобальные настройки конфигурации. У многих свойств есть максимальное и минимальное значения, которые также хранятся как свойства <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>. Для этих свойств требуется, <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> чтобы метод зафиксировал изменения в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Все параметры конфигурации в объекте <xref:Microsoft.SqlServer.Management.Smo.Configuration> должен изменять системный администратор.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. [в статье Создание проекта Visual C&#35; SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="modifying-sql-server-configuration-options-in-visual-basic"></a>Изменение параметров конфигурации SQL Server на языке Visual Basic  
 Этот пример кода показывает, как обновить параметр конфигурации на языке Visual Basic .NET. Он также возвращает и отображает сведения о максимальном и минимальном значениях указанного параметра конфигурации. Наконец, программа извещает пользователя, выполнено ли изменение динамически или оно будет храниться до тех пор, пока не произойдет перезагрузка экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Display all the configuration options.
Dim p As ConfigProperty
For Each p In srv.Configuration.Properties
    Console.WriteLine(p.DisplayName)
Next
Console.WriteLine("There are " & srv.Configuration.Properties.Count.ToString & " configuration options.")
'Display the maximum and minimum values for ShowAdvancedOptions.
Dim min As Integer
Dim max As Integer
min = srv.Configuration.ShowAdvancedOptions.Minimum
max = srv.Configuration.ShowAdvancedOptions.Maximum
Console.WriteLine("Minimum and Maximum values are " & min & " and " & max & ".")
'Modify the value of ShowAdvancedOptions and run the Alter method.
srv.Configuration.ShowAdvancedOptions.ConfigValue = 0
srv.Configuration.Alter()
'Display when the change takes place according to the IsDynamic property.
If srv.Configuration.ShowAdvancedOptions.IsDynamic = True Then
    Console.WriteLine("Configuration option has been updated.")
Else
    Console.WriteLine("Configuration option will be updated when SQL Server is restarted.")
End If
``` 
  
## <a name="modifying-sql-server-settings-in-visual-basic"></a>Изменение параметров SQL Server на языке Visual Basic  
 В примере кода выводятся сведения об экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в <xref:Microsoft.SqlServer.Management.Smo.Information> и <xref:Microsoft.SqlServer.Management.Smo.Settings> , а также изменяются параметры в <xref:Microsoft.SqlServer.Management.Smo.Settings> <xref:Microsoft.SqlServer.Management.Smo.UserOptions> свойствах объекта и.  
  
 В этом примере оба объекта, <xref:Microsoft.SqlServer.Management.Smo.UserOptions> и <xref:Microsoft.SqlServer.Management.Smo.Settings>, обладают методом <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Для них можно отдельно запустить методы <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Display information about the instance of SQL Server in Information and Settings.
Console.WriteLine("OS Version = " & srv.Information.OSVersion)
Console.WriteLine("State = " & srv.Settings.State.ToString)
'Display information specific to the current user in UserOptions.
Console.WriteLine("Quoted Identifier support = " & srv.UserOptions.QuotedIdentifier)
'Modify server settings in Settings.

srv.Settings.LoginMode = ServerLoginMode.Integrated
'Modify settings specific to the current connection in UserOptions.
srv.UserOptions.AbortOnArithmeticErrors = True
'Run the Alter method to make the changes on the instance of SQL Server.
srv.Alter()
```
  
## <a name="modifying-sql-server-settings-in-visual-c"></a>Изменение параметров SQL Server на языке Visual C#  
 В примере кода выводятся сведения об экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в <xref:Microsoft.SqlServer.Management.Smo.Information> и <xref:Microsoft.SqlServer.Management.Smo.Settings> , а также изменяются параметры в <xref:Microsoft.SqlServer.Management.Smo.Settings> <xref:Microsoft.SqlServer.Management.Smo.UserOptions> свойствах объекта и.  
  
 В этом примере оба объекта, <xref:Microsoft.SqlServer.Management.Smo.UserOptions> и <xref:Microsoft.SqlServer.Management.Smo.Settings>, обладают методом <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Для них можно отдельно запустить методы <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>.  
  
 `//Connect to the local, default instance of SQL Server.`  
  
```csharp  
{  
            Server srv = new Server();  
            //Display all the configuration options.   
  
            foreach (ConfigProperty p in srv.Configuration.Properties)  
            {  
                Console.WriteLine(p.DisplayName);  
            }  
            Console.WriteLine("There are " + srv.Configuration.Properties.Count.ToString() + " configuration options.");  
            //Display the maximum and minimum values for ShowAdvancedOptions.   
            int min = 0;  
            int max = 0;  
            min = srv.Configuration.ShowAdvancedOptions.Minimum;  
            max = srv.Configuration.ShowAdvancedOptions.Maximum;  
            Console.WriteLine("Minimum and Maximum values are " + min + " and " + max + ".");  
            //Modify the value of ShowAdvancedOptions and run the Alter method.   
            srv.Configuration.ShowAdvancedOptions.ConfigValue = 0;  
            srv.Configuration.Alter();  
            //Display when the change takes place according to the IsDynamic property.   
            if (srv.Configuration.ShowAdvancedOptions.IsDynamic == true)  
            {  
                Console.WriteLine("Configuration option has been updated.");  
            }  
            else  
            {  
                Console.WriteLine("Configuration option will be updated when SQL Server is restarted.");  
            }  
        }  
```  
  
## <a name="modifying-sql-server-settings-in-powershell"></a>Изменение параметров SQL Server в PowerShell  
 В примере кода выводятся сведения об экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в <xref:Microsoft.SqlServer.Management.Smo.Information> и <xref:Microsoft.SqlServer.Management.Smo.Settings> , а также изменяются параметры в <xref:Microsoft.SqlServer.Management.Smo.Settings> <xref:Microsoft.SqlServer.Management.Smo.UserOptions> свойствах объекта и.  
  
 В этом примере оба объекта, <xref:Microsoft.SqlServer.Management.Smo.UserOptions> и <xref:Microsoft.SqlServer.Management.Smo.Settings>, обладают методом <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Для них можно отдельно запустить методы <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>.  
  
```powershell 
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Display information about the instance of SQL Server in Information and Settings.  
"OS Version = " + $srv.Information.OSVersion  
"State = "+ $srv.Settings.State.ToString()  
  
#Display information specific to the current user in UserOptions.  
"Quoted Identifier support = " + $srv.UserOptions.QuotedIdentifier  
  
#Modify server settings in Settings.  
$srv.Settings.LoginMode = [Microsoft.SqlServer.Management.SMO.ServerLoginMode]::Integrated  
  
#Modify settings specific to the current connection in UserOptions.  
$srv.UserOptions.AbortOnArithmeticErrors = $true  
  
#Run the Alter method to make the changes on the instance of SQL Server.  
$srv.Alter()  
```  
  
## <a name="modifying-sql-server-configuration-options-in-powershell"></a>Изменение параметров конфигурации SQL Server в PowerShell  
 Этот пример кода показывает, как обновить параметр конфигурации на языке Visual Basic .NET. Он также возвращает и отображает сведения о максимальном и минимальном значениях указанного параметра конфигурации. Наконец, программа извещает пользователя, выполнено ли изменение динамически или оно будет храниться до тех пор, пока не произойдет перезагрузка экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
```powershell 
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalMachine  
$svr = get-item default  
  
#enumerate its properties  
foreach ($Item in $Svr.Configuration.Properties)   
{  
 $Item.DisplayName  
}  
  
"There are " + $svr.Configuration.Properties.Count.ToString() + " configuration options."  
  
#Display the maximum and minimum values for ShowAdvancedOptions.  
$min = $svr.Configuration.ShowAdvancedOptions.Minimum  
$max = $svr.Configuration.ShowAdvancedOptions.Maximum  
"Minimum and Maximum values are " + $min.ToString() + " and " + $max.ToString() + "."  
  
#Modify the value of ShowAdvancedOptions and run the Alter method.  
$svr.Configuration.ShowAdvancedOptions.ConfigValue = 0  
$svr.Configuration.Alter()  
  
#Display when the change takes place according to the IsDynamic property.  
If ($svr.Configuration.ShowAdvancedOptions.IsDynamic -eq $true)  
 {    
   "Configuration option has been updated."  
 }  
Else  
{  
    "Configuration option will be updated when SQL Server is restarted."  
}  
```  
  
  
