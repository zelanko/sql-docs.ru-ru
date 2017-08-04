---
title: "Отключение базы данных Stretch и возврат данных, перенесенных в удаленное расположение | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/05/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, disabling
- disabling Stretch Database
ms.assetid: c1bbb24e-47e3-46aa-b786-fcadf9fb65ce
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: dc5f97519cc9c2916f164b4905e164a273ef2d58
ms.contentlocale: ru-ru
ms.lasthandoff: 07/29/2017

---
# <a name="disable-stretch-database-and-bring-back-remote-data"></a>Отключение базы данных Stretch и возврат данных, перенесенных в удаленное расположение
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Чтобы отключить базу данных Stretch для таблицы, в среде Management Studio для SQL Server выберите для таблицы пункт **Stretch** . Затем выберите один из следующих вариантов.  
  
-   **Отключить | Вернуть данные из Azure**. Копирование удаленных данных для таблицы из Azure обратно в SQL Server с последующим отключением базы данных Stretch для таблицы. Эта операция предусматривает расходы на передачу данных и не может быть отменена.  
  
-   **Отключить | Оставить данные в Azure**. Отключение базы данных Stretch для таблицы.  Отказ от удаленных данных для таблицы в Azure.  
  
 Вы также можете использовать Transact-SQL, чтобы отключить базу данных Stretch для таблицы или базы данных.  
  
 Когда вы отключите базу данных Stretch для таблицы, перенос данных остановится, а результаты запроса больше не будут включать результаты из удаленной таблицы.  
  
 Если вы хотите просто приостановить перенос данных, см. раздел [Приостановка и возобновление переноса данных (база данных Stretch)](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
> [!NOTE]
> Отключение базы данных Stretch для таблицы или базы данных не ведет к удалению удаленного объекта. Если вы хотите удалить удаленную таблицу или базу данных, это нужно сделать с помощью портала управления Azure. Пока удаленные объекты не будут удалены, их хранение будет сопровождаться затратами в Azure. Дополнительные сведения см. на странице с [ценами на использование базы данных Stretch в SQL Server](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
## <a name="disable-stretch-database-for-a-table"></a>Отключение базы данных Stretch для таблицы  
  
### <a name="use-sql-server-management-studio-to-disable-stretch-database-for-a-table"></a>Чтобы отключить базу данных Stretch для таблицы, воспользуйтесь средой Management Studio для SQL Server.  
  
1.  В среде SQL Server Management Studio в обозревателе объектов выберите таблицу, для которой нужно отключить базу данных Stretch.  
  
2.  Щелкните правой кнопкой и выберите **Stretch**, а затем один из следующих вариантов.  
  
    -   **Отключить | Вернуть данные из Azure**. Копирование удаленных данных для таблицы из Azure обратно в SQL Server с последующим отключением базы данных Stretch для таблицы. Эту команду нельзя отменить.  
  
        > [!NOTE]
        > Копирование удаленных данных для таблицы из Azure обратно в SQL Server предусматривает расходы на передачу данных. Дополнительные сведения см. на странице [Сведения о ценах —передача данных](https://azure.microsoft.com/pricing/details/data-transfers/).  
  
         После копирования всех удаленных данных из Azure в SQL Server база данных Stretch для таблицы будет отключена.  
  
    -   **Отключить | Оставить данные в Azure**. Отключение базы данных Stretch для таблицы.  Отказ от удаленных данных для таблицы в Azure.  
  
    > [!NOTE]
    > Отключение базы данных Stretch для таблицы не ведет к удалению удаленных данных или таблицы. Если вы хотите удалить размещенную удаленно таблицу, вам нужно сделать это с помощью портала управления Azure. Пока расположенная удаленно таблица не будет удалена, ее хранение будет сопровождаться затратами в Azure. Дополнительные сведения см. на странице с [ценами на использование базы данных Stretch в SQL Server](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
### <a name="use-transact-sql-to-disable-stretch-database-for-a-table"></a>Использование Transact-SQL для отключения базы данных Stretch для таблицы  
  
-   Чтобы отключить базу данных Stretch для таблицы и скопировать удаленные данные из Azure обратно в SQL Server, запустите следующую команду. После копирования всех удаленных данных из Azure в SQL Server база данных Stretch для таблицы будет отключена.

    Эту команду нельзя отменить.  
  
    ```tsql  
    USE <Stretch-enabled database name>;
    GO
    ALTER TABLE <Stretch-enabled table name>  
       SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = INBOUND ) ) ; 
    GO 
    ```  
  
    > [!NOTE]
    > Копирование удаленных данных для таблицы из Azure обратно в SQL Server предусматривает расходы на передачу данных. Дополнительные сведения см. на странице [Сведения о ценах —передача данных](https://azure.microsoft.com/pricing/details/data-transfers/).    
  
-   Чтобы отключить растяжение для таблицы и отказаться от удаленных данных, выполните следующую команду.  
  
    ```tsql  
    USE <Stretch-enabled database name>;
    GO
    ALTER TABLE <Stretch-enabled table name>  
       SET ( REMOTE_DATA_ARCHIVE = OFF_WITHOUT_DATA_RECOVERY ( MIGRATION_STATE = PAUSED ) ) ; 
    GO
    ```  
  
> [!NOTE]
> Отключение базы данных Stretch для таблицы не ведет к удалению удаленных данных или таблицы. Если вы хотите удалить размещенную удаленно таблицу, вам нужно сделать это с помощью портала управления Azure. Пока расположенная удаленно таблица не будет удалена, ее хранение будет сопровождаться затратами в Azure. Дополнительные сведения см. на странице с [ценами на использование базы данных Stretch в SQL Server](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
## <a name="disable-stretch-database-for-a-database"></a>Отключение базы данных Stretch для базы данных  
 Прежде чем отключить базу данных Stretch для базы данных, вам потребуется отключить базу данных Stretch для всех отдельных таблиц, для которых она включена.  
  
### <a name="use-sql-server-management-studio-to-disable-stretch-database-for-a-database"></a>Отключение базы данных Stretch для базы данных с помощью Management Studio для SQL Server  
  
1.  В обозревателе объектов SQL Server Management Studio выберите базу данных, для которой нужно отключить базу данных Stretch.  
  
2.  Щелкните правой кнопкой **Задачи**, выберите **Stretch**и щелкните **Отключить**.  
  
> [!NOTE]
> Отключение базы данных Stretch для базы данных не ведет к удалению расположенной удаленно базы данных. Если вы хотите удалить расположенную удаленно базу данных, вам потребуется сделать это с помощью портала управления Azure. Пока расположенная удаленно база данных не будет удалена, ее хранение будет сопровождаться затратами в Azure. Дополнительные сведения см. на странице с [ценами на использование базы данных Stretch в SQL Server](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
### <a name="use-transact-sql-to-disable-stretch-database-for-a-database"></a>Отключение базы данных Stretch для базы данных с помощью Transact-SQL  
 Выполните следующую команду.  
  
```tsql  
ALTER DATABASE <Stretch-enabled database name>  
    SET REMOTE_DATA_ARCHIVE = OFF ;  
GO 
```  
  
> [!NOTE]
> Отключение базы данных Stretch для базы данных не ведет к удалению расположенной удаленно базы данных. Если вы хотите удалить расположенную удаленно базу данных, вам потребуется сделать это с помощью портала управления Azure. Пока расположенная удаленно база данных не будет удалена, ее хранение будет сопровождаться затратами в Azure. Дополнительные сведения см. на странице с [ценами на использование базы данных Stretch в SQL Server](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
## <a name="see-also"></a>См. также:  
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [Приостановка и возобновление переноса данных (база данных Stretch)](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)  
  
  

