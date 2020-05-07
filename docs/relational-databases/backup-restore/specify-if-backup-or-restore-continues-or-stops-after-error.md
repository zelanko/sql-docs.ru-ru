---
title: Настройка резервного копирования или восстановления после ошибки
description: Узнайте, как выполнить операцию резервного копирования или восстановления после обнаружения ошибки в SQL Server с помощью SQL Server Management Studio или Transact-SQL.
ms.custom: seo-lt-2019
ms.date: 12/17/2019
ms.prod: sql
ms.prod_service: backup-restore
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
ms.openlocfilehash: 0eb3b8554a0d24442d110032834006a0d8e0f7af
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "82180583"
---
# <a name="specify-backup-or-restore-to-continue-or-stop-after-error"></a>Настройка резервного копирования или восстановления для продолжения или остановки после ошибки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

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
  
 Проблемы, связанные с владельцем и разрешениями у физических файлов на устройстве резервного копирования, могут помешать операции резервного копирования. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен иметь возможность считывать и записывать данные на устройстве; учетная запись, от имени которой выполняется служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должна иметь разрешения на запись. Однако процедура [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md), добавляющая запись для устройства резервного копирования в системные таблицы, не проверяет разрешения на доступ к файлу. Проблемы физического файла устройства резервного копирования могут не проявляться до момента доступа к физическому ресурсу во время операции резервного копирования или восстановления.  
  
 RESTORE  
 Если восстанавливаемая база данных не существуют, для выполнения инструкции RESTORE у пользователя должны быть разрешения CREATE DATABASE. Если база данных существует, разрешения на выполнение инструкции RESTORE по умолчанию предоставлены членам предопределенных ролей сервера **sysadmin** и **dbcreator** , а также владельцу базы данных (**dbo**) (для параметра FROM DATABASE_SNAPSHOT база данных всегда существует).  
  
 Разрешения на выполнение инструкции RESTORE даются ролям, в которых данные о членстве всегда доступны серверу. Так как членство в предопределенной роли базы данных может быть проверено только тогда, когда база данных доступна и не повреждена, что не всегда имеет место при выполнении инструкции RESTORE, члены предопределенной роли базы данных **db_owner** не имеют разрешений RESTORE.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-specify-whether-backup-continues-or-stops-after-an-error-is-encountered"></a>Определение, продолжается или останавливается резервное копирование при возникновении ошибки  
  
1.  Выполните следующие шаги, чтобы [создать резервную копию базы данных](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
2.  На странице **Параметры** в разделе **Надежность** выберите параметр **Вычислять контрольную сумму перед записью на носитель** и **Продолжить при возникновении ошибки**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-specify-whether-a-backup-operation-continues-or-stops-after-encountering-an-error"></a>Определение, продолжает ли операция резервного копирования работу или останавливается после возникновения ошибки  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  В инструкции [BACKUP](../../t-sql/statements/backup-transact-sql.md) задайте параметр CONTINUE_AFTER ERROR для продолжения или STOP_ON_ERROR для остановки. По умолчанию в случае ошибки операция останавливается. В этом примере операция резервного копирования настраивается на продолжение работы в случае ошибки.  
  
```sql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM, CONTINUE_AFTER_ERROR;  
GO  
```  
  
#### <a name="to-specify-whether-a-restore-operation-continues-or-stops-after-encountering-an-error"></a>Определение, продолжает ли операция восстановления работу или останавливается после возникновения ошибки  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  В инструкции [RESTORE](../../t-sql/statements/restore-statements-transact-sql.md) укажите параметр CONTINUE_AFTER ERROR для продолжения или STOP_ON_ERROR для остановки. По умолчанию в случае ошибки операция останавливается. В этом примере операция восстановления настраивается на продолжение работы в случае ошибки.  
  
```sql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'   
   WITH CHECKSUM, CONTINUE_AFTER_ERROR;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкция RESTORE FILELISTONLY (Transact-SQL)](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)   
 [RESTORE HEADERONLY (Transact-SQL)](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)   
 [RESTORE LABELONLY (Transact-SQL)](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)   
 [RESTORE VERIFYONLY (Transact-SQL)](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [backupset (Transact-SQL)](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Аргументы инструкции RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-arguments-transact-sql.md)   
 [Возможные ошибки носителей во время резервного копирования и восстановления (SQL Server)](../../relational-databases/backup-restore/possible-media-errors-during-backup-and-restore-sql-server.md)   
 [Включение или отключение вычисления контрольных сумм резервных копий во время резервного копирования или восстановления (SQL Server)](../../relational-databases/backup-restore/enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
  
