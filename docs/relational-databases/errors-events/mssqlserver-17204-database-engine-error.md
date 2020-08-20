---
description: MSSQLSERVER_17204
title: MSSQLSERVER_17204 | Документация Майкрософт
ms.custom: ''
ms.date: 07/25/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: 40db66f9-dd5e-478c-891e-a06d363a2552
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3853181bad494232b1874a7e19da9652738b546f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456509"
---
# <a name="mssqlserver_17204"></a>MSSQLSERVER_17204
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |
| :-------- | :---- |
|Название продукта|SQL Server|  
|Идентификатор события|17204|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBLKIO_DEVOPENFAILED|  
|Текст сообщения|%ls: не удалось открыть файл %ls для номера файла %d.  Ошибка операционной системы: %ls.|  
  
## <a name="explanation"></a>Объяснение  
SQL Server не удалось открыть указанный файл из-за указанной ошибки ОС.  

Если SQL Server не удается открыть базу данных и (или) файлы журнала транзакций, в событии приложения Windows или в журнале ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может отобразиться ошибка 17204. Ниже приведен пример такой ошибки:

``` 
Error: 17204, Severity: 16, State: 1.
FCB::Open failed: Could not open file c:\Program Files\Microsoft SQL Server\MSSQL10.SQL2008\MSSQL\data\MyDB_Prm.mdf for file number 1.  OS error: 5(Access is denied.).
```

Эти ошибки могут возникнуть во время запуска экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или любой операции с базой данных, при которой выполняется попытка запустить базу данных (например, ALTER DATABASE). В некоторых сценариях могут возникать ошибки 17204 и 17207, а в некоторых — лишь одна из них.

Если такие ошибки происходят в пользовательской базе данных, она остается в состоянии RECOVERY_PENDING, а приложения не могут получить доступ к базе данных. Если такие ошибки происходят в системной базе данных, экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не запускается и вы не можете подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сбой системной базы данных может привести к переходу ресурса отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в автономный режим.

## <a name="cause"></a>Причина
Прежде чем можно будет использовать базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ее необходимо запустить. Процесс запуска базы данных включает в себя следующее: 
1. инициализацию различных структур данных, представляющих базу данных и ее файлы;
1. открытие всех файлов, принадлежащих к базе данных;
1. выполнение восстановления базы данных. 

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует функцию API [CreateFile](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-createfilea) в Windows для открытия файлов, принадлежащих базе данных.
 
Сообщения 17204 (и 17207) указывают на то, что при попытке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] открыть файлы базы данных во время запуска произошла ошибка.
 
Эти сообщения об ошибках содержат следующие сведения:
1. Имя функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая пытается открыть файл. В этих сообщениях об ошибках обычно содержится одно из следующих имен:
   - В FCB::Open — произошла ошибка при попытке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] открыть файл.
   - FileMgr::StartPrimaryDataFiles — первичный файл данных или файл, принадлежащий первичной файловой группе.
   - FileMgr::StartSecondaryDataFiles — файл, принадлежащий вторичной файловой группе.
   - FileMgr::StartLogFiles — файл журнала транзакций.
   - STREAMFCB::Startup — контейнер SQL FileStream.
   - FCB::RemoveAlternateStreams
  
      
1. В сведениях о состоянии указаны различные данные о нескольких расположениях внутри функции, которая может создать это сообщение об ошибке.
1. Полный физический путь к файлу.
1. Идентификатор файла, соответствующий файлу.
1. Код ошибки операционной системы и описание ошибки. В некоторых экземплярах вы увидите только код ошибки.
 
Сведения об ошибках операционной системы, выводимые в этих сообщениях о них, являются основной причиной ошибки 17204. Распространенными причинами этих сообщений об ошибках являются проблемы с разрешениями или неверный путь к файлу.


## <a name="user-action"></a>Действие пользователя  
1. Для устранения ошибки 17204 необходимо узнать соответствующий код ошибки операционной системы. А затем выполнить диагностику этой ошибки. После устранения ошибки операционной системы можно попытаться перезапустить базу данных (например, с помощью инструкции ALTER DATABASE SET ONLINE) или экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы перевести затронутую базу данных в режим "в сети". Иногда устранить ошибку операционной системы не удается. В таком случае необходимо выполнить определенные корректирующие действия. Мы обсудим их в этом разделе.
1. Если сообщение об ошибке 17204 содержит лишь код ошибки, а не ее описание, можно попробовать разрешить код ошибки, выполнив в оболочке операционной системы эту команду: net helpmsg <error code>. Если кодом ошибки является 8-значный код состояния, ознакомьтесь с инструкциями на [этой странице](https://devblogs.microsoft.com/oldnewthing/20061103-07/?p=29133), чтобы декодировать код состояния в ошибку ОС.
1. В случае возникновения ошибки операционной системы 5 (`Access is Denied`), рассмотрите следующие методы устранения:
   -  Проверьте разрешения, заданные в файле, просмотрев свойства файла в проводнике Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует группы Windows, чтобы подготовить службу контроля доступа для различных ресурсов файла. Убедитесь, что соответствующая группа (с именем SQLServerMSSQLUser$ComputerName$MSSQLSERVER или SQLServerMSSQLUser$ComputerName$InstanceName) имеет необходимые разрешения для файла базы данных, указанного в сообщении об ошибке. Дополнительные сведения см. в статье [Настройка разрешений файловой системы для доступа к компоненту ядра СУБД](/previous-versions/sql/2014/database-engine/configure-windows/configure-file-system-permissions-for-database-engine-access?view=sql-server-2014). Убедитесь, что группа Windows содержит учетную запись запуска службы или идентификатор безопасности службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
   -  Проверьте учетную запись пользователя, от имени которой сейчас запущена служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для получения этих сведений можно использовать диспетчер задач Windows. Найдите значение "Имя пользователя" для исполняемого файла "sqlservr.exe". Если вы недавно изменили учетную запись службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживаемым способом выполнения этой операции является использование служебной программы "Диспетчер конфигурации SQL Server". Дополнительные сведения см. в статье [Диспетчер конфигурации SQL Server](../sql-server-configuration-manager.md). 
   -  В зависимости от типа операции — открытие баз данных во время запуска сервера, присоединение базы данных, восстановление базы данных и т. д. — учетная запись, используемая для олицетворения и получения доступа к файлу базы данных, может варьироваться. Сведения о том, какая операция позволяет задавать разрешения к каким учетным записям, см. в статье [Защита данных и файлов журналов](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms189128(v=sql.105)?redirectedfrom=MSDN). Используйте такие средства, как [Process Monitor](https://docs.microsoft.com/sysinternals/downloads/procmon), чтобы узнать, каким образом предоставляется доступ к файлу: в контексте безопасности учетной записи запуска службы экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (или идентификатора безопасности службы) либо олицетворенной учетной записи.

      Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] олицетворяет учетные данные пользователя, выполняющего операцию ALTER DATABASE или CREATE DATABASE, в средстве Process Monitor отобразятся следующие сведения (пример):
        ```Date & Time:      3/27/2010 8:26:08 PM
        Event Class:        File System
        Operation:          CreateFile
        Result:                ACCESS DENIED
        Path:                  C:\Program Files\Microsoft SQL Server\MSSQL10.SQL2008\MSSQL\DATA\attach_test.mdf
        TID:                   4288
        Duration:             0.0000366
        Desired Access:Generic Read/Write
        Disposition:        Open
        Options:            Synchronous IO Non-Alert, Non-Directory File, Open No Recall
        Attributes:          N
        ShareMode:       Read
        AllocationSize:   n/a
        Impersonating: DomainName\UserName```
  
1. If you are getting `The system cannot find the file specified` OS error = 3:
   - Review the complete path from the error message
   - Ensure the disk drive and the folder path is visible and accessible from Windows Explorer
   - Review the Windows Event log to find out if any problems exist with this disk drive
   - If the path is incorrect and if this database already exists in the system, you can change the database file paths using the methods explained in the topic [Move Database Files](../databases/move-database-files.md). You may have to use this procedure, especially for system database files that encounter 17204 or 17207 and you are working through a disaster recovery scenario where the specified disk drives are unavailable. This topic also explains how you can identify the current location of the various system databases [master, model, tempdb, msdb and mssqlsystemresource].
   - If you see this error because the database files are missing, you have to restore the database from a valid backup.
     - If the database file associated with the error belongs to a secondary filegroup, then you can optionally mark that filegroup offline, bring the database online and then perform a restore of that filegroup alone. For more information, refer to the OFFLINE section of the topic [ALTER DATABASE File and Filegroup Options (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).
     - If the file that produced the error is a transaction log file, review the information under the sections "FOR ATTACH" and "FOR ATTACH_REBUILD_LOG" of the topic [CREATE DATABASE (Transact-SQL)](../../t-sql/statements/create-database-transact-sql.md) to understand how you can recreate the missing transaction log files.
   - Ensure that any disk or network location [like iSCSI drive] is available before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attempts to access the database files on these locations. If needed create the required dependencies in Cluster Administrator or Service Control Manager.
1. If you're getting the `The process cannot access the file because it is being used by another process` operating system error = 32:
   - Use a tool like [Process Explorer](https://docs.microsoft.com/sysinternals/downloads/process-explorer) or [Handle](https://docs.microsoft.com/sysinternals/downloads/handle) from Windows Sysinternals to find out if another process or service has acquired exclusive lock on this database file
   - Stop that process from accessing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database files. Common examples include anti-virus programs (see guidance for file exclusions in the following [KB article](https://support.microsoft.com/help/309422/choosing-antivirus-software-for-computers-that-run-sql-server) )
   - In a cluster environment, make sure that the sqlservr.exe process from the previous owning node has actually released the handles to the database files. Normally, this doesn't occur, but misconfigurations of the cluster or I/O paths can lead to such issues.
  
