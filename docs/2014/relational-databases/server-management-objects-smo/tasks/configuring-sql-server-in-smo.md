---
title: Настройка SQL Server в SMO | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- SQL Server, configuring
- configuration options [SMO]
ms.assetid: 0a372643-15cb-45a7-8665-04f1215df8ed
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a0d54fd966594fc8219623e566f68edf65023546
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48052184"
---
# <a name="configuring-sql-server-in-smo"></a>Настройка SQL Server в SMO
  В SMO <xref:Microsoft.SqlServer.Management.Smo.Information> объекта, <xref:Microsoft.SqlServer.Management.Smo.Settings> объекта, <xref:Microsoft.SqlServer.Management.Smo.UserOptions> объекта и <xref:Microsoft.SqlServer.Management.Smo.Configuration> содержат настройки и сведения для экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] имеется множество свойств, описывающих поведение установленного экземпляра. Эти свойства описывают параметры запуска, используемые по умолчанию параметры сервера, файлы и каталоги, сведения о системе и процессоре, о продукте и версиях, сведения о соединении, параметры памяти, выбранные язык и параметры сортировки, а также режим проверки подлинности.  
  
## <a name="sql-server-configuration"></a>Настройка SQL Server  
 <xref:Microsoft.SqlServer.Management.Smo.Information> Свойства объекта содержат сведения об экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], такие как процессор и платформа.  
  
 <xref:Microsoft.SqlServer.Management.Smo.Settings> Свойства объекта содержат сведения об экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Помимо свойств Mail Profile и Server Account можно изменить используемые по умолчанию файл базы данных и каталог. Эти свойства сохраняются на протяжении всего соединения.  
  
 В свойствах объекта <xref:Microsoft.SqlServer.Management.Smo.UserOptions> содержатся сведения о текущем поведении соединения, связанном с выполняемыми вычислениями, применяемыми стандартами ANSI и осуществляемыми транзакциями.  
  
 Имеется также ряд параметров конфигурации, представленных <xref:Microsoft.SqlServer.Management.Smo.Configuration> объекта. Он содержит набор свойств, представляющих параметры, которые можно изменить с помощью хранимой процедуры `sp_configure`. Параметры, такие как **Priority Boost**, **Recovery Interval** и **Network Packet Size**управляют производительностью экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Многие из этих параметров можно менять динамически, но в некоторых случаях значение сначала надо настроить, а затем изменить при перезапуске экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Существует <xref:Microsoft.SqlServer.Management.Smo.Configuration> объект, свойство для каждого параметра конфигурации. С помощью объекта <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> можно изменить глобальные настройки конфигурации. У многих свойств есть максимальное и минимальное значения, которые также хранятся как свойства <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>. Этим свойствам требуется <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> для фиксирования изменений на экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Все параметры конфигурации в <xref:Microsoft.SqlServer.Management.Smo.Configuration> объект должен изменять системный администратор.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. в разделе [Создание проекта SMO на Visual Basic в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) и [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="modifying-sql-server-configuration-options-in-visual-basic"></a>Изменение параметров конфигурации SQL Server на языке Visual Basic  
 Этот пример кода показывает, как обновить параметр конфигурации на языке Visual Basic .NET. Он также возвращает и отображает сведения о максимальном и минимальном значениях указанного параметра конфигурации. Наконец, программа извещает пользователя, если изменение уже внесено динамически или оно будет храниться до экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] перезапускается.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure2](SMO How to#SMO_VBConfigure2)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-basic"></a>Изменение параметров SQL Server на языке Visual Basic  
 В примере кода отображаются сведения об экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в <xref:Microsoft.SqlServer.Management.Smo.Information> и <xref:Microsoft.SqlServer.Management.Smo.Settings>, а также изменяет настройки <xref:Microsoft.SqlServer.Management.Smo.Settings> и <xref:Microsoft.SqlServer.Management.Smo.UserOptions>свойства объекта.  
  
 В этом примере оба объекта, <xref:Microsoft.SqlServer.Management.Smo.UserOptions> и <xref:Microsoft.SqlServer.Management.Smo.Settings>, обладают методом <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Можно запустить <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> методы для них по отдельности.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure1](SMO How to#SMO_VBConfigure1)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-c"></a>Изменение параметров SQL Server на языке Visual C#  
 В примере кода отображаются сведения об экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в <xref:Microsoft.SqlServer.Management.Smo.Information> и <xref:Microsoft.SqlServer.Management.Smo.Settings>, а также изменяет настройки <xref:Microsoft.SqlServer.Management.Smo.Settings> и <xref:Microsoft.SqlServer.Management.Smo.UserOptions>свойства объекта.  
  
 В этом примере оба объекта, <xref:Microsoft.SqlServer.Management.Smo.UserOptions> и <xref:Microsoft.SqlServer.Management.Smo.Settings>, обладают методом <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Можно запустить <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> методы для них по отдельности.  
  
 `//Connect to the local, default instance of SQL Server.`  
  
```  
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
 В примере кода отображаются сведения об экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в <xref:Microsoft.SqlServer.Management.Smo.Information> и <xref:Microsoft.SqlServer.Management.Smo.Settings>, а также изменяет настройки <xref:Microsoft.SqlServer.Management.Smo.Settings> и <xref:Microsoft.SqlServer.Management.Smo.UserOptions>свойства объекта.  
  
 В этом примере оба объекта, <xref:Microsoft.SqlServer.Management.Smo.UserOptions> и <xref:Microsoft.SqlServer.Management.Smo.Settings>, обладают методом <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Можно запустить <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> методы для них по отдельности.  
  
```  
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
 Этот пример кода показывает, как обновить параметр конфигурации на языке Visual Basic .NET. Он также возвращает и отображает сведения о максимальном и минимальном значениях указанного параметра конфигурации. Наконец, программа извещает пользователя, если изменение уже внесено динамически или оно будет храниться до экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] перезапускается.  
  
```  
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
  
  
