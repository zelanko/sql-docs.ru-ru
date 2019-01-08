---
title: Урок 4. Выполните восстановление из полной резервной копии | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 3af76a0ec664a10d5457dc3d106de3727740ce19
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52523660"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a>Урок 4. Выполнение восстановления базы данных из полной резервной копии
  На этом занятии рассматривается использование инструкции TSQL для выполнения восстановления из полной резервной копии базы данных, созданной на предыдущем уроке.  
  
## <a name="perform-a-restore-of-a-database-backup"></a>Выполнение восстановления резервной копии базы данных  
 Для восстановления базы данных с помощью полной резервной копии выполните следующие действия:  
  
1.  соединение с [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)];  
  
2.  в **обозревателе объектов**установите соединение с экземпляром компонента [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)];  
  
3.  на панели меню «Стандартная» выберите пункт **Создать запрос**;  
  
4.  Скопируйте и вставьте следующий пример в окно запроса (при необходимости измените).  
  
    ```  
    RESTORE DATABASE AdventureWorks2012   
    FROM URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    WITH CREDENTIAL = 'mycredential';  
    , STATS = 5 - use this to see monitor the progress  
    GO  
  
    ```  
  
5.  Проверьте инструкцию T-SQL и нажмите кнопку **Execute**  
  
### <a name="return-to-tutorials-portal"></a>Возвращение к порталу учебников  
 [Учебник. SQL Server резервного копирования и восстановления в Windows Azure BLOB-объектов службы хранилища](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md).  
  
  
