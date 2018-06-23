---
title: Командлет Invoke-PolicyEvaluation | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, Invoke-PolicyEvaluation
- Policy-Based Management, PowerShell
- Invoke-PolicyEvaluation cmdlet
- Cmdlets [SQL Server], Invoke-PolicyEvaluation
- PowerShell [SQL Server], Invoke-PolicyEvaluation
ms.assetid: 3e6d4f5a-59b7-4203-b95a-f7e692c0f131
caps.latest.revision: 18
author: mgblythe
ms.author: mblythe
manager: jhubbard
ms.openlocfilehash: c0ec56b9cde0a2def994d8deffd0ef051459dbf7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087715"
---
# <a name="invoke-policyevaluation-cmdlet"></a>Invoke-PolicyEvaluation, командлет
  **Invoke-PolicyEvaluation** — это командлет [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , который определяет, соответствует ли набор целей объектов SQL Server условиям, заданным в одной или нескольких политиках в системе управления на основе политик.  
  
## <a name="using-invoke-policyevaluation"></a>Использование Invoke-PolicyEvaluation  
 Командлет**Invoke-PolicyEvaluation** оценивает одну или несколько политик относительно набора объектов SQL Server, который называется целевым. Набор целевых объектов поступает от целевого сервера. Каждая политика определяет условия, которые являются разрешенными состояниями для целевых объектов. Например, в соответствии с политикой **Доверенная база данных** для свойства базы данных TRUSTWORTHY должно быть указано значение OFF.  
  
 Параметр **-AdHocPolicyEvaluationMode** определяет выполняемые действия:  
  
 Проверить  
 Сообщает состояние соответствия целевых объектов при помощи учетных данных текущего имени входа. Не проводите повторную настройку каких-либо объектов. Это параметр по умолчанию.  
  
 CheckSqlScriptAsProxy  
 Сообщите о состоянии соответствия целевых объектов с помощью учетных данных для входа на прокси-сервер **##MS_PolicyTSQLExecutionLogin##** . Не проводите повторную настройку каких-либо объектов.  
  
 Configure  
 Сообщает состояние соответствия целевых объектов при помощи учетных данных текущего имени входа. Измените все настраиваемые и детерминированные параметры, которые не соответствуют политикам.  
  
## <a name="specifying-polices"></a>Задание политик  
 Процедура задания политики зависит от того, где она хранится. Политики могут храниться в двух форматах.  
  
-   Они могут быть объектами, находящимися в хранилище политик, таком как экземпляр ядра СУБД. Для указания места хранения политик в хранилище политик можно использовать папку SQLSERVER:\SQLPolicy. При помощи командлетов Windows PowerShell можно фильтровать входные политики на основе их свойств, например использовать командлет Where-Object, чтобы фильтровать по категории политики, или Get-Item, чтобы фильтровать по имени политики.  
  
-   Политики можно экспортировать как XML-файлы. Можно использовать диск файловой системы, например D:, чтобы указать место для размещения XML-файлов. При помощи командлетов Windows PowerShell, таких как Where-Object, можно фильтровать политики по таким свойствам файла, как имя.  
  
 Если политики хранятся в хранилище политик, необходимо передавать набор PSObjects, указывающий на те политики, которые должны быть оценены. Обычно это делается путем перенаправления вывода командлета, например Get-Item, в командлет **Invoke-PolicyEvaluation**. При этом указывать параметр **-Policy** не нужно. Например, если политики "Рекомендации корпорации Майкрософт" были импортированы в экземпляр ядра СУБД, оценивать политику **Состояние базы данных** будет следующая команда:  
  
```  
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
Get-Item "Database Status" | Invoke-PolicyEvaluation -TargetServerName "MYCOMPUTER"  
```  
  
 В этом примере показано использование командлета Where-Object для фильтрации нескольких политик из хранилища политик на основе свойства **PolicyCategory** . Объекты из перенаправленного вывода **Where-Object** используются командлетом **Invoke-PolicyEvaluation**.  
  
```  
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
gci | Where-Object {$_.PolicyCategory -eq "Microsoft Best Practices: Maintenance"} | Invoke-PolicyEvaluation -TargetServer "MYCOMPUTER"  
```  
  
 Если политики хранятся в виде XML-файлов, вам нужно с помощью параметра **-Policy** указать путь и имя для каждой политики. Если вы не укажете путь в параметре **-Policy** , командлет **Invoke-PolicyEvaulation** будет использовать текущий параметр пути **sqlps** . Например, эта команда оценивает одну из политик «Microsoft Best Practice», установленных с SQL Server, по базе данных по умолчанию для этого имени входа:  
  
```  
Invoke-PolicyEvaluation -Policy "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033\Database Status.xml" -TargetServerName "MYCOMPUTER"  
```  
  
 Эта команда делает то же самое, но в ней для определения местоположения XML-файла политики используется текущий путь **sqlps** :  
  
```  
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName "MYCOMPUTER"  
```  
  
 В этом примере показано использование командлета **Get-ChildItem** для извлечения нескольких XML-файлов политик и перенаправления объектов в командлет **Invoke-PolicyEvaluation**:  
  
```  
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
gci "Database Status.xml", "Trustworthy Database.xml" | Invoke-PolicyEvaluation -TargetServer "MYCOMPUTER"  
```  
  
## <a name="specifying-the-target-set"></a>Указание набора целей  
 Для указания набора целевых объектов используется три параметра.  
  
-   Параметр **-TargetServerName** определяет экземпляр SQL Server, содержащий целевые объекты. Сведения можно указать в строке, для которой используется формат, определенный для свойства ConnectionString класса <xref:System.Data.SqlClient.SqlConnection> . Для построения правильно форматированной строки подключения можно использовать класс <xref:System.Data.SqlClient.SqlConnectionStringBuilder> . Можно также создать объект <xref:Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection> и передать его в параметр **-TargetServer**. При передаче строки, которая содержит только имя сервера, командлет **Invoke-PolicyEvaluation** для подключения к серверу использует проверку подлинности Windows.  
  
-   Параметр **-TargetObjects** принимает объект или массив объектов, которые представляют объекты SQL Server в наборе целей. Например, можно создать массив объектов класса <xref:Microsoft.SqlServer.Management.Smo.Database> для передачи параметру **-TargetObjects**.  
  
-   Параметр **-TargetExpressions** принимает строку, содержащую выражение запроса, которое определяет объекты в наборе целей. Это выражение запроса состоит из узлов, разделенных символом «/». Каждый узел имеет вид ObjectType[Filter]. Тип объекта — это один из объектов в иерархии управляющих объектов SQL Server (SMO). Фильтр — это выражение, которое фильтрует объекты в этом узле. Дополнительные сведения см. в статье [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md).  
  
 Укажите либо **-TargetObjects** , либо **-TargetExpression**, но не оба параметра.  
  
 В этом примере для указания целевого сервера используется объект Sfc.SqlStoreConnection:  
  
```  
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
$conn = New-Object Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection("server='MYCOMPUTER';Trusted_Connection=True")  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName $conn  
```  
  
 В этом примере для определения базы данных для оценки используется параметр **-TargetExpression** :  
  
```  
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName "MyComputer" -TargetExpression "Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']"  
```  
  
## <a name="evaluating-analysis-services-policies"></a>Оценка политик служб Analysis Services  
 Чтобы оценить политики относительно экземпляра служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], необходимо загрузить и зарегистрировать сборку в PowerShell, создать переменную с использованием объекта соединения служб Analysis Services и передать переменную параметру **-TargetObject** . В этом примере показана оценка политики настройки контактной зоны «Рекомендации» для служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]:  
  
```  
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\AnalysisServices\1033"  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.AnalysisServices")  
$SSASsvr = new-object Microsoft.AnalysisServices.Server  
$SSASsvr.Connect("Data Source=Localhost")  
Invoke-PolicyEvaluation -Policy "Surface Area Configuration for Analysis Services Features.xml" -TargetObject $SSASsvr  
```  
  
## <a name="evaluating-reporting-services-policies"></a>Оценка политик служб Reporting Services  
 Чтобы оценить политики служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , необходимо загрузить и зарегистрировать сборку в PowerShell, создать переменную с помощью объекта соединения [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и передать переменную параметру **-TargetObject** . В этом примере показана оценка политики настройки контактной зоны «Рекомендации» для служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]:  
  
```  
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\ReportingServices\1033"  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Dmf.Adapters")  
$SSRSsvr = new-object Microsoft.SqlServer.Management.Adapters.RSContainer('MyComputer')  
Invoke-PolicyEvaluation -Policy "Surface Area Configuration for Reporting Services 2008 Features.xml" -TargetObject $SSRSsvr  
```  
  
## <a name="formatting-output"></a>Форматирование выходных данных  
 По умолчанию выходные данные командлета **Invoke-PolicyEvaluation** отображаются в окне командной строки в виде краткого отчета в удобной для чтения форме. С помощью параметра **-OutputXML** можно указать, что командлет должен генерировать подробный отчет в виде XML-файла. Командлет**Invoke-PolicyEvaluation** использует схему SML-IF, поэтому файл смогут читать модули чтения SML-IF.  
  
```  
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
Invoke-PolicyEvaluation -Policy "Datbase Status" -TargetServer "MYCOMPUTER" -OutputXML > C:\MyReports\DatabaseStatusReport.xml  
```  
  
## <a name="see-also"></a>См. также  
 [Использование командлетов ядра СУБД](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
  
  