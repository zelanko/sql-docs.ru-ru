---
title: Включение или отключение вычисления контрольных сумм резервных копий во время архивации или восстановления (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup checksums [SQL Server]
- disabling checksums
- checksums [SQL Server]
ms.assetid: 6786bd1e-ad97-430a-8dfb-d4ba952d6c4d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d5783f393cbbe70e89e2d1ee4b7e05481fdc3ab9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62922115"
---
# <a name="enable-or-disable-backup-checksums-during-backup-or-restore-sql-server"></a>Включение или отключение вычисления контрольных сумм резервных копий во время резервного копирования или восстановления (SQL Server)
  В этом разделе описано, как включить или отключить контрольные суммы резервных копий при резервном копировании или восстановлении базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Включение или отключение расчета контрольных сумм резервных копий**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 BACKUP  
 Разрешения BACKUP DATABASE и BACKUP LOG назначены по умолчанию членам предопределенной роли сервера **sysadmin** и предопределенным ролям базы данных **db_owner** и **db_backupoperator** .  
  
 Проблемы, связанные с владельцем и разрешениями у физических файлов на устройстве резервного копирования, могут помешать операции резервного копирования. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен иметь возможность считывать и записывать данные на устройстве; учетная запись, от имени которой выполняется служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должна иметь разрешения на запись. Однако процедура [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), добавляющая запись для устройства резервного копирования в системные таблицы, не проверяет разрешения на доступ к файлу. Проблемы физического файла устройства резервного копирования могут не проявляться до момента доступа к физическому ресурсу во время операции резервного копирования или восстановления.  
  
 RESTORE  
 Если восстанавливаемая база данных не существуют, для выполнения инструкции RESTORE у пользователя должны быть разрешения CREATE DATABASE. Если база данных существует, разрешения на выполнение инструкции RESTORE по умолчанию предоставлены членам предопределенных ролей сервера **sysadmin** и **dbcreator** , а также владельцу базы данных (**dbo**) (для параметра FROM DATABASE_SNAPSHOT база данных всегда существует).  
  
 Разрешения на выполнение инструкции RESTORE даются ролям, в которых данные о членстве всегда доступны серверу. Так как членство в предопределенной роли базы данных может быть проверено только тогда, когда база данных доступна и не повреждена, что не всегда имеет место при выполнении инструкции RESTORE, члены предопределенной роли базы данных **db_owner** не имеют разрешений RESTORE.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-enable-or-disable-checksums-during-a-backup-operation"></a>Включение или отключение вычисления контрольных сумм во время создания резервной копии  
  
1.  Выполните следующие шаги, чтобы [создать резервную копию базы данных](create-a-full-database-backup-sql-server.md).  
  
2.  На странице **Параметры** в разделе **Надежность** выберите параметр **Вычислять контрольную сумму перед записью на носитель**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-enable-or-disable-backup-checksum-for-a-backup-operation"></a>Включение или отключение вычисления контрольных сумм для операции создания резервной копии  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Чтобы включить контрольные суммы резервных копий в инструкции [BACKUP](/sql/t-sql/statements/backup-transact-sql) , укажите параметр WITH CHECKSUM. Чтобы отключить контрольные суммы резервных копий, укажите параметр WITH NO_CHECKSUM. Это поведение по умолчанию для всех, за исключением сжатых резервных копий. В следующем примере указывается, что контрольные суммы будут вычисляться.  
  
```sql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
#### <a name="to-enable-or-disable-backup-checksum-for-a-restore-operation"></a>Включение или отключение вычисления контрольных сумм для операции восстановления из резервной копии  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Чтобы включить контрольные суммы резервных копий в инструкции [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) , укажите параметр WITH CHECKSUM. Это поведение по умолчанию для сжатых резервных копий. Чтобы отключить контрольные суммы резервных копий, укажите параметр WITH NO_CHECKSUM. Это поведение по умолчанию для всех, за исключением сжатых резервных копий. В следующем примере указывается, что контрольные суммы резервных копий будут вычисляться.  
  
```sql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
> [!WARNING]  
>  Если явно запрашивается CHECKSUM для операции восстановления и если резервная копия содержит контрольные суммы, то проверяются контрольные суммы и резервной копии, и страниц, как в случае по умолчанию. Однако если в резервном наборе данных нет контрольных сумм, такая операция восстановления завершается аварийно с сообщением об отсутствии контрольных сумм.  
  
## <a name="see-also"></a>См. также:  
 [Инструкция RESTORE FILELISTONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)   
 [RESTORE HEADERONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)   
 [RESTORE LABELONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)   
 [RESTORE VERIFYONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)   
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [backupset (Transact-SQL)](/sql/relational-databases/system-tables/backupset-transact-sql)   
 [Аргументы инструкции RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql)   
 [Возможные ошибки носителей во время резервного копирования и восстановления (SQL Server)](possible-media-errors-during-backup-and-restore-sql-server.md)   
 [Определение, продолжает ли операция резервного копирования или восстановления работу после возникновения ошибки (SQL Server)](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
  
