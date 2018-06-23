---
title: 'Урок 4: Выполните восстановление из полной резервной копии | Документы Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8869fa4bba6050dd0c15b8b59b7f2d091902936f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087529"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a>Урок 4: Выполните восстановление из полной резервной копии
  На этом занятии рассматривается использование инструкции TSQL для выполнения восстановления из полной резервной копии базы данных, созданной на предыдущем уроке.  
  
## <a name="perform-a-restore-of-a-database-backup"></a>Выполнение восстановления резервной копии базы данных  
 Для восстановления базы данных с помощью полной резервной копии выполните следующие действия:  
  
1.  Подключиться к [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  В **обозревателя объектов**, подключитесь к экземпляру [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
3.  на панели меню «Стандартная» выберите пункт **Создать запрос**;  
  
4.  Скопируйте и вставьте следующий пример в окно запроса (при необходимости измените).  
  
    ```  
    RESTORE DATABASE AdventureWorks2012   
    FROM URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    WITH CREDENTIAL = 'mycredential';  
    , STATS = 5 – use this to see monitor the progress  
    GO  
  
    ```  
  
5.  Проверьте инструкцию T-SQL и нажмите кнопку **Execute**  
  
### <a name="return-to-tutorials-portal"></a>Возвращение к порталу учебников  
 [Учебник: SQL Server резервного копирования и восстановления в Windows Azure BLOB-объект службы хранилища](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md).  
  
  