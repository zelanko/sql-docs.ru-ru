---
title: Командлет Invoke-Sqlcmd | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], Invoke-Sqlcmd
- Cmdlets [SQL Server], Invoke-Sqlcmd
- Invoke-Sqlcmd cmdlet
- sqlcmd utility, PowerShell
ms.assetid: 0c74d21b-84a5-4fa4-be51-90f0f7230044
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: beee2fa576387eadb75ee5ab1bfefcb66453acc0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "76928026"
---
# <a name="invoke-sqlcmd-cmdlet"></a>Invoke-Sqlcmd, командлет
  **Invoke-Sqlcmd** представляет собой командлет [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], предназначенный для выполнения сценариев, которые содержат инструкции определенных языков ([!INCLUDE[tsql](../includes/tsql-md.md)] и XQuery) и команды, поддерживаемые служебной программой **sqlcmd**.  
  
## <a name="using-invoke-sqlcmd"></a>Использование командлета Invoke-Sqlcmd  
 Командлет **Invoke-Sqlcmd** позволяет запускать файлы сценариев **sqlcmd** в среде Windows PowerShell. Значительная часть действий, выполняемых с помощью программы **sqlcmd** , может быть также выполнена с помощью командлета **Invoke-Sqlcmd**.  
  
 Ниже приведен пример вызова командлета Invoke-Sqlcmd для выполнения простого запроса, аналогичного тому, который выполняется путем задания команды **sqlcmd** с параметрами **-Q** и **-S** :  
  
```powershell
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
 В этом примере вызывается командлет **Invoke-Sqlcmd**, указывается входной файл и вывод перенаправляется прямо в файл. Это аналогично заданию команды **sqlcmd** с параметрами **-i** и **-o** :  
  
```powershell
Invoke-Sqlcmd -InputFile "C:\MyFolder\TestSQLCmd.sql" | Out-File -FilePath "C:\MyFolder\TestSQLCmd.rpt"  
```  
  
 В следующем примере массив Windows PowerShell используется для передачи нескольких переменных сценария **sqlcmd** в командлет **Invoke-Sqlcmd**. Символ "$", обозначающий переменные сценария **sqlcmd** в инструкции SELECT, отмечен как специальный с помощью escape-символа обратной кавычки PowerShell "`":  
  
```powershell
$MyArray = "MyVar1 = 'String1'", "MyVar2 = 'String2'"  
Invoke-Sqlcmd -Query "SELECT `$(MyVar1) AS Var1, `$(MyVar2) AS Var2;" -Variable $MyArray  
```  
  
 В следующем примере с помощью поставщика [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для Windows PowerShell выполняется переход к экземпляру компонента [!INCLUDE[ssDE](../includes/ssde-md.md)], а затем с помощью командлета **Get-Item** среды Windows PowerShell получается объект сервера SMO для экземпляра и передается командлету **Invoke-Sqlcmd**:  
  
```powershell
Set-Location SQLSERVER:\SQL\MyComputer\MyInstance  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance (Get-Item .)  
```  
  
 Параметр -Query является позиционным, ему не обязательно присваивать имя. Если первая строка, которая передается командлету **Invoke-Sqlcmd**, не имеет имени, то она обрабатывается как параметр -Query.  
  
```powershell
Invoke-Sqlcmd "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
## <a name="path-context-in-invoke-sqlcmd"></a>Путь к контексту в Invoke-Sqlcmd  
 Если параметр -Database не используется, контекст базы данных для Invoke-Sqlcmd задается активным путем при вызове командлета.  
  
|Path|Контекст базы данных|  
|----------|----------------------|  
|Начинается с диска, отличного от SQLSERVER:|База данных по умолчанию для данного идентификатора входа в экземпляре по умолчанию на локальном компьютере.|  
|SQLSERVER:\SQL|База данных по умолчанию для данного идентификатора входа в экземпляре по умолчанию на локальном компьютере.|  
|SQLSERVER:\SQL\имя_компьютера|База данных по умолчанию для данного идентификатора входа в экземпляре по умолчанию на указанном компьютере.|  
|SQLSERVER:\SQL\имя_компьютера\имя_экземпляра|База данных по умолчанию для данного идентификатора входа в указанном экземпляре на указанном компьютере.|  
|SQLSERVER:\SQL\имя_компьютера\имя_экземпляра\Databases|База данных по умолчанию для данного идентификатора входа в указанном экземпляре на указанном компьютере.|  
|SQLSERVER:\SQL\имя_компьютера\имя_экземпляра\Databases\имя_базы данных|Указанная база данных в указанном экземпляре на указанном компьютере. Это также применимо к более длинным путям, например к пути, указывающему узел «Таблицы и столбцы» в базе данных.|  
  
 Например, предположим, что база данных по умолчанию для данной учетной записи Windows в экземпляре по умолчанию локального компьютера является основной. В этом случае следующие команды возвратят значение «master»:  
  
```powershell
Set-Location SQLSERVER:\SQL  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 Следующие команды возвратят базу данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]:  
  
```powershell
Set-Location SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Person  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 Командлет Invoke-Sqlcmd выдает предупреждение при использовании пути к контексту базы данных. Чтобы отключить сообщение с предупреждением, используется параметр -SuppressProviderContextWarning. Чтобы указать командлету Invoke-Sqlcmd операцию «всегда использовать для входа базу данных» по умолчанию, используется параметр -IgnoreProviderContext.  
  
## <a name="comparing-invoke-sqlcmd-and-the-sqlcmd-utility"></a>Сравнение командлета Invoke-Sqlcmd и программы sqlcmd  
 Командлет**Invoke-Sqlcmd** может использоваться для запуска многих сценариев, которые могут быть также выполнены с помощью служебной программы **sqlcmd** . Но командлет **Invoke-Sqlcmd** функционирует в среде Windows PowerShell, отличной от среды командной строки, в которой работает **sqlcmd** . Поведение **Invoke-Sqlcmd** было изменено в целях обеспечения работы в среде Windows PowerShell.  
  
 Тем не менее в командлете **Invoke-Sqlcmd** реализованы не все команды **sqlcmd**. К нереализованным командам относятся следующие: **:!**!, **: Connect**, **: Error**, **: out**, **: ED**, **: List**, **: listvar**, **: Reset**, **:p ерфтраце**и **: SERVERLIST**.  
  
 Командлет**Invoke-Sqlcmd** не инициализирует среду **sqlcmd** или переменные сценария, такие как SQLCMDDBNAME или SQLCMDWORKSTATION.  
  
 Командлет**Invoke-Sqlcmd** не отображает сообщения, такие как выходные данные инструкций PRINT, если не указан общий параметр **-Verbose** среды Windows PowerShell. Пример:  
  
```powershell
Invoke-Sqlcmd -Query "PRINT N'abc';" -Verbose  
```  
  
 В среде PowerShell требуются не все параметры **sqlcmd** . Например, среда Windows PowerShell форматирует все выходные данные командлетов, поэтому параметры форматирования **sqlcmd** не реализованы в командлете **Invoke-Sqlcmd**. В следующей таблице показана связь между параметрами **Invoke-Sqlcmd** и параметрами **sqlcmd** :  
  
|Описание|Параметр sqlcmd|Параметр Invoke-Sqlcmd|  
|-----------------|-------------------|------------------------------|  
|Сервер и имя экземпляра|-S|-ServerInstance|  
|Используемая исходная база данных|-d|-Database|  
|Выполнение указанного запроса и выход|-Q|-Query|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-U|-Username|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-P|-Password|  
|Определение переменной|-v|-Variable|  
|Интервал времени ожидания запроса|-T|-QueryTimeout|  
|Прекращение выполнения в случае ошибки|-b|-AbortOnError|  
|Выделенное административное соединение|-A|-DedicatedAdministratorConnection|  
|Отключение интерактивных команд, скрипта запуска и переменных среды|-X|-DisableCommands|  
|Отключение подстановки переменных|-X|-DisableVariables|  
|Минимальная степень серьезности для формирования отчета|-v|-SeverityLevel|  
|Минимальный уровень ошибки для формирования отчета|-M|-ErrorLevel|  
|Интервал времени ожидания входа|-l|-ConnectionTimeout|  
|Имя узла|-H|-HostName|  
|Изменение пароля и выход|-Z|-NewPassword|  
|Входной файл, содержащий запрос|-i|-InputFile|  
|Максимальная длина символьных выходных данных|-w|-MaxCharLength|  
|Максимальная длина двоичных выходных данных|-w|-MaxBinaryLength|  
|Подключаться с помощью шифрования SSL|Параметр отсутствует|-EncryptConnection|  
|Отображать сообщения об ошибках|Параметр отсутствует|-OutputSqlErrors|  
|Выводить сообщения в поток stderr|-r|Параметр отсутствует|  
|Использовать региональные настройки клиента|-R|Параметр отсутствует|  
|Выполнить указанный запрос и продолжить работу|-Q|Параметр отсутствует|  
|Кодовая страница, применяемая для выходных данных|-f|Параметр отсутствует|  
|Сменить пароль и продолжить работу|-Z|Параметр отсутствует|  
|Размер пакета|-a|Параметр отсутствует|  
|Разделитель столбцов|-S|Параметр отсутствует|  
|Управлять заголовками выходных данных|-H|Параметр отсутствует|  
|Указать управляющие символы|-k|Параметр отсутствует|  
|Постоянная ширина экрана|-y|Параметр отсутствует|  
|Переменная ширина экрана|-y|Параметр отсутствует|  
|Эхо-повтор входных данных|-E|Параметр отсутствует|  
|Включить использование заключенных в кавычки идентификаторов|-I|Параметр отсутствует|  
|Удалить конечные пробелы|-w|Параметр отсутствует|  
|Перечислить экземпляры|-l|Параметр отсутствует|  
|Форматировать выходные данные в формате Юникод|-U|Параметр отсутствует|  
|Напечатать статистику|-p|Параметр отсутствует|  
|Окончание команды|-c|Параметр отсутствует|  
|Подключение с помощью проверки подлинности Windows|-E|Параметр отсутствует|  
  
## <a name="see-also"></a>См. также:  
 [Использование командлетов ядро СУБД](../../2014/database-engine/use-the-database-engine-cmdlets.md)   
 [Программа sqlcmd](../tools/sqlcmd-utility.md)   
 [Использование программы sqlcmd](../relational-databases/scripting/sqlcmd-use-the-utility.md)  
