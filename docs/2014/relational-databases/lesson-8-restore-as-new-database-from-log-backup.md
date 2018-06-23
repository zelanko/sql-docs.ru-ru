---
title: Занятие 9. Восстановление базы данных из хранилища Windows Azure | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebba12c7-3d13-4c9d-8540-ad410a08356d
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b8ff5ec90f80262aae76abfb01ef6c737d13369c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195166"
---
# <a name="lesson-9-restore-a-database-from-windows-azure-storage"></a>Занятие 9. Восстановление базы данных из хранилища Windows Azure
  На этом занятии вы узнаете, как восстановить файл резервной копии базы данных из хранилища Windows Azure в базу данных, которая находится на локальном компьютере или на виртуальной машине в Windows Azure. Для прохождения этого занятия не требуется завершать занятия 4, 5, 6, 7 и 8.  
  
 Для этого занятия предполагается, что вы уже выполнили следующие шаги.  
  
-   Создали базу данных на исходном компьютере.  
  
-   Создания резервной копии базы данных (BAK-файл) в хранилище Windows Azure с помощью [SQL Server Backup and Restore with Windows Azure Blob Storage Service](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) компонентов. Обратите внимание, что на этом шаге потребуется создать еще одни учетные данные SQL Server. Эти учетные данные используют ключи учетной записи хранения.  
  
-   Получили учетную запись хранения Windows Azure.  
  
-   Создали контейнер с использованием вашей учетной записи хранения Windows Azure.  
  
-   Создали политику в контейнере с правами на чтение, запись и перечисление. Создали ключ SAS.  
  
-   Создали учетные данные SQL Server на компьютере для функции интеграции хранилища Windows Azure. Обратите внимание, что для этих учетных данных требуется ключ подписанного URL-адреса.  
  
 Чтобы восстановить базу данных из хранилища Windows Azure, можно выполнить следующие действия.  
  
1.  Запустите среду SQL Server Management Studio. Подключитесь к экземпляру по умолчанию.  
  
2.  Нажмите кнопку **новый запрос** на стандартной панели инструментов.  
  
3.  Скопируйте и вставьте следующий полный скрипт в окно запроса. При необходимости измените скрипт.  
  
     **Примечание:** запуском `RESTORE` инструкции для восстановления резервной копии базы данных (BAK) в хранилище Windows Azure в экземпляр базы данных на другом компьютере.  
  
    ```tsql  
  
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
    -- Create a credential to be used by SQL Server Backup and Restore with Windows Azure -----Blob Storage Service.   
    USE master;   
    GO   
    CREATE CREDENTIAL BackupCredential    
    WITH IDENTITY= 'teststorageaccnt',   
    SECRET = 'BO1nH/lWRdnc8TGPlQIXmGLWVCoEa48suYSGiAlC73+S0TX5VXo5/LCm8qiyGCYafDg4ZsueDIV3GQ5RXHaRGw=='    
    GO   
    -- Display the newly created credential   
    SELECT * from sys.credentials   
    -- Create a backup in Windows Azure Storage.   
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
  
 **Конец учебника: SQL Server Data Files в службе хранилища Windows Azure**  
  
  