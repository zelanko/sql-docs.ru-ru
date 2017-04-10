---
title: "Командлет Backup-ASDatabase | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 03d58a82-021c-4e13-b265-c084f42a8bb2
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 13
---
# Командлет Backup-ASDatabase
  Создайте резервную копию многомерной базы данных служб Analysis Services или табличной базы данных в файле резервной копии служб Analysis Services (ABF-файле).  
  
## Синтаксис  
 `Backup-ASDatabase [-BackupFile] <string> [-Name] <string> [-AllowOverwrite <SwitchParameter>] [-BackupRemotePartitions <SwitchParameter>] [-ApplyCompression <SwitchParameter>] [-FilePassword <SecureString>] [-Locations <Microsoft.AnalysisServices.BackupLocation[]>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
 `Backup-ASDatabase –Database <Microsoft.AnalysisServices.Database> [-AllowOverwrite <SwitchParameter>] [-BackupRemotePartitions <SwitchParameter>] [-ApplyCompression <SwitchParameter>] [-FilePassword <SecureString>] [-Locations <Microsoft.AnalysisServices.BackupLocation[]>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
## Description  
 Дает возможность системному администратору служб Analysis Services создать резервную копию многомерной или табличной базы данных в файле резервной копии. Если расположение не указано, по умолчанию используется расположение резервных копий, заданное во время установки.  
  
 Файлы, резервные копии которых создаются, можно шифровать. Используйте параметр –FilePassword, чтобы зашифровать файл. При последующем восстановлении файла необходимо указать тот же пароль, который был использован для его шифрования.  
  
 Этот командлет поддерживает параметр –Credential, который можно использовать, если экземпляр служб Analysis Services настроен для доступа по протоколу HTTP. Параметр –Credential принимает объект PSCredential, который содержит идентификатор пользователя Windows. Службы IIS будут олицетворять этого пользователя при подключении к службам Analysis Services. Для выполнения резервного копирования идентификатору должны быть предоставлены разрешения системного администратора на экземпляр служб Analysis Services.  
  
## Параметры  
  
### -BackupFile \<строка>  
 Задает путь и имя файла резервной копии. Если указать просто имя файла без пути, будет использоваться расположение резервной копии по умолчанию. Этот параметр используется только с параметром «–Name».  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -Name \<строка>  
 Указывает базу данных служб Analysis Services, резервная копия которой создается. Задать базу данных можно с помощью параметра «–Database» или параметра «–Name», если нужно передать имя в виде строки.  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|1|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -AllowOverwrite \<переключатель>  
 Перезаписывает одноименный файл резервной копии.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -BackupRemotePartitions \<переключатель>  
 Указывает, включать ли удаленные разделы в резервную копию.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -ApplyCompression \<переключатель>  
 Указывает, сжимать ли файл резервной копии.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -FilePassword \<строка безопасности>  
 Задает пароль, который должен использоваться при шифровании файла резервной копии.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -Locations \<Microsoft.AnalysisServices.BackupLocation[]>  
 Указывает расположение, в котором будет храниться файл резервной копии.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -Server \<строка>  
 Указывает экземпляр служб Analysis Services, к которому подключится командлет и где он будет выполняться. Если имя сервера не указано, произойдет подключение к серверу localhost. Для экземпляров по умолчанию достаточно указать имя сервера. Для именованных экземпляров используйте формат имя_сервера\имя_экземпляра. Для HTTP-соединений используйте формат http[s]://server[:port]/virtualdirectory/msmdpump.dll.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию|localhost|  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -Credential \<учетные данные ПК>  
 Указывает объект PSCredential, который содержит имя пользователя и пароль Windows. Укажите этот параметр, только если экземпляр служб Analysis Services настроен для доступа HTTP с использованием обычной проверки подлинности. Для соединений в собственном режиме, в которых используются интегрированные функции безопасности, этот параметр не учитываются.  
  
 Если этот параметр указан, учетные данные, которые он содержит, добавляются в строку подключения. Службы IIS будут олицетворять этого пользователя при соединении со службами Analysis Services. Если учетные данные не будут указаны, будут использованы учетные данные по умолчанию для пользователя, который запускает это средство.  
  
 Для использования этого параметра необходимо сначала создать объект PSCredential с помощью командлета Get-Credential, чтобы указать имя пользователя и пароль (например, `$Cred=Get-Credential “adventure-works\admin”`. этот объект можно затем передать по конвейеру в параметр –Credential `(-Credential:$Cred`.  
  
 Дополнительные сведения о проверке подлинности и использовании учетных данных см. в разделе [Создание скриптов PowerShell в службах Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md). Дополнительные сведения о HTTP-доступе см. в разделе [Настройка HTTP-доступа к службам Analysis Services в службах Internet Information Services (IIS) 8.0](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md).  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|True (ByValue)|  
|Принимать символы-шаблоны?|false|  
  
### -Database \<Microsoft.AnalysisServices.Database[]>  
 Указывает объект базы данных служб Analysis Services, резервная копия которого создается. Задать базу данных можно с помощью параметра «-Database» или параметра «–Name». Чтобы передать имя базы данных по конвейеру, используйте параметр «–Database».  
  
|||  
|-|-|  
|Обязательно?|true|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true|  
|Принимать символы-шаблоны?|false|  
  
### \<Общие параметры>  
 Этот командлет поддерживает общие параметры: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer и -OutVariable. Дополнительные сведения см. в разделе [Об общих параметрах](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|Microsoft.AnalysisServices.Database<br /><br /> Можно передать по конвейеру имена нескольких баз данных, резервные копии которых нужно создать, например всех баз данных определенного экземпляра.|  
|Выходные данные|Нет.|  
  
## Пример 1  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default >backup-asdatabase awdb-20110930.abf “Adventure Works” -AllowOverwrite -ApplyCompression  
```  
  
 Эта команда создает резервную копию базы данных Adventure Works в ABF-файле в расположении резервных копий по умолчанию. Если в этом расположении уже существует файл с таким именем, он перезаписывается.  
  
## Пример 2  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default >$AWDB = get-item “databases\Adventure Works”   
PS SQLSERVER:\SQLAS\Localhost\default >Backup-asdatabase –database:$AWDB –AllowOverwrite  
```  
  
 В этой команде используется параметр «–Database» вместо «-Backupfile» и «-Name». Используйте параметр «–Database», если хотите передать имя базы данных в командлет по конвейеру.  
  
## Пример 3  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default\databases >dir * | backup-asdatabase  
```  
  
 Эта команда создает резервные копии всех баз данных на локальном сервере.  
  
## Пример 4  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default > $pwd = read-host –AsSecureString –Prompt “Password”   
PS SQLSERVER:\SQLAS\Localhost\default > $pwd -is [System.IDisposable]   
PS SQLSERVER:\SQLAS\Localhost\default > backup-asdatabase –backupfile test.abf –name contoso_retail –filepassword:$pwd server myremoteserver  
PS SQLSERVER:\SQLAS\Localhost\default >$pwd.Dispose()  
PS SQLSERVER:\SQLAS\Localhost\default >Remove-Variable –Name pwd  
```  
  
 Строки 1 и 2 используются для запроса пароля, который будет использован для шифрования файла.  
  
 Строка 3 выполняет резервное копирование образца базы данных Contoso_Retail на удаленном сервере служб Analysis Services в файл резервной копии служб Analysis Services с именем test.abf, который также располагается на удаленном сервере. Этот файл сохраняется в папке резервных копий по умолчанию на экземпляре по умолчанию.  
  
 Строки 4 и 5 удаляют пароль.  
  
## См. также  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Управление табличными моделями с помощью PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  