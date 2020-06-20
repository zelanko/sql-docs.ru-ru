---
title: Занятие 8. Восстановление базы данных в службе хранилища Azure | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9f99670-e1de-441e-972c-69faffcac17a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b500c2c9a2e725577ac542b738f2ea6a536cfe34
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85024940"
---
# <a name="lesson-8-restore-a-database-to-azure-storage"></a>Занятие 8. Восстановление базы данных в службу хранилища Azure
  На этом занятии вы узнаете, как создать файл резервной копии локально, а затем восстановить его в службе хранилища Azure. Обратите внимание, что базу данных можно настроить либо локально, либо на виртуальной машине в Azure. Для прохождения этого занятия не требуется завершать занятия 4, 5, 6 и 7.  
  
 Для этого занятия предполагается, что вы уже выполнили следующие шаги.  
  
-   У вас есть учетная запись хранения Azure.  
  
-   Вы создали контейнер в учетной записи хранения Azure.  
  
-   Создали политику в контейнере с правами на чтение, запись и перечисление. Создали ключ SAS.  
  
-   Создали учетные данные SQL Server на исходном компьютере на основе подписанного URL-адреса.  
  
-   Создали базу данных на исходном компьютере.  
  
 Для восстановления базы данных в службе хранилища Azure можно выполнить следующие действия.  
  
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
  
 Чтобы восстановить базу данных с файлами данных и журналов, указывающими на службу хранилища Azure, с помощью SQL Server Management Studio пользовательского интерфейса, выполните следующие действия.  
  
1.  В **обозревателе объектов**щелкните имя сервера, чтобы развернуть дерево сервера.  
  
2.  Разверните узел **базы данных**и выберите свою базу данных.  
  
3.  Щелкните правой кнопкой мыши базу данных, укажите на пункт **Задачи**и щелкните **Восстановить**.  
  
4.  На странице **Общие** в разделе Источник **восстановления** щелкните **исходное** устройство.  
  
5.  Нажмите кнопку Обзор для текстового поля **исходное** устройство, после чего откроется диалоговое окно **Выбор устройств резервного копирования** .  
  
6.  В текстовом поле Носитель резервной копии выберите **файл**и нажмите кнопку **Добавить** , чтобы указать файл резервной копии (BAK). Нажмите кнопку **ОК**.  
  
7.  На первой странице щелкните **файлы** .  
  
8.  В разделе **Восстановление файлов базы данных** как в поле **восстановить как** введите следующее:  
  
     Для файла данных введите: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS.mdf` . В качестве файла журнала введите: `https://teststorageaccnt.blob.core.windows.net/testrestoressms/TestRESSMS_log.ldf` .  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-8.gif "SQL 14 CTP2")  
  
9. Нажмите кнопку **ОК**.  
  
 После завершения восстановления войдите на портал управления. Вы должны увидеть MDF- и LDF-файлы в контейнере следующим образом.  
  
 ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-8-9.gif "SQL 14 CTP2")  
  
 **Следующее занятие:**  
  
 [Занятие 9. Восстановление базы данных из службы хранилища Azure](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)  
  
  
