---
title: Справка по PowerShell (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Help [PowerShell]
- Help [SQL Server], PowerShell
- PowerShell [SQL Server], help
ms.assetid: 968c316d-db83-4c24-8ea6-9f18736842f7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 705512f54feae3bf60317c18b8c260ef484abebc
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72797883"
---
# <a name="get-help-sql-server-powershell"></a>Get Help SQL Server PowerShell
  Сведения об использовании поставщика и командлетов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для Windows PowerShell можно получить из нескольких источников. К ним относится справка, доступная в среде Windows PowerShell.  
  
## <a name="before-you-begin"></a>Перед началом  
 Дополнительные сведения о Windows PowerShell см. в разделе [Приступая к работе с Windows PowerShell](https://technet.microsoft.com/library/hh857337.aspx).  
  
 Общие сведения о поставщике и командлетах [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] см. в статье [SQL Server PowerShell](../powershell/sql-server-powershell.md).  
  
### <a name="help-in-the-windows-powershell-environment"></a>Справка в среде Windows PowerShell  
 Командлет **Get-Help** позволяет получить справку в среде Windows PowerShell. Командлет**Get-Help** предоставляет основную справку по языку Windows PowerShell и различным командлетам и поставщикам, доступным в среде Windows PowerShell.  
  
 Дополнительные сведения о способах использования командлета **Get-Help**см. в документации по [получению справки с помощью командлета Get-Help](https://go.microsoft.com/fwlink/?LinkId=102136).  
  
### <a name="sql-server-powershell-provider-help"></a>Справка поставщика SQL Server PowerShell  
 Поставщик [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell создает несколько папок на виртуальном диске SQLSERVER, среди них папки SQLSERVER:\SQL и SQLSERVER:\DAC. Каждая папка связана с одной из объектных моделей управляемости SQL Server. Пользователь может перечислять методы и свойства, связанные с каждым узлом в пути SQL Server, однако он не может получить справку по ним в среде PowerShell. Таблица папок со ссылками на соответствующие разделы справочника по программированию приведена в статье [SQL Server PowerShell, поставщик](../powershell/sql-server-powershell-provider.md).  
  
### <a name="invoke-sqlcmd-help"></a>Справка Invoke-Sqlcmd  
 Командлет **Invoke-Sqlcmd** принимает в качестве входных данных любой файл запроса или скрипта, который можно запустить с помощью программы **sqlcmd** . **Get-Help** можно использовать для получения сведений о командлете **Invoke-Sqlcmd** и его параметрах, но **Get-Help** не охватывает запросы **sqlcmd** .  
  
 Параметр *-Query* или *-QueryFromFile* может содержать следующее:  
  
-   Переменные и команды**sqlcmd** . Сведения об этих переменных и командах см. в разделе "Примечания" статьи [Программа sqlcmd](../tools/sqlcmd-utility.md).  
  
-   [!INCLUDE[tsql](../includes/tsql-md.md)] . Дополнительные сведения о языке [!INCLUDE[tsql](../includes/tsql-md.md)] см. в [Справочнике по Transact-SQL (компонент Database Engine)](/sql/t-sql/language-reference).  
  
-   Инструкции XQuery. Сведения о языке XQuery, поддерживаемом [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], см. в [Справочнике по языку XQuery (SQL Server)](/sql/xquery/xquery-language-reference-sql-server).  
  
## <a name="get-help-for-a-sql-server-cmdlet"></a>Получение справки по командлету SQL Server  
 **Получение справки по командлету**  
  
-   Запустите командлет Get-Help, указав имя командлета и уровень справочных данных, которые должны быть возвращены.  
  
### <a name="example-cmdlet-get-help"></a>Пример: командлет Get-Help  
 Следующие примеры возвращают справочные данные по командлету **Invoke-Sqlcmd**разного уровня.  
  
```powershell
## Get the basic help.  
Get-Help Invoke-Sqlcmd  
  
## Get the full help.  
Get-Help Invoke-Sqlcmd -Full  
  
## Get the parameter descriptions.  
Get-Help Invoke-Sqlcmd -Parameter *  
  
## Get the code examples.  
Get-Help Invoke-Sqlcmd -Examples  
  
## Get the syntax diagram.  
Get-Help Invoke-Sqlcmd -Syntax  
```  
  
## <a name="get-a-list-of-providers"></a>Получение списка поставщиков  

### <a name="to-get-a-list-of-active-providers"></a>Получение списка активных поставщиков
  
1.  Запустите командлет Get-Help, указав категорию поставщиков.  
  
 Дополнительные сведения о получении справки поставщика в среде Windows PowerShell см. в разделе [Диски и поставщики](https://go.microsoft.com/fwlink/?LinkId=102137).  
  
### <a name="example-get-a-list-of-providers"></a>Пример: получение списка поставщиков  
 Следующий код возвращает список поставщиков, которые включены в текущем сеансе Windows PowerShell:  
  
```powershell
Get-Help -Category provider  
```  
  
## <a name="get-help-about-the-sql-server-provider"></a>Получение справки о поставщике SQL Server  
 **Получение справки о поставщике**  
  
1.  Запустите командлет Get-Help, указав имя SQL Server.  
  
### <a name="example-get-sql-server-provider-help"></a>Пример: получение справки о поставщике SQL Server  
 Код, приведенные в этом примере, возвращает основные сведения о поставщике [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] :  
  
```powershell
Get-Help SQLServer  
```  
  
## <a name="list-methods-and-properties"></a>Список методов и свойств  
 **Формирование списка методов и свойств узла из пути поставщика SQL Server**  
  
1.  Перейдите в узел из пути SQL Server или создайте набор переменных к этому расположению.  
  
2.  Выполните командлет **Get-Member** с параметром-Type, для которого задано значение либо методы, либо свойства.  
  
### <a name="examples-listing-methods-and-properties"></a>Примеры: список методов и свойств  
 Этот пример формирует список методов, поддерживаемых для узла Databases.  
  
```powershell
Set-Location SQL:\MyComputer\DEFAULT\Databases  
Get-Item . | Get-Member -Type Methods  
```  
  
 Этот пример формирует список свойств для переменной, заданной объекту таблицы SMO.  
  
```powershell
$MyVar = New-Object Microsoft.SqlServer.Management.SMO.Table  
$MyVar | Get-Member -Type Properties  
```  
  
## <a name="see-also"></a>См. также статью  
 [SQL Server PowerShell, поставщик](../powershell/sql-server-powershell-provider.md)   
 [Использование командлетов ядра СУБД](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
