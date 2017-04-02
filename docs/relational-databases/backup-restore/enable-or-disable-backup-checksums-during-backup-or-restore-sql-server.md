---
title: "Включение или отключение вычисления контрольных сумм резервных копий во время резервного копирования или восстановления (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "контрольные суммы резервных копий [SQL Server]"
  - "отключение расчета контрольных сумм"
  - "контрольные суммы [SQL Server]"
ms.assetid: 6786bd1e-ad97-430a-8dfb-d4ba952d6c4d
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# Включение или отключение вычисления контрольных сумм резервных копий во время резервного копирования или восстановления (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этом разделе описано, как включить или отключить контрольные суммы резервных копий при резервном копировании или восстановлении базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Включение или отключение расчета контрольных сумм резервных копий**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 BACKUP  
 Разрешения BACKUP DATABASE и BACKUP LOG назначены по умолчанию членам предопределенной роли сервера **sysadmin** и предопределенным ролям базы данных **db_owner** и **db_backupoperator**.  
  
 Проблемы, связанные с владельцем и разрешениями у физических файлов на устройстве резервного копирования, могут помешать операции резервного копирования. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен иметь возможность считывать и записывать данные на устройстве; учетная запись, от имени которой выполняется служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должна иметь разрешения на запись. Однако процедура [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md), добавляющая запись для устройства резервного копирования в системные таблицы, не проверяет разрешения на доступ к файлу. Проблемы физического файла устройства резервного копирования могут не проявляться до момента доступа к физическому ресурсу во время операции резервного копирования или восстановления.  
  
 RESTORE  
 Если восстанавливаемая база данных не существуют, для выполнения инструкции RESTORE у пользователя должны быть разрешения CREATE DATABASE. Если база данных существует, разрешения на выполнение инструкции RESTORE по умолчанию предоставлены членам предопределенных ролей сервера **sysadmin** и **dbcreator**, а также владельцу базы данных (**dbo**) (для параметра FROM DATABASE_SNAPSHOT база данных всегда существует).  
  
 Разрешения на выполнение инструкции RESTORE даются ролям, в которых данные о членстве всегда доступны серверу. Так как членство в предопределенной роли базы данных может быть проверено только тогда, когда база данных доступна и не повреждена, что не всегда имеет место при выполнении инструкции RESTORE, члены предопределенной роли базы данных **db_owner** не имеют разрешений RESTORE.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Включение или отключение вычисления контрольных сумм во время создания резервной копии  
  
1.  Выполните следующие шаги, чтобы [создать резервную копию базы данных](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
2.  На странице **Параметры** в разделе **Надежность** выберите параметр **Вычислять контрольную сумму перед записью на носитель**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Включение или отключение вычисления контрольных сумм для операции создания резервной копии  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Чтобы включить контрольные суммы резервных копий в инструкции [BACKUP](../../t-sql/statements/backup-transact-sql.md) , укажите параметр WITH CHECKSUM. Чтобы отключить контрольные суммы резервных копий, укажите параметр WITH NO_CHECKSUM. Это поведение по умолчанию для всех, за исключением сжатых резервных копий. В следующем примере указывается, что контрольные суммы будут вычисляться.  
  
```tsql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
#### Включение или отключение вычисления контрольных сумм для операции восстановления из резервной копии  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Чтобы включить контрольные суммы резервных копий в инструкции [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) , укажите параметр WITH CHECKSUM. Это поведение по умолчанию для сжатых резервных копий. Чтобы отключить контрольные суммы резервных копий, укажите параметр WITH NO_CHECKSUM. Это поведение по умолчанию для всех, за исключением сжатых резервных копий. В следующем примере указывается, что контрольные суммы резервных копий будут вычисляться.  
  
```tsql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
> [!WARNING]  
>  Если явно запрашивается CHECKSUM для операции восстановления и если резервная копия содержит контрольные суммы, то проверяются контрольные суммы и резервной копии, и страниц, как в случае по умолчанию. Однако если в резервном наборе данных нет контрольных сумм, такая операция восстановления завершается аварийно с сообщением об отсутствии контрольных сумм.  
  
## См. также:  
 [RESTORE FILELISTONLY (Transact-SQL)](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)   
 [RESTORE HEADERONLY (Transact-SQL)](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md)   
 [RESTORE LABELONLY (Transact-SQL)](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md)   
 [RESTORE VERIFYONLY (Transact-SQL)](../Topic/RESTORE%20VERIFYONLY%20\(Transact-SQL\).md)   
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [backupset (Transact-SQL)](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Аргументы RESTORE (Transact-SQL)](../Topic/RESTORE%20Arguments%20\(Transact-SQL\).md)   
 [Возможные ошибки носителей во время резервного копирования и восстановления (SQL Server)](../../relational-databases/backup-restore/possible-media-errors-during-backup-and-restore-sql-server.md)   
 [Определение, продолжает ли операция резервного копирования или восстановления работу после возникновения ошибки (SQL Server)](../../relational-databases/backup-restore/specify if backup or restore continues or stops after error.md)  
  
  