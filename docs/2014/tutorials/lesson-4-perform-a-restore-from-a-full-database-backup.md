---
title: 'Занятие 4: Выполните восстановление из полной резервной копии | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 9d3220d2012587a6deedad51156b49f13ed9266c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293674"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a>Занятие 4: Выполните восстановление из полной резервной копии
  На этом занятии рассматривается использование инструкции TSQL для выполнения восстановления из полной резервной копии базы данных, созданной на предыдущем уроке.  
  
## <a name="perform-a-restore-of-a-database-backup"></a>Выполнение восстановления резервной копии базы данных  
 Для восстановления базы данных с помощью полной резервной копии выполните следующие действия:  
  
1.  Подключение к [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
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
 [Учебник: SQL Server резервного копирования и восстановления в Windows Azure BLOB-объектов службы хранилища](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md).  
  
  
