---
title: 'Занятие 7: Перемещение файлов данных в хранилище Windows Azure | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 44bc025ce3eb536e10f4c77410ea487e59f006ee
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37162715"
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
  
    ```tsql  
  
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
  
    ```tsql  
  
    -- In the following statement, modify the path specified in FILENAME to   
    -- the new location of the file in Windows Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  После выполнения этой инструкции вы увидите следующее сообщение: «Файл «TestDB1Alter» изменен в системном каталоге. При следующем запуске этой базы данных будет использоваться новый путь».  
  
4.  Затем переведите базу данных в автономный режим.  
  
    ```tsql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  Теперь необходимо скопировать файлы данных в хранилище Windows Azure одним из следующих методов: [инструмента AzCopy](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/12/03/azcopy-uploading-downloading-files-for-windows-azure-blobs.aspx), [вставки страницы](https://msdn.microsoft.com/library/azure/ee691975.aspx), [справочника по клиентской библиотеке хранилища](https://msdn.microsoft.com/library/azure/dn261237.aspx)или обозревателя хранилищ сторонних производителей.  
  
     **Внимание!** При использовании этого расширения всегда проверяйте, что создается большой двоичный объект страницы, а не блока.  
  
6.  Затем переведите базу данных в оперативный режим.  
  
    ```tsql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 **Следующее занятие:**  
  
 [Занятие 8. Восстановление базы данных в хранилище Microsoft Azure](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  
