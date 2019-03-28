---
title: Занятие 8. Восстановление базы данных в хранилище Windows Azure | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: a9f99670-e1de-441e-972c-69faffcac17a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9e0841c3473baf73033f298cfd3c8402ffc3aa19
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58532566"
---
# <a name="lesson-8-restore-a-database-to-windows-azure-storage"></a>Занятие 8. Восстановление базы данных в хранилище Windows Azure
  На этом занятии вы узнаете, как создать файл резервной копии локально, а затем восстановить его в хранилище Windows Azure. Обратите внимание, что ваша база данных может быть размещена локально или на виртуальной машине в Windows Azure. Для прохождения этого занятия не требуется завершать занятия 4, 5, 6 и 7.  
  
 Для этого занятия предполагается, что вы уже выполнили следующие шаги.  
  
-   Получили учетную запись хранения Windows Azure.  
  
-   Создали контейнер с использованием вашей учетной записи хранения Windows Azure.  
  
-   Создали политику в контейнере с правами на чтение, запись и перечисление. Создали ключ SAS.  
  
-   Создали учетные данные SQL Server на исходном компьютере на основе подписанного URL-адреса.  
  
-   Создали базу данных на исходном компьютере.  
  
 Чтобы восстановить базу данных в хранилище Windows Azure, можно выполнить следующие действия.  
  
1.  На исходном компьютере запустите среду SQL Server Management Studio.  
  
2.  При подключении к созданной базе данных откройте окно запроса. Выполните следующую инструкцию:  
  
    ```sql  
  
    USE TestDB3Restore;   
    GO   
    BACKUP DATABASE TestDB3Restore   
    TO DISK = 'C:\BACKUP\TestDB3Restore.Bak'   
       WITH FORMAT,   
       NAME = 'Full Backup of TestDB3Restore'   
    GO  
  
    ```  
  
3.  Затем скопируйте и выполните следующие инструкции в окне запроса.  
  
    ```sql  
  
    USE master;   
    GO   
    RESTORE DATABASE TestDB3Restore    
    FROM DISK = 'C:\BACKUP\TestDB3Restore.bak'    
    WITH REPLACE,   
    MOVE 'TestDB3Restore' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore.mdf',     
    MOVE 'TestDB3Restore_log' TO 'https://teststorageaccnt.blob.core.windows.net/testcontainrestore/TestDB3Restore_log.ldf';   
    GO  
  
    ```  
  
     После завершения этого шага контейнер должен отображать файлы данных (MDF) и журналов (LDF) на портале управления.  
  
 Чтобы восстановить базу данных с файлами данных и журнала, указывающими на существующие файлы, в хранилище Windows Azure с помощью пользовательского интерфейса SQL Server Management Studio, выполните следующие действия.  
  
1.  В **обозревателя объектов**, щелкните имя сервера, чтобы развернуть дерево сервера.  
  
2.  Разверните **баз данных**и выберите свою базу данных.  
  
3.  Щелкните правой кнопкой мыши базу данных, укажите на пункт **Задачи**и щелкните **Восстановить**.  
  
4.  На **Общие** странице **восстановить** источника раздел, нажмите кнопку **источника** устройства.  
  
5.  Нажмите кнопку обзора для **источника** устройства текстовое поле, которое открывает **выберите устройства резервного копирования** диалоговое окно.  
  
6.  В текстовом поле носителя резервной копии, выберите **файл**и нажмите кнопку **добавить** кнопку, чтобы найти файл резервной копии (BAK). Нажмите кнопку **ОК**.  
  
7.  Нажмите кнопку **файлы** на первой странице.  
  
8.  В **восстановить файлы базы данных** как раздела **восстановить как** введите следующее:  
  
     Файл данных, введите: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf`. Файл журнала, введите: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf`.  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")  
  
9. Нажмите кнопку **ОК**.  
  
 После завершения восстановления войдите на портал управления. Вы должны увидеть MDF- и LDF-файлы в контейнере следующим образом.  
  
 ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")  
  
 **Следующее занятие:**  
  
 [Занятие 9. Восстановление базы данных из хранилища Microsoft Azure](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)  
  
  
