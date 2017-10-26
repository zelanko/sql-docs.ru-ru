---
title: "Занятие 6. Создание журнала действий и резервного копирования с помощью резервного копирования моментальных снимков файлов | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8f3ea59fb612ea692b52ab46bb342d8c4031fb71
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup"></a>Занятие 6. Создание журнала действий и резервного копирования с помощью резервного копирования моментальных снимков файлов
На этом занятии вы создадите действие в базе данных AdventureWorks2014 и будете периодически создавать резервные копии журналов транзакций с помощью резервного копирования моментальных снимков файлов. Дополнительные сведения об использовании резервных копий моментальных снимков файлов см. в разделе [Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).  
  
Чтобы создать действие в базе данных AdventureWorks2014 и периодически создавать резервные копии журналов транзакций с помощью резервного копирования моментальных снимков файлов, выполните указанные ниже действия.  
  
1.  Подключитесь к среде Microsoft SQL Server Management Studio.  
  
2.  Откройте два новых окна запросов и подключите каждое из них к экземпляру SQL Server 2016 ядра СУБД в виртуальной машине Azure.  
  
3.  Скопируйте и вставьте приведенный ниже скрипт Transact-SQL в одно из окон запросов, а затем выполните его. Обратите внимание на то, что таблица Production.Location содержит 14 строк до того, как в нее будут добавлены новые строки в шаге 4.  
  
    ```  
  
    -- Verify row count at start  
    SELECT COUNT (*) from AdventureWorks2014.Production.Location;  
  
    ```  
  
4.  Скопируйте и вставьте приведенные ниже скрипты Transact-SQL в два отдельных окна запросов. Измените URL-адрес в соответствии с именем учетной записи хранения и контейнером, которые были указаны на занятии 1, а затем выполните эти скрипты одновременно в отдельных окнах запросов. На выполнение скриптов потребуется приблизительно семь минут.  
  
    ```  
    -- Insert 30,000 new rows into the Production.Location table in the AdventureWorks2014 database in batches of 75  
    DECLARE @count INT=1, @inner INT;  
    WHILE @count < 400  
       BEGIN  
          BEGIN TRAN;  
             SET @inner =1;  
                WHILE @inner <= 75  
                   BEGIN;  
                      INSERT INTO AdventureWorks2014.Production.Location    
                         (Name, CostRate, Availability, ModifiedDate)   
                            VALUES (NEWID(), .5, 5.2, GETDATE());  
                      SET @inner = @inner + 1;  
                   END;  
          COMMIT;  
       WAITFOR DELAY '00:00:01';   
       SET @count = @count + 1;  
       END;  
    SELECT COUNT (*) from AdventureWorks2014.Production.Location;  
  
    ```  
  
    ```  
    --take 7 transaction log backups with FILE_SNAPSHOT, one per minute, and include the row count and the execution time in the backup file name   
    DECLARE @count INT=1, @device NVARCHAR(120), @numrows INT;  
    WHILE @count <= 7  
       BEGIN  
             SET @numrows = (SELECT COUNT (*) FROM AdventureWorks2014.Production.Location);  
             SET @device = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/tutorial-' + CONVERT (varchar(10),@numrows) + '-' + FORMAT(GETDATE(), 'yyyyMMddHHmmss') + '.bak';  
             BACKUP LOG AdventureWorks2014 TO URL = @device WITH FILE_SNAPSHOT;  
             SELECT * from sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
          WAITFOR DELAY '00:1:00';   
             SET @count = @count + 1;  
       END;  
    ```  
  
5.  Просмотрите выходные данные первого скрипта и обратите внимание на то, что последняя строка теперь имеет номер 29 939.  
  
    ![Отображается 29 939 строк](../relational-databases/media/5e2f4229-1970-49c9-89b3-e96b6f7fde83.JPG "Отображается 29 939 строк")  
  
6.  Просмотрите выходные данные второго скрипта и обратите внимание на то, что при каждом выполнении инструкции BACKUP LOG создаются два моментальных снимка файлов: один для файла журнала, а другой для файла данных. Таким образом, для каждого файла базы данных создается всего два моментальных снимка файлов. После завершения выполнения второго скрипта должно быть создано всего 16 моментальных снимков файлов (по 8 для каждого файла базы данных): по одному при каждом выполнении инструкции BACKUP DATABASE и еще по одному при каждом выполнении инструкции BACKUP LOG.  
  
    ![Область результатов, в которой отображаются моментальные снимки файлов данных и журнала при создании резервной копии журнала](../relational-databases/media/acd213b8-895e-425c-bd72-2bf10e65a5ba.JPG "Область результатов, в которой отображаются моментальные снимки файлов данных и журнала при создании резервной копии журнала")  
  
    ![Отображаются четыре моментальных снимка файлов](../relational-databases/media/e7eff77d-85b9-4e52-abd8-e49952c8118a.JPG "Отображаются четыре моментальных снимка файлов")  
  
    ![Область результатов с 16 моментальными снимками файлов](../relational-databases/media/c3ddff17-a83c-4bf0-a670-a38834f9c922.JPG "Область результатов с 16 моментальными снимками файлов")  
  
7.  В обозревателе объектов подключитесь к хранилищу Azure.  
  
8.  Разверните узел "Контейнеры", а также контейнер, созданный на занятии 1, и убедитесь в том, что появилось 7 новых файлов резервной копии и BLOB-объекты из предыдущих занятий (при необходимости обновите узел).  
  
    ![Контейнер Azure, отображающий 7 больших двоичных объектов с резервными копиями журналов](../relational-databases/media/cfa5a326-87a2-4202-9a04-38bf577d2d0b.JPG "Контейнер Azure, отображающий 7 больших двоичных объектов с резервными копиями журналов")  
  
**Следующее занятие:**  
  
[Занятие 7. Восстановление базы данных на момент времени](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
  

