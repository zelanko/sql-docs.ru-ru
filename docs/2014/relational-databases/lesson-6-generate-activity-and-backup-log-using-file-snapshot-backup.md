---
title: Занятие 7. Переместить файлы данных в хранилище Windows Azure | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 45004f8544efc0f0cc02292dbe28fdd75d6dc1de
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534076"
---
# <a name="lesson-7-move-your-data-files-to-windows-azure-storage"></a>Занятие 7. Перемещение файлов данных в хранилище Windows Azure
  На этом занятии вы узнаете, как переместить файлы данных (но не экземпляр SQL Server) в хранилище Windows Azure. Для прохождения этого занятия не требуется завершать занятия 4, 5 и 6.  
  
 Чтобы переместить файлы данных в хранилище Windows Azure, можно использовать инструкцию `ALTER DATABASE`, так как она позволяет изменять расположение файлов данных.  
  
 Для этого занятия предполагается, что вы уже выполнили следующие шаги.  
  
-   Получили учетную запись хранения Windows Azure.  
  
-   Создали контейнер с использованием вашей учетной записи хранения Windows Azure.  
  
-   Создали политику в контейнере с правами на чтение, запись и перечисление. Создали ключ SAS.  
  
-   Создали учетные данные SQL Server на исходном компьютере.  
  
 Затем выполните следующие шаги, чтобы переместить файлы данных в хранилище Windows Azure.  
  
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
    -- the new location of the file in Windows Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  После выполнения этой инструкции вы увидите следующее сообщение: «Файл «TestDB1Alter» изменен в системном каталоге. Новый путь будет использоваться при следующем запуске базы данных.»  
  
4.  Затем переведите базу данных в автономный режим.  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  Теперь необходимо скопировать файлы данных в хранилище Windows Azure одним из следующих методов: [Средство AzCopy](https://blogs.msdn.com/b/windowsazurestorage/archive/2012/12/03/azcopy-uploading-downloading-files-for-windows-azure-blobs.aspx), [Put Page](https://msdn.microsoft.com/library/azure/ee691975.aspx), [Справочник по клиентской библиотеке хранилища](https://msdn.microsoft.com/library/azure/dn261237.aspx), или хранилища стороннего обозревателя.  
  
     **Внимание!** При использовании этого расширения всегда проверяйте, что создается большой двоичный объект страницы, а не блока.  
  
6.  Затем переведите базу данных в оперативный режим.  
  
    ```sql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 **Следующее занятие:**  
  
 [Занятие 8. Восстановление базы данных в хранилище Microsoft Azure](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
