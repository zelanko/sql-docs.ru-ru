---
title: Выполнение полного восстановления базы данных (простая модель восстановления) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- complete database restores
- database restores [SQL Server], complete database
- restoring databases [SQL Server], complete database
- simple recovery model [SQL Server]
- restoring [SQL Server], database
ms.assetid: 49828927-1727-4d1d-9ef5-3de43f68c026
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67eee8d7d6f44c9ff83795bf2a8bd612309bf0a5
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84959004"
---
# <a name="complete-database-restores-simple-recovery-model"></a>Выполнение полного восстановления базы данных (Простая модель восстановления)
  Задача полного восстановления — восстановить базу данных целиком. В период восстановления база данных находится вне сети. Прежде чем какая-либо часть базы данных перейдет в режим «в сети», все данные восстанавливаются до точки согласования, в которой все части базы данных находятся в одном и том же моменте времени и в которой нет незафиксированных транзакций.  
  
 При использовании простой модели восстановления база данных не может быть восстановлена к определенному моменту времени внутри заданной резервной копии.  
  
> [!IMPORTANT]  
>  Не рекомендуется подключать или восстанавливать базы данных, полученные из неизвестных или ненадежных источников. В этих базах данных может содержаться вредоносный код, вызывающий выполнение непредусмотренных инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)] или появление ошибок путем изменения схемы или физической структуры базы данных. Перед тем как использовать базу данных, полученную из неизвестного или ненадежного источника, выполните на тестовом сервере инструкцию [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) для этой базы данных, а также изучите исходный код в базе данных, например хранимые процедуры и другой пользовательский код.  
  

  
> [!NOTE]  
>  Сведения о поддержке резервных копий более ранних версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]см. в подразделе "Поддержка совместимости" раздела [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql).  
  
##  <a name="overview-of-database-restore-under-the-simple-recovery-model"></a><a name="Overview"></a> Общие сведения о восстановлении баз данных в рамках простой модели восстановления  
 Полное восстановление базы данных при использовании простой модели восстановления состоит из одной или двух инструкций [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) , в зависимости от того, нужно ли выполнять восстановление разностной резервной копии базы данных. При использовании только полной резервной копии базы данных просто восстановите последнюю резервную копию, как показано на следующем рисунке.  
  
 ![Восстановление только полной резервной копии базы данных](../../database-engine/media/bnrr-rmsimple1-fulldbbu.gif "Восстановление только полной резервной копии базы данных")  
  
 Если используется также восстановление разностной резервной копии базы данных, восстановите самую последнюю полную резервную копию базы данных без восстановления самой базы данных, а затем восстановите самую последнюю разностную резервную копию базы данных и восстановите саму базу данных. На следующем рисунке показан этот процесс.  
  
 ![Восстановление полной и разностной резервных копий базы данных](../../database-engine/media/bnrr-rmsimple2-diffdbbu.gif "Восстановление полной и разностной резервных копий базы данных")  
  
> [!NOTE]  
>  Если база данных восстанавливается на другой экземпляр сервера, см. раздел [Копирование баз данных путем создания и восстановления резервных копий](../databases/copy-databases-with-backup-and-restore.md).  
  
###  <a name="basic-transact-sql-restore-syntax"></a><a name="TsqlSyntax"></a> Базовый синтаксис инструкции Transact-SQL RESTORE  
 Базовый синтаксис инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) для восстановления полной резервной копии базы данных выглядит следующим образом:  
  
 RESTORE DATABASE *имя_базы_данных* FROM *устройство_резервного_копирования* [ WITH NORECOVERY ]  
  
> [!NOTE]  
>  Если планируется также восстановление разностной резервной копии базы данных, используйте параметр WITH NORECOVERY.  
  
 Базовый синтаксис инструкции [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) восстановления из резервной копии базы данных:  
  
 RESTORE DATABASE *имя_базы_данных* FROM *устройство_резервного_копирования* WITH RECOVERY  
  
###  <a name="example-transact-sql"></a><a name="Example"></a> Примеры (Transact-SQL)  
 В следующем примере сначала показано, как использовать инструкцию [BACKUP](/sql/t-sql/statements/backup-transact-sql) , чтобы создать полную резервную копию базы данных и разностную резервную копию базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Затем в примере восстанавливаются резервные копии в последовательности восстановления. База данных восстанавливается к состоянию на момент создания разностной резервной копии базы данных.  
  
 В  примере показаны критически важные параметры в последовательности восстановления для полного восстановления базы данных. *Последовательность восстановления* состоит из одной или нескольких операций восстановления, которые выполняют перемещение данных в одном или нескольких этапах восстановления. Синтаксис и прочие подробности, несущественные для данной цели, опущены. При восстановлении базы данных рекомендуется явно указать параметр RECOVERY, несмотря на то, что он подразумевается по умолчанию.  
  
> [!NOTE]  
>  Пример начинается с инструкции [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) , которая устанавливает модель восстановления `SIMPLE`.  
  
```  
USE master;  
--Make sure the database is using the simple recovery model.  
ALTER DATABASE AdventureWorks2012 SET RECOVERY SIMPLE;  
GO  
-- Back up the full AdventureWorks2012 database.  
BACKUP DATABASE AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
  WITH FORMAT;  
GO  
--Create a differential database backup.  
BACKUP DATABASE AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'  
   WITH DIFFERENTIAL;  
GO  
--Restore the full database backup (from backup set 1).  
RESTORE DATABASE AdventureWorks2012   
FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
   WITH FILE=1, NORECOVERY;  
--Restore the differential backup (from backup set 2).  
RESTORE DATABASE AdventureWorks2012   
FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
   WITH FILE=2, RECOVERY;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
 **Восстановление полной резервной копии базы данных**  
  
-   [Восстановление резервной копии базы данных в простой модели восстановления (Transact-SQL)](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [Восстановление резервной копии базы данных &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)  
  
-   [Восстановление базы данных в новом расположении (SQL Server)](restore-a-database-to-a-new-location-sql-server.md)  
  
 **Восстановление разностной резервной копии базы данных**  
  
-   [Восстановление разностной резервной копии базы данных (SQL Server)](restore-a-differential-database-backup-sql-server.md)  
  
 **Восстановление резервной копии с помощью управляющих объектов SQL Server (SMO)**  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  

  
## <a name="see-also"></a>См. также:  
 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)   
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [sp_addumpdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)   
 [Полные резервные копии баз данных (SQL Server)](full-database-backups-sql-server.md)   
 [Разностные резервные копии (SQL Server)](differential-backups-sql-server.md)   
 [Общие сведения о резервном копировании (SQL Server)](backup-overview-sql-server.md)   
 [Обзор процессов восстановления (SQL Server)](restore-and-recovery-overview-sql-server.md)  
  
  
