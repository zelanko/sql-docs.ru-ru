---
title: Занятие 9. Восстановление базы данных из службы хранилища Azure | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ebba12c7-3d13-4c9d-8540-ad410a08356d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c1a58b7c233c3b49cf85ba34bedcd74121047564
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154974"
---
# <a name="lesson-9-restore-a-database-from-azure-storage"></a>Занятие 9. Восстановление базы данных из службы хранилища Azure
  На этом занятии вы узнаете, как восстановить файл резервной копии базы данных из хранилища Azure в базу данных, которая находится локально или на виртуальной машине в Azure. Для прохождения этого занятия не требуется завершать занятия 4, 5, 6, 7 и 8.  
  
 Для этого занятия предполагается, что вы уже выполнили следующие шаги.  
  
-   Создали базу данных на исходном компьютере.  
  
-   Вы создали резервную копию базы данных (BAK-файла) в службе хранилища Azure с помощью [SQL Server резервное копирование и восстановление с помощью функции службы хранилища больших двоичных объектов Azure](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) . Обратите внимание, что на этом шаге потребуется создать еще одни учетные данные SQL Server. Эти учетные данные используют ключи учетной записи хранения.  
  
-   У вас есть учетная запись хранения Azure.  
  
-   Вы создали контейнер в учетной записи хранения Azure.  
  
-   Создали политику в контейнере с правами на чтение, запись и перечисление. Создали ключ SAS.  
  
-   Вы создали на своем компьютере учетные данные SQL Server для функции интеграции службы хранилища Azure. Обратите внимание, что для этих учетных данных требуется ключ подписанного URL-адреса.  
  
 Для восстановления базы данных из службы хранилища Azure можно выполнить следующие действия.  
  
1.  Запустите среду SQL Server Management Studio. Подключитесь к экземпляру по умолчанию.  
  
2.  Нажмите кнопку **создать запрос** на панели инструментов Стандартная.  
  
3.  Скопируйте и вставьте следующий полный скрипт в окно запроса. При необходимости измените сценарий.  
  
     **Примечание.** Выполните `RESTORE` инструкцию, чтобы восстановить резервную копию базы данных (BAK) в службе хранилища Azure на экземпляр базы данных на другом компьютере.  
  
    ```sql  
  
    USE master   
    GO   
    -- Create a new database to be backed up.   
    CREATE DATABASE TestDbRestoreFrom;   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO   
    USE TestDbRestoreFrom;   
    GO   
    SELECT * from dbo.Table1;   
    GO   
    -- Create a credential to be used by SQL Server Backup and Restore with Azure -----Blob Storage Service.   
    USE master;   
    GO   
    CREATE CREDENTIAL BackupCredential    
    WITH IDENTITY= 'teststorageaccnt',   
    SECRET = 'BO1nH/lWRdnc8TGPlQIXmGLWVCoEa48suYSGiAlC73+S0TX5VXo5/LCm8qiyGCYafDg4ZsueDIV3GQ5RXHaRGw=='    
    GO   
    -- Display the newly created credential   
    SELECT * from sys.credentials   
    -- Create a backup in Azure Storage.   
    BACKUP DATABASE TestDBRestoreFrom    
    TO URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
          WITH CREDENTIAL = 'BackupCredential'    
         ,COMPRESSION   
         ,STATS = 5;   
    GO    
    -- Create a Shared Access Signature credential   
    CREATE CREDENTIAL [https://teststorageaccnt.blob.core.windows.net/testrestorefrom]   
    WITH IDENTITY='SHARED ACCESS SIGNATURE',   
    SECRET = 'sv=2012-02-12&sr=c&si=policy_resfrom&sig=EhVpzLUXjG4ThAMLmVhrnoiCt8IfmD3BsuYiMawGzxc%3D'   
    GO   
    USE master;   
    GO   
    RESTORE DATABASE TestDBRestoreFrom    
    FROM URL = 'https://teststorageaccnt.blob.core.windows.net/testrestorefrom/TestDBRestoreFrom.bak'    
    WITH    
    CREDENTIAL = 'BackupCredential',    
    REPLACE,   
    MOVE 'TestDBRestoreFrom' TO 'C:\Backup\TestDBRestoreFrom.mdf',     
    MOVE 'TestDBRestoreFrom_log' TO 'C:\Backup\TestDBRestoreFrom_log.ldf';   
    GO  
  
    ```  
  
 **Конец учебника: SQL Server файлы данных в службе хранилища Azure**  
  
  
