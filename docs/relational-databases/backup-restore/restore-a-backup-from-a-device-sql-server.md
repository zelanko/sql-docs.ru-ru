---
title: "Восстановление резервной копии с устройства (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "08/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "восстановление баз данных [SQL Server], восстановление с устройства"
  - "устройства резервного копирования [SQL Server], восстановление с"
  - "восстановления баз данных [SQL Server], восстановление с устройства"
  - "устройства [SQL Server]"
ms.assetid: 6e139de7-7de2-4d18-9df0-beac31ba7ff1
caps.latest.revision: 28
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 28
---
# Восстановление резервной копии с устройства (SQL Server)
  В этом разделе описано, как восстановить журнал транзакций с устройства в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  Сведения о резервном копировании SQL Server в службу хранилища BLOB-объектов Windows Azure см. в разделе [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Восстановление резервной копии с устройства с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Если восстанавливаемая база данных не существуют, для выполнения инструкции RESTORE у пользователя должны быть разрешения CREATE DATABASE. Если база данных существует, разрешения на выполнение инструкции RESTORE по умолчанию предоставлены членам предопределенных ролей сервера **sysadmin** и **dbcreator**, а также владельцу базы данных (**dbo**) (для параметра FROM DATABASE_SNAPSHOT база данных всегда существует).  
  
 Разрешения на выполнение инструкции RESTORE даются ролям, в которых данные о членстве всегда доступны серверу. Так как членство в предопределенной роли базы данных может быть проверено только тогда, когда база данных доступна и не повреждена, что не всегда имеет место при выполнении инструкции RESTORE, члены предопределенной роли базы данных **db_owner** не имеют разрешений RESTORE.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Восстановление резервной копии с устройства  
  
1.  После соединения с соответствующим экземпляром компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]в обозревателе объектов разверните дерево сервера, щелкнув его имя.  
  
2.  Раскройте узел **Базы данных**и в зависимости от типа восстанавливаемой базы данных выберите пользовательскую базу данных или раскройте узел **Системные базы данных** и выберите системную базу данных.  
  
3.  Щелкните правой кнопкой мыши базу данных, укажите на пункт **Задачи** и выберите **Восстановить**.  
  
4.  Выберите нужный тип операции восстановления (**База данных**, **Файлы и файловые группы** или **Журнал транзакций**). Откроется соответствующее диалоговое окно.  
  
5.  На странице **Общие** в разделе **Источник для восстановления** выберите **С устройства**.  
  
6.  В текстовом поле **С устройства** нажмите кнопку обзора. Откроется диалоговое окно **Указание резервной копии** .  
  
7.  В текстовом поле **Носитель резервной копии** выберите **Устройство резервного копирования**и нажмите кнопку **Добавить** . Откроется текстовое поле **Выбор устройства резервного копирования** .  
  
8.  В текстовом поле **Устройство резервного копирования** выберите устройство для операции восстановления.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Восстановление резервной копии с устройства  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  В инструкции [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) укажите логическое или физическое устройство резервного копирования, которое будет использоваться для создания резервной копии. В этом примере показано восстановление из файла на диске, имеющего физическое имя `Z:\SQLServerBackups\AdventureWorks2012.bak`.  
  
```tsql  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' ;  
  
```  
  
## См. также:  
 [RESTORE FILELISTONLY (Transact-SQL)](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)   
 [RESTORE HEADERONLY (Transact-SQL)](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md)   
 [RESTORE LABELONLY (Transact-SQL)](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md)   
 [RESTORE VERIFYONLY (Transact-SQL)](../Topic/RESTORE%20VERIFYONLY%20\(Transact-SQL\).md)   
 [Восстановление резервной копии базы данных в простой модели восстановления (Transact-SQL)](../../relational-databases/backup-restore/restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)   
 [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)   
 [Восстановление разностной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/restore-a-differential-database-backup-sql-server.md)   
 [Восстановление базы данных в новом расположении (SQL Server)](../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [Резервное копирование файлов и файловых групп (SQL Server)](../../relational-databases/backup-restore/back-up-files-and-filegroups-sql-server.md)   
 [Создание резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)   
 [Создание разностной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
  