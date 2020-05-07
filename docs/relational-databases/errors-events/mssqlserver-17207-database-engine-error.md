---
title: MSSQLSERVER_17204 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: ''
author: PijoCoder
ms.author: mathoma
ms.openlocfilehash: b885504d8431be2df9ab0c841b47fe0eb7019932
ms.sourcegitcommit: 66407a7248118bb3e167fae76bacaa868b134734
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2020
ms.locfileid: "81728641"
---
# <a name="mssqlserver_17207"></a>MSSQLSERVER_17207
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17207|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBLKIO_OS2DISKERROR|  
|Текст сообщения|%ls: при создании или открытии файла "%ls" произошла ошибка операционной системы %ls. Определите причину, исправьте ошибку операционной системы, затем еще раз попытайтесь выполнить операцию.|  


## <a name="explanation"></a>Объяснение  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось открыть указанный файл из-за указанной ошибки ОС.  

Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается открыть базу данных и (или) файлы журнала транзакций, в событии приложения Windows или в журнале ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может появиться сообщение об ошибке 17207. Вот пример такого сообщения:

``` 
Error: 17207, Severity: 16, State: 1.
FileMgr::StartSecondaryDataFiles: Operating system error 2(The system cannot find the file specified.) occurred while creating or opening file 'F:\MSSQL\DATA\MyDB_FG1_1.ndf'. Diagnose and correct the operating system error, and retry the operation.
```

Эти ошибки могут возникнуть во время запуска экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или любой операции с базой данных, при которой выполняется попытка запустить базу данных (например, ALTER DATABASE). В некоторых сценариях могут возникнуть ошибки 17207 и 17204, а в других случаях может возникнуть только одна из них.

Если такие ошибки происходят в пользовательской базе данных, она остается в состоянии RECOVERY_PENDING, а приложения не могут получить доступ к базе данных. Если такие ошибки происходят в системной базе данных, экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не запускается и вы не можете подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это также может привести к тому, что ресурс отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перейдет в режим "вне сети".

Если проблема связана с файловой группой FileStream в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], вы увидите, что вместо имени файла указан только полный путь к каталогу. Пример приведен ниже. 
```
Error: 17207, Severity: 16, State: 1.
STREAMFCB::Startup: Operating system error 2(The system cannot find the file specified.) occurred while creating or opening file 'C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\DATA\bpa_files_test_fs_1\bpa_files_test_fs_1'. Diagnose and correct the operating system error, and retry the operation.
```

## <a name="cause"></a>Причина
Прежде чем можно будет использовать базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ее необходимо запустить. При запуске базы данных инициализируются различные структуры данных, представляющие базу данных и ее файлы, открываются все файлы, принадлежащие базе данных, и, наконец, база данных восстанавливается. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует функцию API [CreateFile](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-createfilea) в Windows для открытия файлов, принадлежащих базе данных.
 
Сообщения 17207 (и 17204) указывают на то, что при попытке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] открыть файлы базы данных во время запуска произошла ошибка.
 
Эти сообщения об ошибках содержат следующие сведения:
1. Имя функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая пытается открыть файл. В этих сообщениях об ошибках обычно содержится одно из следующих имен:
   - FCB::Open — ошибка файла при попытке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] открыть его.
   - FileMgr::StartPrimaryDataFiles — первичный файл данных или файл, принадлежащий первичной группе файлов.
   - FileMgr::StartSecondaryDataFiles — файл, принадлежащий вторичной группе файлов.
   - FileMgr::StartLogFiles — файл журнала транзакций.
   - STREAMFCB::Startup — контейнер FileStream в SQL.
   - FCB::RemoveAlternateStreams.
  
      
1. В сведениях о состоянии указаны различные данные о нескольких расположениях внутри функции, которая может создать это сообщение об ошибке.
1. Полный физический путь к файлу.
1. Идентификатор файла, соответствующий файлу.
1. Код ошибки операционной системы и описание ошибки. В некоторых экземплярах вы увидите только код ошибки.
 
Сведения об ошибках операционной системы, выводимые в этих сообщениях о них, являются основной причиной ошибки 17204. Часто такие сообщения об ошибках поступают из-за проблем с разрешениями или указания неверного пути к файлу.


## <a name="user-action"></a>Действие пользователя  
1. Для устранения ошибки 17207 нужно расшифровать соответствующий код ошибки операционной системы и провести диагностику. После устранения ошибки операционной системы можно попытаться перезапустить базу данных (например, с помощью инструкции ALTER DATABASE SET ONLINE) или экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы перевести затронутую базу данных в режим "в сети". Иногда устранить ошибку операционной системы не удается. В таком случае необходимо выполнить определенные корректирующие действия. Мы обсудим их в этом разделе.
1. Если сообщение об ошибке 17207 содержит только код ошибки, а не ее описание, можно попробовать расшифровать этот код. Для этого выполните в оболочке операционной системы команду net helpmsg <error code>. Если кодом ошибки является 8-значный код состояния, ознакомьтесь с инструкциями на [этой странице](https://devblogs.microsoft.com/oldnewthing/20061103-07/?p=29133), чтобы декодировать код состояния в ошибку ОС.
1. В случае возникновения ошибки операционной системы 5 (```Access is Denied```), рассмотрите следующие методы устранения:
   -  Проверьте разрешения, заданные в файле, просмотрев свойства файла в проводнике Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует группы Windows, чтобы подготовить службу контроля доступа для различных ресурсов файла. Убедитесь, что соответствующая группа (с именем SQLServerMSSQLUser$ComputerName$MSSQLSERVER или SQLServerMSSQLUser$ComputerName$InstanceName) имеет необходимые разрешения для файла базы данных, указанного в сообщении об ошибке. Дополнительные сведения см. в статье [Настройка разрешений файловой системы для доступа к компоненту ядра СУБД](../../2014/database-engine/configure-windows/configure-file-system-permissions-for-database-engine-access.md). Убедитесь, что группа Windows содержит учетную запись запуска службы или идентификатор безопасности службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
   -  Проверьте учетную запись пользователя, от имени которой сейчас запущена служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для получения этих сведений можно использовать диспетчер задач Windows. Найдите значение "Имя пользователя" для исполняемого файла "sqlservr.exe". Если вы недавно изменили учетную запись службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживаемым способом выполнения этой операции является использование служебной программы "Диспетчер конфигурации SQL Server". Дополнительные сведения см. в статье [Диспетчер конфигурации SQL Server](../sql-server-configuration-manager.md). 
   -  В зависимости от типа операции — открытие баз данных во время запуска сервера, присоединение базы данных, восстановление базы данных и т. д. — учетная запись, используемая для олицетворения и получения доступа к файлу базы данных, может варьироваться. Сведения о том, какая операция позволяет задавать разрешения к каким учетным записям, см. в статье [Защита данных и файлов журналов](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms189128(v=sql.105)?redirectedfrom=MSDN). Используйте такие средства, как [Process Monitor](https://docs.microsoft.com/sysinternals/downloads/procmon) из пакета Windows SysInternals, чтобы узнать, каким образом предоставляется доступ к файлу: в контексте безопасности учетной записи запуска службы экземпляра SQL Server или через олицетворенной учетной записи.

      Если SQL Server олицетворяет учетные данные пользователя, выполняющего операцию ALTER DATABASE или CREATE DATABASE, в средстве Process Monitor отобразятся следующие сведения (пример):
        ```Date & Time:      3/27/2010 8:26:08 PM
        Event Class:        File System
        Operation:          CreateFile
        Result:                ACCESS DENIED
        Path:                  C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\DATA\attach_test.mdf
        TID:                   4288
        Duration:             0.0000366
        Desired Access:Generic Read/Write
        Disposition:        Open
        Options:            Synchronous IO Non-Alert, Non-Directory File, Open No Recall
        Attributes:          N
        ShareMode:       Read
        AllocationSize:   n/a
        Impersonating: DomainName\UserName```
  
1. If you are getting ```The system cannot find the file specified``` OS error = 3:
   - Review the complete path from the error message
   - Ensure the disk drive and the folder path is visible and accessible from Windows Explorer
   - Review the Windows Event log to find out if any problems exist with this disk drive
   - If the path is incorrect and if this database already exists in the system, you can change the database file paths using the methods explained in the topic [Move Database Files](../databases/move-database-files.md). You may have to use this procedure, especially for system database files which encounter 17204 or 17207 and you are working through a disaster recovery scenario where the specified disk drives are unavailable. This topic also explains how you can identify the current location of the various system databases [master, model, tempdb, msdb and mssqlsystemresource].
   - If you see this error because the database files are missing, you have to restore the database from a valid backup.
     - If the database file associated with the error belongs to a secondary filegroup, then you can optionally mark that filegroup offline, bring the database online and then perform a restore of that filegroup alone. For more information, refer to the OFFLINE section of the topic [ALTER DATABASE File and Filegroup Options (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).
     - If the file that produced the error is a transaction log file, review the information under the sections "FOR ATTACH" and "FOR ATTACH_REBUILD_LOG" of the topic [CREATE DATABASE (Transact-SQL)](../../t-sql/statements/create-database-transact-sql.md) to understand how you can recreate the missing transaction log files.
   - Ensure that any disk or network location [like iSCSI drive] is available before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attempts to access the database files on these locations. If needed create the required dependencies in Cluster Administrator or Service Control Manager.
1. If you're getting the ```The process cannot access the file because it is being used by another process``` operating system error = 32:
   - Use a tool like [Process Explorer](https://docs.microsoft.com/sysinternals/downloads/process-explorer) or [Handle](https://docs.microsoft.com/sysinternals/downloads/handle) from Windows Sysinternals to find out if another process or service has acquired exclusive lock on this database file
   - Stop that process from accessing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database files. Common examples include anti-virus programs (see guidance for file exclusions in the following [KB article](https://support.microsoft.com/help/309422/choosing-antivirus-software-for-computers-that-run-sql-server) )
   - In a cluster environment, make sure that the sqlservr.exe process from the previous owning node has actually released the handles to the database files. Normally, this doesn't occur, but misconfigurations of the cluster or I/O paths can lead to such issues.
  
