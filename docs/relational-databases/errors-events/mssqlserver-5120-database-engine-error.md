---
title: MSSQLSERVER_5228 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5120 (Database Engine error)
ms.assetid: ''
author: PijoCoder
ms.author: mathoma
ms.openlocfilehash: ff8fb262b643390f2914a4a5e6c42dcc887206f8
ms.sourcegitcommit: 66407a7248118bb3e167fae76bacaa868b134734
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2020
ms.locfileid: "81728621"
---
# <a name="mssqlserver_5120"></a>MSSQLSERVER_5120
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|5120|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DSK_FCB_FAILURE|  
|Текст сообщения|Ошибка таблицы: Не удалось открыть физический файл "%.*ls". Ошибка операционной системы %d: "%ls".|  
  
## <a name="explanation"></a>Объяснение  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось открыть файл базы данных.  Ошибка операционной системы, о которой говорится в сообщении, указывает на конкретные первопричины сбоя. Обычно эта ошибка происходит вместе с другими ошибками, такими как [17204](mssqlserver-17204-database-engine-error.md) или [17207](mssqlserver-17207-database-engine-error.md).
  
## <a name="user-action"></a>Действие пользователя  
  
  Определите причину, исправьте ошибку операционной системы, затем еще раз попытайтесь выполнить операцию. Есть несколько состояний, сведения о которых могут помочь корпорации Майкрософт уменьшить область изучения для определения ошибки. 
  
### <a name="access-is-denied"></a>Доступ запрещен 
В случае возникновения ошибки операционной системы 5 (```Access is Denied```), рассмотрите следующие методы устранения:
   -  Проверьте разрешения, заданные в файле, просмотрев свойства файла в проводнике Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует группы Windows, чтобы подготовить службу контроля доступа для различных ресурсов файла. Убедитесь, что соответствующая группа (с именем SQLServerMSSQLUser$ComputerName$MSSQLSERVER или SQLServerMSSQLUser$ComputerName$InstanceName) имеет необходимые разрешения для файла базы данных, указанного в сообщении об ошибке. Дополнительные сведения см. в статье [Настройка разрешений файловой системы для доступа к компоненту ядра СУБД](../../2014/database-engine/configure-windows/configure-file-system-permissions-for-database-engine-access.md). Убедитесь, что группа Windows содержит учетную запись запуска службы или идентификатор безопасности службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
   -  Проверьте учетную запись пользователя, от имени которой сейчас запущена служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для получения этих сведений можно использовать диспетчер задач Windows. Найдите значение "Имя пользователя" для исполняемого файла "sqlservr.exe". Если вы недавно изменили учетную запись службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживаемым способом выполнения этой операции является использование служебной программы [Диспетчер конфигурации SQL Server](../sql-server-configuration-manager.md). 
   -  В зависимости от типа операции — открытие баз данных во время запуска сервера, присоединение базы данных, восстановление базы данных и т. д. — учетная запись, используемая для олицетворения и получения доступа к файлу базы данных, может варьироваться. Сведения о том, какая операция позволяет задавать разрешения к каким учетным записям, см. в статье [Защита данных и файлов журналов](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms189128(v=sql.105)?redirectedfrom=MSDN). Используйте такие средства, как [Process Monitor](https://docs.microsoft.com/sysinternals/downloads/procmon), чтобы узнать, каким образом предоставляется доступ к файлу: в контексте безопасности учетной записи запуска службы экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (или идентификатора безопасности службы) либо олицетворенной учетной записи.

      Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] олицетворяет учетные данные для входа пользователя, выполняющего операцию ALTER DATABASE или CREATE DATABASE, в средстве Process Monitor отобразятся следующие сведения. Пример:
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
  
  
### Attaching Files that Reside on a Network-attached storage  
If you cannot re-attach a database that resides on network-attached storage, a message like this may be logged in the Application log:

```Msg 5120, Level 16, State 101, Line 1 Unable to open the physical file "\\servername\sharename\filename.mdf". Operating system error 5: (Access is denied.).```

This problem occurs because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resets the file permissions when the database is detached. When you try to reattach the database, a failure occurs because of limited share permissions.

To resolve, follow these steps:
1. Use the -T startup option to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Use this startup option to turn on trace flag 1802 in [SQL Server Configuration Manager](../sql-server-configuration-manager.md) (see [Trace Flags](../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md) for information on 1802). For more information about how to change the startup parameters, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)

2. Use the following command to detach the database.
```tsql
 exec sp_detach_db DatabaseName
 go 
```

3. Восстановить подключение базы данных можно с помощью приведенной ниже команды.
```tsql
exec sp_attach_db DatabaseName, '\\Network-attached storage_Path\DatabaseMDFFile.mdf', '\\Network-attached storage_Path\DatabaseLDFFile.ldf'
go
```
 
