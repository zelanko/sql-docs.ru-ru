---
title: Занятие 7. Перемещение файлов данных в службу хранилища Azure | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5ae5b92ace65f255aacff5b49fe789a31d3a69e0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049809"
---
# <a name="lesson-7-move-your-data-files-to-azure-storage"></a>Занятие 7: Перенос файлов данных в службу хранилища Azure
  На этом занятии вы узнаете, как перемещать файлы данных в службу хранилища Azure (но не на экземпляр SQL Server). Для прохождения этого занятия не требуется завершать занятия 4, 5 и 6.  
  
 Чтобы переместить файлы данных в службу хранилища Azure, можно использовать `ALTER DATABASE` инструкцию, так как она помогает изменить расположение файлов данных.  
  
 Для этого занятия предполагается, что вы уже выполнили следующие шаги.  
  
-   У вас есть учетная запись хранения Azure.  
  
-   Вы создали контейнер в учетной записи хранения Azure.  
  
-   Создали политику в контейнере с правами на чтение, запись и перечисление. Создали ключ SAS.  
  
-   Создали учетные данные SQL Server на исходном компьютере.  
  
 Затем выполните следующие действия, чтобы переместить файлы данных в службу хранилища Azure.  
  
1.  Сначала создайте тестовую базу данных на исходном компьютере и добавьте в нее данные.  
  
    ```sql  
  
    USE master;   
    CREATE DATABASE TestDB1Alter;   
    GO   
    USE TestDB1Alter;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
2.  Выполните следующий код:  
  
    ```sql  
  
    -- In the following statement, modify the path specified in FILENAME to   
    -- the new location of the file in Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  При выполнении этой задачи вы увидите следующее сообщение: "файл" TestDB1Alter "был изменен в системном каталоге. Новый путь будет использоваться при следующем запуске базы данных ".  
  
4.  Затем переведите базу данных в автономный режим.  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  Теперь необходимо скопировать файлы данных в службу хранилища Azure с помощью одного из следующих методов: [средство AzCopy](https://docs.microsoft.com/archive/blogs/windowsazurestorage/azcopy-uploadingdownloading-files-for-windows-azure-blobs), [размещение страницы](https://msdn.microsoft.com/library/azure/ee691975.aspx), [Справочник по клиентской библиотеке хранилища](https://msdn.microsoft.com/library/azure/dn261237.aspx)или средство обозревателя хранилищ сторонних производителей.  
  
     **Внимание!** При использовании этого расширения всегда проверяйте, что создается большой двоичный объект страницы, а не блока.  
  
6.  Затем переведите базу данных в оперативный режим.  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 **Следующее занятие:**  
  
 [Занятие 8. Восстановление базы данных в службе хранилища Azure](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
