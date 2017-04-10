---
title: "Занятие&#160;5. Резервное копирование базы данных с помощью резервной копии моментального снимка | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: d9134ade-7b03-4c5c-8ed3-3bc369a61691
caps.latest.revision: 19
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 19
---
# Занятие&#160;5. Резервное копирование базы данных с помощью резервной копии моментального снимка
На этом занятии будет выполнено резервное копирование базы данных AdventureWorks2014 в виртуальной машине Azure с помощью резервной копии снимка файла. Такой способ позволяет выполнять почти мгновенное резервное копирование с использованием моментальных снимков Azure. Дополнительные сведения о резервных копиях моментальных снимков файлов см. в разделе [Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
Чтобы создать резервную копию базы данных AdventureWorks2014 с помощью резервного копирования моментальных снимков файлов, выполните указанные ниже действия.  
  
1.  Подключитесь к среде Microsoft SQL Server Management Studio.  
  
2.  Откройте новое окно запроса и подключитесь к экземпляру SQL Server 2016 ядра СУБД в виртуальной машине Azure.  
  
3.  Скопируйте и вставьте приведенный ниже скрипт Transact-SQL в окно запроса, а затем выполните его (не закрывайте окно запроса — этот скрипт необходимо будет выполнить еще раз в шаге 5). Эта системная хранимая процедура позволяет просмотреть существующие резервные копии моментальных снимков файлов для каждого файла, входящего в состав указанной базы данных. Обратите внимание на то, что для данной базы данных резервных копий моментальных снимков файлов нет.  
  
    ```  
  
    -- Verify that no file snapshot backups exist  
    SELECT * FROM sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
  
    ```  
  
4.  Скопируйте и вставьте приведенный ниже скрипт Transact-SQL в окне запроса. Измените URL-адрес в соответствии с именем учетной записи хранения и контейнером, которые были указаны на занятии 1, а затем выполните этот скрипт. Обратите внимание на то, как быстро выполняется это резервное копирование.  
  
    ```  
  
    -- Backup the AdventureWorks2014 database with FILE_SNAPSHOT  
    BACKUP DATABASE AdventureWorks2014   
       TO URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_Azure.bak'   
       WITH FILE_SNAPSHOT;  
  
    ```  
  
    ![results pane showing file snapshots of each database file](../relational-databases/media/2a9320e0-067a-485a-8e0e-636660005e5c.JPG "results pane showing file snapshots of each database file")  
  
5.  Проверив успешность выполнения скрипта в шаге 4, выполните приведенный ниже скрипт еще раз. Обратите внимание на то, что в результате операции резервного копирования моментальных снимков файлов в шаге 4 были созданы моментальные снимки как файлов данных, так и файлов журналов.  
  
    ```  
  
    -- Verify that two file-snapshot backups exist  
    SELECT * FROM sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
  
    ```  
  
    ![results of the sys.fn_db_backup_file_snapshots function showing 2 snapshots](../relational-databases/media/fca1436e-9607-4432-97ee-f66ac2f2108d.JPG "results of the sys.fn_db_backup_file_snapshots function showing 2 snapshots")  
  
6.  В обозревателе объектов экземпляра SQL Server 2016 в виртуальной машине Azure разверните узел "Базы данных" и убедитесь в том, что база данных AdventureWorks2014 восстановлена в этом экземпляре (при необходимости обновите узел).  
  
7.  В обозревателе объектов подключитесь к хранилищу Azure.  
  
8.  Разверните узел "Контейнеры", разверните контейнер, созданный на занятии 1, и проверьте, имеется ли в нем файл AdventureWorks2014_Azure.bak из шага 4, а также файл резервной копии из занятия 3 и файлы базы данных из занятия 4 (при необходимости обновите узел).  
  
    ![File snapshot backup appears in the Azure container](../relational-databases/media/181bc970-4af7-4272-a9ae-4bef674f2e02.JPG "File snapshot backup appears in the Azure container")  
  
**Следующее занятие:**  
  
[Занятие 6. Создание журнала действий и резервного копирования с помощью резервного копирования моментальных снимков файлов](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)  
  
## См. также:  
[Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
[sys.fn_db_backup_file_snapshots (Transact-SQL)](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)  
  
  
  
