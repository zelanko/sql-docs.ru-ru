---
title: Восстановление резервной копии с устройства (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], device restores
- backup devices [SQL Server], restoring from
- database restores [SQL Server], device restores
- devices [SQL Server]
ms.assetid: 6e139de7-7de2-4d18-9df0-beac31ba7ff1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f5e272dde5ca7a3c0ff7246d42131f1e70331689
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62921979"
---
# <a name="restore-a-backup-from-a-device-sql-server"></a>Восстановление резервной копии с устройства (SQL Server)
  В этом разделе описано, как восстановить журнал транзакций с устройства в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  Дополнительные сведения о резервном копировании SQL Server в службу хранилища больших двоичных объектов Windows Azure см. в разделе [Резервное копирование и восстановление SQL Server с помощью службы хранилищ больших двоичных объектов Windows Azure](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Восстановление резервной копии с устройства с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Если восстанавливаемая база данных не существуют, для выполнения инструкции RESTORE у пользователя должны быть разрешения CREATE DATABASE. Если база данных существует, разрешения на выполнение инструкции RESTORE по умолчанию предоставлены членам предопределенных ролей сервера **sysadmin** и **dbcreator** , а также владельцу базы данных (**dbo**) (для параметра FROM DATABASE_SNAPSHOT база данных всегда существует).  
  
 Разрешения на выполнение инструкции RESTORE даются ролям, в которых данные о членстве всегда доступны серверу. Так как членство в предопределенной роли базы данных может быть проверено только тогда, когда база данных доступна и не повреждена, что не всегда имеет место при выполнении инструкции RESTORE, члены предопределенной роли базы данных **db_owner** не имеют разрешений RESTORE.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-restore-a-backup-from-a-device"></a>Восстановление резервной копии с устройства  
  
1.  После соединения с соответствующим экземпляром компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]в обозревателе объектов разверните дерево сервера, щелкнув его имя.  
  
2.  Раскройте узел **Базы данных**и в зависимости от типа восстанавливаемой базы данных выберите пользовательскую базу данных или раскройте узел **Системные базы данных** и выберите системную базу данных.  
  
3.  Щелкните правой кнопкой мыши базу данных, укажите на пункт **Задачи**и выберите **Восстановить**.  
  
4.  Выберите нужный тип операции восстановления (**База данных**, **Файлы и файловые группы**или **Журнал транзакций**). Откроется соответствующее диалоговое окно.  
  
5.  На странице **Общие** в разделе **Источник для восстановления** выберите **С устройства**.  
  
6.  В текстовом поле **С устройства** нажмите кнопку обзора. Откроется диалоговое окно **Указание резервной копии** .  
  
7.  В текстовом поле **Носитель резервной копии** выберите **Устройство резервного копирования**и нажмите кнопку **Добавить** . Откроется текстовое поле **Выбор устройства резервного копирования** .  
  
8.  В текстовом поле **Устройство резервного копирования** выберите устройство для операции восстановления.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-restore-a-backup-from-a-device"></a>Восстановление резервной копии с устройства  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  В инструкции [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) укажите логическое или физическое устройство резервного копирования, которое будет использоваться для создания резервной копии. В этом примере показано восстановление из файла на диске, имеющего физическое имя `Z:\SQLServerBackups\AdventureWorks2012.bak`.  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' ;  
  
```  
  
## <a name="see-also"></a>См. также  
 [RESTORE FILELISTONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)   
 [RESTORE HEADERONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)   
 [RESTORE LABELONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)   
 [RESTORE VERIFYONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)   
 [Восстановление резервной копии базы данных в простой модели восстановления (Transact-SQL)](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)   
 [Восстановление резервной копии базы данных &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)   
 [Восстановление разностной резервной копии базы данных (SQL Server)](restore-a-differential-database-backup-sql-server.md)   
 [Восстановление базы данных в новом расположении (SQL Server)](restore-a-database-to-a-new-location-sql-server.md)   
 [Резервное копирование файлов и файловых групп (SQL Server)](back-up-files-and-filegroups-sql-server.md)   
 [Создание резервной копии журнала транзакций (SQL Server)](back-up-a-transaction-log-sql-server.md)   
 [Создание разностной резервной копии базы данных (SQL Server)](create-a-differential-database-backup-sql-server.md)  
  
  
