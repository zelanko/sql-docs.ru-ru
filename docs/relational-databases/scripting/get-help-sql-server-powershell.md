---
title: "Получение справок по SQL Server PowerShell | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "справка [PowerShell]"
  - "справка [SQL Server], PowerShell"
  - "PowerShell [SQL Server], справка"
ms.assetid: 968c316d-db83-4c24-8ea6-9f18736842f7
caps.latest.revision: 18
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 18
---
# Получение справок по SQL Server PowerShell
  Сведения об использовании поставщика и командлетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для Windows PowerShell можно получить из нескольких источников. К ним относится справка, доступная в среде Windows PowerShell.  
  
## Перед началом  
 Дополнительные сведения о Windows PowerShell см. в разделе [Приступая к работе с Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=217083).  
  
 Общие сведения о поставщике и командлетах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md).  
  
### Справка в среде Windows PowerShell  
 Командлет **Get-Help** позволяет получить справку в среде Windows PowerShell. Командлет **Get-Help** предоставляет основную справку по языку Windows PowerShell и различным командлетам и поставщикам, доступным в среде Windows PowerShell.  
  
 Дополнительные сведения о способах использования командлета **Get-Help** см. в документации по [получению справки с помощью командлета Get-Help](http://go.microsoft.com/fwlink/?LinkId=102136).  
  
### Справка поставщика SQL Server PowerShell  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell создает несколько папок на виртуальном диске SQLSERVER, среди них папки SQLSERVER:\SQL и SQLSERVER:\DAC. Каждая папка связана с одной из объектных моделей управляемости SQL Server. Пользователь может перечислять методы и свойства, связанные с каждым узлом в пути SQL Server, однако он не может получить справку по ним в среде PowerShell. Таблица папок со ссылками на соответствующие разделы справочника по программированию приведена в статье [SQL Server PowerShell, поставщик](../../relational-databases/scripting/sql-server-powershell-provider.md).  
  
### Справка Invoke-Sqlcmd  
 Командлет **Invoke-Sqlcmd** принимает в качестве входных данных любой файл запроса или скрипта, который можно запустить с помощью программы **sqlcmd**. **Get-Help** можно использовать для получения сведений о командлете **Invoke-Sqlcmd** и его параметрах, но **Get-Help** не охватывает запросы **sqlcmd**.  
  
 Параметр *-Query* или *-QueryFromFile* может содержать следующее:  
  
-   Переменные и команды **sqlcmd**. Сведения об этих переменных и командах см. в разделе "Примечания" статьи [Программа sqlcmd](../../tools/sqlcmd-utility.md).  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] . Дополнительные сведения о языке [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в [Справочнике по Transact-SQL (компонент Database Engine)](../../t-sql/transact-sql-reference-database-engine.md).  
  
-   Инструкции XQuery. Сведения о языке XQuery, поддерживаемом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в [Справочнике по языку XQuery (SQL Server)](../../xquery/xquery-language-reference-sql-server.md).  
  
## Получение справки по командлету SQL Server  
 **Получение справки по командлету**  
  
-   Запустите командлет Get-Help, указав имя командлета и уровень справочных данных, которые должны быть возвращены.  
  
### Пример: командлет Get-Help  
 Следующие примеры возвращают справочные данные по командлету **Invoke-Sqlcmd** разного уровня.  
  
```  
## Get the basic help.  
Get-Help Invoke-Sqlcmd  
  
## Get the full help.  
Get-Help Invoke-Sqlcmd –Full  
  
## Get the parameter descriptions.  
Get-Help Invoke-Sqlcmd -Parameter *  
  
## Get the code examples.  
Get-Help Invoke-Sqlcmd –Examples  
  
## Get the syntax diagram.  
Get-Help Invoke-Sqlcmd –Syntax  
```  
  
## Получение списка поставщиков  
 **Получение списка активных поставщиков**  
  
1.  Запустите командлет Get-Help, указав категорию поставщиков.  
  
 Дополнительные сведения о получении справки поставщика в среде Windows PowerShell см. в разделе [Диски и поставщики](http://go.microsoft.com/fwlink/?LinkId=102137).  
  
### Пример: получение списка поставщиков  
 Следующий код возвращает список поставщиков, которые включены в текущем сеансе Windows PowerShell:  
  
```  
Get-Help -Category provider  
```  
  
## Получение справки о поставщике SQL Server  
 **Получение справки о поставщике**  
  
1.  Запустите командлет Get-Help, указав имя SQL Server.  
  
### Пример: получение справки о поставщике SQL Server  
 Код, приведенные в этом примере, возвращает основные сведения о поставщике [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
Get-Help SQLServer  
```  
  
## Список методов и свойств  
 **Формирование списка методов и свойств узла из пути поставщика SQL Server**  
  
1.  Перейдите в узел из пути SQL Server или создайте набор переменных к этому расположению.  
  
2.  Запустите командлет **Get-Member**, при этом параметру –Type задайте значение Methods или Properties.  
  
### Примеры: список методов и свойств  
 Этот пример формирует список методов, поддерживаемых для узла Databases.  
  
```  
Set-Location SQL:\MyComputer\DEFAULT\Databases  
Get-Item . | Get-Member -Type Methods  
```  
  
 Этот пример формирует список свойств для переменной, заданной объекту таблицы SMO.  
  
```  
$MyVar = New-Object Microsoft.SqlServer.Management.SMO.Table  
$MyVar | Get-Member -Type Properties  
```  
  
## См. также:  
 [SQL Server PowerShell, поставщик](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [Использование командлетов компонента Database Engine](../../relational-databases/scripting/use-the-database-engine-cmdlets.md)  
  
  