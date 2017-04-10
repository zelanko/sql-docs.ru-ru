---
title: "Занятие&#160;4. Восстановление базы данных в виртуальной машине с URL-адреса | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
caps.latest.revision: 23
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 23
---
# Занятие&#160;4. Восстановление базы данных в виртуальной машине с URL-адреса
На этом занятии вы восстановите базу данных AdventureWorks2014 в экземпляр SQL Server 2016 в виртуальной машине Azure.  
  
> [!NOTE]  
> В целях упрощения в этом учебнике для файлов данных и журналов применяется тот же контейнер, который использовался для резервной копии базы данных. В рабочей среде обычно используется несколько контейнеров, а также несколько файлов данных. В SQL Server 2016 можно также распределить резервную копию по нескольким BLOB-объектам, чтобы повысить производительность при резервном копировании большой базы данных.  
  
Чтобы восстановить базу данных SQL Server 2014 из хранилища BLOB-объектов Azure в экземпляр SQL Server 2016 в виртуальной машине Azure, выполните указанные ниже действия.  
  
1.  Подключитесь к среде Microsoft SQL Server Management Studio.  
  
2.  Откройте новое окно запроса и подключитесь к экземпляру SQL Server 2016 ядра СУБД в виртуальной машине Azure.  
  
3.  Скопируйте и вставьте приведенный ниже скрипт Transact-SQL в окне запроса. Измените URL-адрес в соответствии с именем учетной записи хранения и контейнером, которые были указаны на занятии 1, а затем выполните этот скрипт.  
  
    ```  
  
    -- Restore AdventureWorks2014 from URL to SQL Server instance using Azure blob storage for database files  
    RESTORE DATABASE AdventureWorks2014   
       FROM URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_onprem.bak'   
       WITH  
          MOVE 'AdventureWorks2014_data' to 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_Data.mdf'  
         ,MOVE 'AdventureWorks2014_log' to 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_Log.ldf'  
    --, REPLACE  
  
    ```  
  
4.  Откройте обозреватель объектов и подключитесь к экземпляру Azure SQL Server 2016.  
  
5.  В обозревателе объектов разверните узел "Базы данных" и убедитесь в том, что база данных AdventureWorks2014 восстановлена (при необходимости обновите узел).  
  
    ![Adventure Works 2014 database restored to SQL Server 2016 in virtual machine](../relational-databases/media/311f69a6-8443-4df5-8f30-3103c2472300.JPG "Adventure Works 2014 database restored to SQL Server 2016 in virtual machine")  
  
6.  В обозревателе объектов щелкните правой кнопкой мыши базу данных AdventureWorks2014 и выберите пункт "Свойства" (по завершении нажмите кнопку "Отмена").  
  
7.  Щелкните "Файлы" и убедитесь в том, что пути к двум файлам базы данных представляют собой URL-адреса, указывающие на BLOB-объекты в контейнере Azure.  
  
    ![database properties showing file path of logical data files as URL](../relational-databases/media/cfeee576-6319-460e-9fa2-f0922e02ee23.JPG "database properties showing file path of logical data files as URL")  
  
8.  В обозревателе объектов подключитесь к хранилищу Azure.  
  
9. Разверните узел "Контейнеры", разверните контейнер, созданный на занятии 1, и проверьте, имеются ли в нем файлы AdventureWorks2014_Data.mdf и AdventureWorks2014_Log.ldf из шага 3, а также файл резервной копии из занятия 3 (при необходимости обновите узел).  
  
    ![Adventure Works 2014 data and log file appear as blobs in Azure container](../relational-databases/media/156c7d73-44be-4754-9653-04cccb6c3066.JPG "Adventure Works 2014 data and log file appear as blobs in Azure container")  
  
**Следующее занятие:**  
  
[Занятие 5. Резервное копирование базы данных с помощью резервной копии моментального снимка](../relational-databases/lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
  
