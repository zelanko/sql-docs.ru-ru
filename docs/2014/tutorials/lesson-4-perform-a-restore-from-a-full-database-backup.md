---
title: 'Занятие 4: Восстановление из полной резервной копии базы данных | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: de9a356589ac6bceb532ed4cecf509f957e3c337
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153404"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a>Занятие 4: Восстановление базы данных из полной резервной копии
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
  
5.  Проверьте инструкцию T-SQL и нажмите кнопку " **выполнить** ".  
  
### <a name="return-to-tutorials-portal"></a>Возвращение к порталу учебников  
 [Учебник. SQL Server резервное копирование и восстановление в службе](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)хранилища BLOB-объектов Azure.  
  
  
