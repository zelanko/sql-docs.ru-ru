---
title: "Занятие&#160;9. Управление резервными наборами данных и резервными копиями моментальных снимков файлов | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 766a0846-db15-4346-b814-4049039bcbfc
caps.latest.revision: 10
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 10
---
# Занятие&#160;9. Управление резервными наборами данных и резервными копиями моментальных снимков файлов
На этом занятии вы удалите резервный набор данных с помощью системной хранимой процедуры [sp_delete_backup (Transact-SQL)](../Topic/sp_delete_backup%20(Transact-SQL).md). Эта процедура удаляет файл резервной копии и моментальный снимок файла для каждого файла базы данных, связанного с резервным набором данных.  
  
> [!NOTE]  
> Если вы попытаетесь удалить резервный набор данных, просто удалив файл резервной копии из контейнера BLOB-объектов Azure, то будет удален только сам файл резервной копии — связанные с ним моментальные снимки файлов останутся. Если у вас возникла такая ситуация, используйте системную функцию [sys.fn_db_backup_file_snapshots (Transact-SQL)](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md) для определения URL-адреса потерянных моментальных снимков файлов, а затем используйте системную хранимую процедуру [sp_delete_backup_file_snapshot (Transact-SQL)](../Topic/sp_delete_backup_file_snapshot%20(Transact-SQL).md) для удаления каждого утерянного моментального снимка файла. Дополнительные сведения см. в разделе [Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
Чтобы удалить резервный набор моментальных снимков файлов, выполните указанные ниже действия.  
  
1.  Подключитесь к среде Microsoft SQL Server Management Studio.  
  
2.  Откройте новое окно запроса и подключитесь к экземпляру SQL Server 2016 ядра СУБД в виртуальной машине Azure (или к любому экземпляру SQL Server 2016 с разрешениями на чтение и запись в этот контейнер).  
  
3.  Скопируйте и вставьте приведенный ниже скрипт Transact-SQL в окне запроса. Выберите резервную копию журнала, которую нужно удалить вместе со связанными моментальными снимками файлов. Измените URL-адрес в соответствии с именем учетной записи хранения и контейнером, которые были указаны на занятии 1, укажите имя файла резервной копии журнала, а затем выполните этот скрипт.  
  
    ```  
  
    sys.sp_delete_backup 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/tutorial-9164-20150726012420.bak';  
  
    ```  
  
4.  В обозревателе объектов подключитесь к хранилищу Azure.  
  
5.  Разверните узел "Контейнеры", разверните контейнер, созданный на занятии 1, и убедитесь в том, что файл резервной копии, который использовался в шаге 3, больше не отображается в этом контейнере (при необходимости обновите узел).  
  
    ![Azure container showing the deletion of the log backup blob](../relational-databases/media/c0070b08-4667-4db5-aaff-987a404ec934.JPG "Azure container showing the deletion of the log backup blob")  
  
6.  Чтобы убедиться в том, что оба моментальных снимка файлов были удалены, скопируйте и вставьте приведенный ниже скрипт Transact-SQL в окно запроса, а затем выполните его.  
  
    ```  
  
    -- verify that two file snapshots have been removed  
    SELECT * from sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
  
    ```  
  
    ![Results pane showing 2 file snapshots deleted](../relational-databases/media/f3891361-dfb6-4f4d-a090-ebfeb977981e.JPG "Results pane showing 2 file snapshots deleted")  
  
**Конец учебника**  
  
## См. также:  
[Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
[sp_delete_backup (Transact-SQL)](../Topic/sp_delete_backup%20(Transact-SQL).md)  
[sys.fn_db_backup_file_snapshots (Transact-SQL)](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)  
[sp_delete_backup_file_snapshot (Transact-SQL)](../Topic/sp_delete_backup_file_snapshot%20(Transact-SQL).md)  
  
  
  
