---
title: Урок 3. Запись полной резервной копии в Windows Azure Blob Storage Service | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 242e32b08ec6346c39e149628e773b33554c95d4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62653691"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Урок 3. Запись полной резервной копии в Windows Azure Blob Storage Service
  На этом занятии рассматривается использование инструкции T-SQL для выполнения полного резервного копирования базы данных в службе хранилищ больших двоичных объектов Windows Azure.  
  
## <a name="perform-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Создание полной резервной копии базы данных в службе хранилища больших двоичных объектов Windows Azure  
 Для создания полной резервной копии базы данных выполните следующие действия:  
  
1.  соединение с [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)];  
  
2.  в **обозревателе объектов**установите соединение с экземпляром компонента [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)];  
  
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
 [Занятие 4. Выполните восстановление из полной резервной копии](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md).  
  
  
