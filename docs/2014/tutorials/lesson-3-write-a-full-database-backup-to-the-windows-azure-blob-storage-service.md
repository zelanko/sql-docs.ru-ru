---
title: 'Занятие 3: Запись полной резервной копии в службу хранилища BLOB-объектов Azure Windows | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: f0de77c43dc2a18bbbb4496f6c1d1c3aab21de96
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172274"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Урок 3. Запись полной резервной копии базы данных в службе хранилища больших двоичных объектов Microsoft Azure
  На этом занятии рассматривается использование инструкции T-SQL для выполнения полного резервного копирования базы данных в службе хранилищ больших двоичных объектов Windows Azure.  
  
## <a name="perform-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Создание полной резервной копии базы данных в службе хранилища больших двоичных объектов Windows Azure  
 Для создания полной резервной копии базы данных выполните следующие действия:  
  
1.  Подключение к [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  В **обозревателя объектов**, подключитесь к экземпляру [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
3.  на панели меню «Стандартная» выберите пункт **Создать запрос**;  
  
4.  скопируйте следующий пример в окно запроса, при необходимости измените его и нажмите кнопку **Выполнить**.  
  
    ```  
    BACKUP DATABASE[AdventureWorks2012]   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/   
    WITH CREDENTIAL = 'mycredential';  
    /* name of the credential you created in the previous step */   
    GO  
  
    ```  
  
5.  В обозревателе объектов подключитесь к хранилищу Windows Azure. Найдите папку с контейнером и только что созданными файлами резервной копии.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Занятие 4: Выполните восстановление из полной резервной копии](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md).  
  
  
