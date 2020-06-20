---
title: Восстановление базы данных до точки сбоя в модели полного восстановления (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- point of failure [SQL Server]
- restoring databases [SQL Server], point of failure
- database restores [SQL Server], point of failure
ms.assetid: 04106e18-bbf7-4a5e-a2e1-3d65319814d5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95b73660ebb44f4daffe6eaefd873699cfbbd8ca
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84956772"
---
# <a name="restore-a-database-to-the-point-of-failure-under-the-full-recovery-model-transact-sql"></a>Восстановление базы данных до точки сбоя в модели полного восстановления (Transact-SQL)
  В этом подразделе описывается восстановление до точки сбоя. Сведения в этом разделе относятся только к тем базам данных, которые используют модель полного восстановления или модель восстановления с неполным протоколированием.  
  
### <a name="to-restore-to-the-point-of-failure"></a>Восстановление до точки сбоя  
  
1.  Создайте резервную копию заключительного фрагмента журнала базы данных, взяв за основу следующую инструкцию [BACKUP](/sql/t-sql/statements/backup-transact-sql) :  
  
    ```  
    BACKUP LOG <database_name> TO <backup_device>   
       WITH NORECOVERY, NO_TRUNCATE;  
    ```  
  
2.  Восстановите базу данных из ее полной резервной копии, взяв за основу следующую инструкцию [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) :  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
3.  Можно также восстановить базу данных из ее разностной резервной копии, взяв за основу следующую инструкцию RESTORE DATABASE:  
  
    ```  
    RESTORE DATABASE <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
4.  Примените все журналы транзакций, включая резервную копию заключительного фрагмента журнала (созданную на первом шаге), указав предложение WITH NORECOVERY в инструкции RESTORE LOG:  
  
    ```  
    RESTORE LOG <database_name> FROM <backup_device>   
       WITH NORECOVERY;  
    ```  
  
5.  Восстановите базу данных, выполнив следующую инструкцию RESTORE DATABASE:  
  
    ```  
    RESTORE DATABASE <database_name>   
       WITH RECOVERY;  
    ```  
  
## <a name="example"></a>Пример  
 Перед запуском этого примера необходимо завершить следующие подготовительные действия.  
  
1.  По умолчанию, база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] имеет простую модель восстановления. Поскольку в этой модели не поддерживается восстановление до момента сбоя, настройте [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на использование модели полного восстановления, выполнив следующую инструкцию [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) :  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
    ```  
  
2.  Создайте полную резервную копию базы данных при помощи следующей инструкции BACKUP:  
  
    ```  
    BACKUP DATABASE AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Data.bck';  
    ```  
  
3.  Создайте резервную копию журналов:  
  
    ```  
    BACKUP LOG AdventureWorks2012 TO DISK = 'C:\AdventureWorks2012_Log.bck';  
    ```  
  
 В следующем примере после создания резервной копии заключительного фрагмента журнала базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] производится восстановление ранее созданной резервной копии (на этом шаге предполагается, что имеется доступ к диску, на котором хранятся журналы).  
  
 Вначале создается резервная копия заключительного фрагмента журнала базы данных, которая захватывает активный журнал и оставляет базу данных в состоянии восстановления. После этого в данном примере производится восстановление резервной копии базы данных, применяется раннее созданная процедура резервного копирования журналов и создается резервная копия заключительного фрагмента журнала. Наконец, отдельным шагом производится восстановление базы данных.  
  
> [!NOTE]  
>  По умолчанию, при обработке инструкции, выполняющей окончательное восстановление резервной копии, производится восстановление базы данных.  
  
```  
/* Example of restoring a to the point of failure */  
-- Step 1: Create a tail-log backup by using WITH NORECOVERY.  
BACKUP LOG AdventureWorks2012  
   TO DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 2: Restore the full database backup.  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Data.bck'  
   WITH NORECOVERY;  
GO  
-- Step 3: Restore the first transaction log backup.  
RESTORE LOG AdventureWorks2012  
   FROM DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 4: Restore the tail-log backup.  
RESTORE LOG AdventureWorks2012  
   FROM  DISK = 'C:\AdventureWorks2012_Log.bck'  
   WITH NORECOVERY;  
GO  
-- Step 5: Recover the database.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
