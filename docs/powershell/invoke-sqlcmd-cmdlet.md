---
title: "Командлет Invoke-Sqlcmd | Документация Майкрософт"
ms.custom: 
ms.date: 08/05/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PowerShell [SQL Server], Invoke-Sqlcmd
- Cmdlets [SQL Server], Invoke-Sqlcmd
- Invoke-Sqlcmd cmdlet
- sqlcmd utility, PowerShell
ms.assetid: 0c74d21b-84a5-4fa4-be51-90f0f7230044
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 679625527f4f29d086b50e2291af4cff14b74d3e
ms.lasthandoff: 04/11/2017

---
# <a name="invoke-sqlcmd-cmdlet"></a>Invoke-Sqlcmd, командлет
  **Invoke-Sqlcmd** представляет собой командлет [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , предназначенный для выполнения скриптов, которые содержат инструкции определенных языков ([!INCLUDE[tsql](../includes/tsql-md.md)] и XQuery) и команды, поддерживаемые служебной программой **sqlcmd** .  
  
## <a name="using-invoke-sqlcmd"></a>Использование командлета Invoke-Sqlcmd  
 Командлет **Invoke-Sqlcmd** позволяет запускать файлы сценариев **sqlcmd** в среде Windows PowerShell. Значительная часть действий, выполняемых с помощью программы **sqlcmd** , может быть также выполнена с помощью командлета **Invoke-Sqlcmd**.  
  
 Ниже приведен пример вызова командлета Invoke-Sqlcmd для выполнения простого запроса, аналогичного тому, который выполняется путем задания команды **sqlcmd** с параметрами **-Q** и **-S** :  
  
```  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
 В этом примере вызывается командлет **Invoke-Sqlcmd**, указывается входной файл и вывод перенаправляется прямо в файл. Это аналогично заданию команды **sqlcmd** с параметрами **-i** и **-o** :  
  
```  
Invoke-Sqlcmd -InputFile "C:\MyFolder\TestSQLCmd.sql" | Out-File -filePath "C:\MyFolder\TestSQLCmd.rpt"  
```  
  
 В следующем примере массив Windows PowerShell используется для передачи нескольких переменных сценария **sqlcmd** в командлет **Invoke-Sqlcmd**. Символ "$", обозначающий переменные сценария **sqlcmd** в инструкции SELECT, отмечен как специальный с помощью escape-символа обратной кавычки PowerShell "`":  
  
```  
$MyArray = "MyVar1 = 'String1'", "MyVar2 = 'String2'"  
Invoke-Sqlcmd -Query "SELECT `$(MyVar1) AS Var1, `$(MyVar2) AS Var2;" -Variable $MyArray  
```  
  
 В следующем примере с помощью поставщика [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для Windows PowerShell выполняется переход к экземпляру компонента [!INCLUDE[ssDE](../includes/ssde-md.md)], а затем с помощью командлета **Get-Item** среды Windows PowerShell получается объект сервера SMO для экземпляра и передается командлету **Invoke-Sqlcmd**:  
  
```  
Set-Location SQLSERVER:\SQL\MyComputer\MyInstance  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance (Get-Item .)  
```  
  
 Параметр -Query является позиционным, ему не обязательно присваивать имя. Если первая строка, которая передается командлету **Invoke-Sqlcmd**, не имеет имени, то она обрабатывается как параметр -Query.  
  
```  
Invoke-Sqlcmd "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
## <a name="path-context-in-invoke-sqlcmd"></a>Путь к контексту в Invoke-Sqlcmd  
 Если параметр -Database не используется, контекст базы данных для Invoke-Sqlcmd задается активным путем при вызове командлета.  
  
|Путь|Контекст базы данных|  
|----------|----------------------|  
|Начинается с диска, отличного от SQLSERVER:|База данных по умолчанию для данного идентификатора входа в экземпляре по умолчанию на локальном компьютере.|  
|SQLSERVER:\SQL|База данных по умолчанию для данного идентификатора входа в экземпляре по умолчанию на локальном компьютере.|  
|SQLSERVER:\SQL\имя_компьютера|База данных по умолчанию для данного идентификатора входа в экземпляре по умолчанию на указанном компьютере.|  
|SQLSERVER:\SQL\имя_компьютера\имя_экземпляра|База данных по умолчанию для данного идентификатора входа в указанном экземпляре на указанном компьютере.|  
|SQLSERVER:\SQL\имя_компьютера\имя_экземпляра\Databases|База данных по умолчанию для данного идентификатора входа в указанном экземпляре на указанном компьютере.|  
|SQLSERVER:\SQL\имя_компьютера\имя_экземпляра\Databases\имя_базы данных|Указанная база данных в указанном экземпляре на указанном компьютере. Это также применимо к более длинным путям, например к пути, указывающему узел «Таблицы и столбцы» в базе данных.|  
  
 Например, предположим, что база данных по умолчанию для данной учетной записи Windows в экземпляре по умолчанию локального компьютера является основной. В этом случае следующие команды возвратят значение «master»:  
  
```  
Set-Location SQLSERVER:\SQL  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 Следующие команды возвратят базу данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]:  
  
```  
Set-Location SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Person  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 Командлет Invoke-Sqlcmd выдает предупреждение при использовании пути к контексту базы данных. Чтобы отключить сообщение с предупреждением, используется параметр -SuppressProviderContextWarning. Чтобы указать командлету Invoke-Sqlcmd операцию «всегда использовать для входа базу данных» по умолчанию, используется параметр -IgnoreProviderContext.  
  
## <a name="comparing-invoke-sqlcmd-and-the-sqlcmd-utility"></a>Сравнение командлета Invoke-Sqlcmd и программы sqlcmd  
 Командлет**Invoke-Sqlcmd** может использоваться для запуска многих сценариев, которые могут быть также выполнены с помощью служебной программы **sqlcmd** . Но командлет **Invoke-Sqlcmd** функционирует в среде Windows PowerShell, отличной от среды командной строки, в которой работает **sqlcmd** . Поведение **Invoke-Sqlcmd** было изменено в целях обеспечения работы в среде Windows PowerShell.  
  
 Тем не менее в командлете **Invoke-Sqlcmd** реализованы не все команды **sqlcmd**. Нереализованные команды включают следующее: **:!!**, **:connect**, **:error**, **:out**, **:ed**, **:list**, **:listvar**, **:reset**, **:perftrace**и **:serverlist**.  
  
 Командлет**Invoke-Sqlcmd** не инициализирует среду **sqlcmd** или переменные сценария, такие как SQLCMDDBNAME или SQLCMDWORKSTATION.  
  
 Командлет**Invoke-Sqlcmd** не отображает сообщения, такие как выходные данные инструкций PRINT, если не указан общий параметр **-Verbose** среды Windows PowerShell. Например:  
  
```  
Invoke-Sqlcmd -Query "PRINT N'abc';" -Verbose  
```  
  
 В среде PowerShell требуются не все параметры **sqlcmd** . Например, среда Windows PowerShell форматирует все выходные данные командлетов, поэтому параметры форматирования **sqlcmd** не реализованы в командлете **Invoke-Sqlcmd**. В следующей таблице показана связь между параметрами **Invoke-Sqlcmd** и параметрами **sqlcmd** .  
  
|Описание|Параметр sqlcmd|Параметр Invoke-Sqlcmd|  
|-----------------|-------------------|------------------------------|  
|Сервер и имя экземпляра|-S|-ServerInstance|  
|Используемая исходная база данных|-d|-Database|  
|Выполнение указанного запроса и выход|-Q|-Query|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-U|-Username|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-P|-Password|  
|Определение переменной|-v|-Variable|  
|Интервал времени ожидания запроса|-t|-QueryTimeout|  
|Прекращение выполнения в случае ошибки|-b|-AbortOnError|  
|Выделенное административное соединение|-A|-DedicatedAdministratorConnection|  
|Отключение интерактивных команд, скрипта запуска и переменных среды|-X|-DisableCommands|  
|Отключение подстановки переменных|-X|-DisableVariables|  
|Минимальная степень серьезности для формирования отчета|-v|-SeverityLevel|  
|Минимальный уровень ошибки для формирования отчета|-m|-ErrorLevel|  
|Интервал времени ожидания входа|-l|-ConnectionTimeout|  
|Имя узла|-H|-HostName|  
|Изменение пароля и выход|-Z|-NewPassword|  
|Входной файл, содержащий запрос|-i|-InputFile|  
|Максимальная длина символьных выходных данных|-w|-MaxCharLength|  
|Максимальная длина двоичных выходных данных|-w|-MaxBinaryLength|  
|Подключаться с помощью шифрования SSL|Параметр отсутствует|-EncryptConnection|  
|Отображать сообщения об ошибках|Параметр отсутствует|-OutputSqlErrors|  
|Выводить сообщения в поток stderr|-r|Параметр отсутствует|  
|Использовать региональные настройки клиента|-r|Параметр отсутствует|  
|Выполнить указанный запрос и продолжить работу|-Q|Параметр отсутствует|  
|Кодовая страница, применяемая для выходных данных|-f|Параметр отсутствует|  
|Сменить пароль и продолжить работу|-Z|Параметр отсутствует|  
|Размер пакета|-A|Параметр отсутствует|  
|Разделитель столбцов|-S|Параметр отсутствует|  
|Управлять заголовками выходных данных|-H|Параметр отсутствует|  
|Указать управляющие символы|-k|Параметр отсутствует|  
|Постоянная ширина экрана|-Y|Параметр отсутствует|  
|Переменная ширина экрана|-Y|Параметр отсутствует|  
|Эхо-повтор входных данных|-e|Параметр отсутствует|  
|Включить использование заключенных в кавычки идентификаторов|-i|Параметр отсутствует|  
|Удалить конечные пробелы|-w|Параметр отсутствует|  
|Перечислить экземпляры|-l|Параметр отсутствует|  
|Форматировать выходные данные в формате Юникод|-U|Параметр отсутствует|  
|Напечатать статистику|-P|Параметр отсутствует|  
|Окончание команды|-c|Параметр отсутствует|  
|Подключение с помощью проверки подлинности Windows|-e|Параметр отсутствует|  
  
## <a name="see-also"></a>См. также:  
 [Использование командлетов ядра СУБД](../relational-databases/scripting/use-the-database-engine-cmdlets.md)   
 [Программа sqlcmd](../tools/sqlcmd-utility.md)   
 [Использование программы sqlcmd](../relational-databases/scripting/sqlcmd-use-the-utility.md)  
  
  

