---
title: Укажите, будет ли операция резервного копирования или восстановления продолжаться или остановлена после возникновения ошибки (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], backups
- backing up databases [SQL Server], errors
- backups [SQL Server], errors
- database backups [SQL Server], errors
ms.assetid: 042be17a-b9b0-4629-b6bb-b87a8bc6c316
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 79ab28861fb4ad1eb3fb166e0cccb6b30ff89f86
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62877055"
---
# <a name="specify-whether-a-backup-or-restore-operation-continues-or-stops-after-encountering-an-error-sql-server"></a>Определение, продолжает ли операция резервного копирования или восстановления работу после возникновения ошибки (SQL Server)
  В этом разделе описывается, как определить, будут ли операции резервного копирования и восстановления продолжать работу или останавливаться при ошибке в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Определение, продолжает ли операция резервного копирования или восстановления работу после возникновения ошибки, с помощью следующих средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 BACKUP  
 Разрешения BACKUP DATABASE и BACKUP LOG назначены по умолчанию членам предопределенной роли сервера **sysadmin** и предопределенным ролям базы данных **db_owner** и **db_backupoperator** .  
  
 Проблемы, связанные с владельцем и разрешениями у физических файлов на устройстве резервного копирования, могут помешать операции резервного копирования. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен иметь возможность считывать и записывать данные на устройстве; учетная запись, от имени которой выполняется служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должна иметь разрешения на запись. Однако процедура [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), добавляющая запись для устройства резервного копирования в системные таблицы, не проверяет разрешения на доступ к файлу. Проблемы физического файла устройства резервного копирования могут не проявляться до момента доступа к физическому ресурсу во время операции резервного копирования или восстановления.  
  
 RESTORE  
 Если восстанавливаемая база данных не существуют, для выполнения инструкции RESTORE у пользователя должны быть разрешения CREATE DATABASE. Если база данных существует, разрешения на выполнение инструкции RESTORE по умолчанию предоставлены членам предопределенных ролей сервера **sysadmin** и **dbcreator** , а также владельцу базы данных (**dbo**) (для параметра FROM DATABASE_SNAPSHOT база данных всегда существует).  
  
 Разрешения на выполнение инструкции RESTORE даются ролям, в которых данные о членстве всегда доступны серверу. Так как членство в предопределенной роли базы данных может быть проверено только тогда, когда база данных доступна и не повреждена, что не всегда имеет место при выполнении инструкции RESTORE, члены предопределенной роли базы данных **db_owner** не имеют разрешений RESTORE.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-specify-whether-backup-continues-or-stops-after-an-error-is-encountered"></a>Определение, продолжается или останавливается резервное копирование при возникновении ошибки  
  
1.  Выполните следующие шаги, чтобы [создать резервную копию базы данных](create-a-full-database-backup-sql-server.md).  
  
2.  На странице **Параметры** в разделе **Надежность** выберите параметр **Вычислять контрольную сумму перед записью на носитель** и **Продолжить при возникновении ошибки**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-specify-whether-a-backup-operation-continues-or-stops-after-encountering-an-error"></a>Определение, продолжает ли операция резервного копирования работу или останавливается после возникновения ошибки  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  В инструкции [BACKUP](/sql/t-sql/statements/backup-transact-sql) задайте параметр CONTINUE_AFTER ERROR для продолжения или STOP_ON_ERROR для остановки. По умолчанию в случае ошибки операция останавливается. В этом примере операция резервного копирования настраивается на продолжение работы в случае ошибки.  
  
```sql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM, CONTINUE_AFTER_ERROR;  
GO  
```  
  
#### <a name="to-specify-whether-a-restore-operation-continues-or-stops-after-encountering-an-error"></a>Определение, продолжает ли операция восстановления работу или останавливается после возникновения ошибки  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  В инструкции [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) укажите параметр CONTINUE_AFTER ERROR для продолжения или STOP_ON_ERROR для остановки. По умолчанию в случае ошибки операция останавливается. В этом примере операция восстановления настраивается на продолжение работы в случае ошибки.  
  
```sql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'   
   WITH CHECKSUM, CONTINUE_AFTER_ERROR;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкция RESTORE FILELISTONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)   
 [RESTORE HEADERONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)   
 [RESTORE LABELONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)   
 [RESTORE VERIFYONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)   
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [backupset (Transact-SQL)](/sql/relational-databases/system-tables/backupset-transact-sql)   
 [Аргументы инструкции RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql)   
 [Возможные ошибки носителей во время резервного копирования и восстановления (SQL Server)](possible-media-errors-during-backup-and-restore-sql-server.md)   
 [Включение или отключение вычисления контрольных сумм резервных копий во время резервного копирования или восстановления (SQL Server)](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
  
