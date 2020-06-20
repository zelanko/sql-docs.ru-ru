---
title: Занятие 3. запись полной резервной копии базы данных в службу хранилища BLOB-объектов Azure | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 627c21a9c2220bcaea76f771624f79618dcf56fb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054295"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-azure-blob-storage-service"></a>Урок 3. Запись полной резервной копии базы данных в службу хранилища BLOB-объектов Azure
  На этом занятии показано использование инструкции TSQL для выполнения полной резервной копии базы данных в службе хранилища BLOB-объектов Azure.  
  
## <a name="perform-a-full-database-backup-to-the-azure-blob-storage-service"></a>Выполнение полной резервной копии базы данных в службе хранилища BLOB-объектов Azure  
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
 [Занятие 4. Восстановление из полной резервной копии базы данных](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md).  
  
  
