---
title: Отключение Stretch Database и возвращение удаленных данных
ms.date: 08/05/2016
ms.service: sql-server-stretch-database
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database, disabling
- disabling Stretch Database
ms.assetid: c1bbb24e-47e3-46aa-b786-fcadf9fb65ce
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: 80974811f45a88b740aa8d84ea9ac67c2c2c1c07
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "73843822"
---
# <a name="disable-stretch-database-and-bring-back-remote-data"></a>Отключение Stretch Database и возвращение удаленных данных
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly.md)]


  Для отключения Stretch Database для таблицы выберите **Перенос** для таблицы в SQL Server Management Studio. Затем выберите один из следующих вариантов.  
  
-   **Отключить | Вернуть данные из Azure**. Скопируйте удаленные данные для таблицы из Azure обратно на SQL Server, затем отключите использование Stretch Database для таблицы. Эта операция предусматривает расходы на передачу данных и не может быть отменена.  
  
-   **Отключить | Оставить данные в Azure**. Отключите Stretch Database для таблицы.  Отказ от удаленных данных для таблицы в Azure.  
  
 Для отключения Stretch Database для таблицы или базы данных также можно использовать Transact-SQL.  
  
 После отключения Stretch Database для таблицы миграция данных останавливается и результаты запроса больше не включают результаты из удаленной таблицы.  
  
 Если вы хотите просто приостановить перенос данных, см. раздел [Приостановка и возобновление переноса данных (Stretch Database)](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
> [!NOTE]
> Отключение Stretch Database для таблицы или базы данных не приводит к удалению удаленного объекта. Если вы хотите удалить удаленную таблицу или базу данных, это нужно сделать с помощью портала управления Azure. Пока удаленные объекты не будут удалены, их хранение будет сопровождаться затратами в Azure. Дополнительные сведения о ценах на использование SQL Server Stretch Database см. на [этой странице](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
## <a name="disable-stretch-database-for-a-table"></a>Отключение Stretch Database для таблицы  
  
### <a name="use-sql-server-management-studio-to-disable-stretch-database-for-a-table"></a>Отключение Stretch Database для таблицы с помощью SQL Server Management Studio  
  
1.  В среде SQL Server Management Studio в обозревателе объектов выберите таблицу, для которой необходимо отключить Stretch Database.  
  
2.  Щелкните правой кнопкой и выберите **Stretch**, а затем один из следующих вариантов.  
  
    -   **Отключить | Вернуть данные из Azure**. Скопируйте удаленные данные для таблицы из Azure обратно на SQL Server, затем отключите использование Stretch Database для таблицы. Эту команду нельзя отменить.  
  
        > [!NOTE]
        > Копирование удаленных данных для таблицы из Azure обратно в SQL Server предусматривает расходы на передачу данных. Дополнительные сведения см. на странице [Сведения о ценах —передача данных](https://azure.microsoft.com/pricing/details/data-transfers/).  
  
         После копирования всех удаленных данных из Azure в SQL Server база данных Stretch для таблицы будет отключена.  
  
    -   **Отключить | Оставить данные в Azure**. Отключите Stretch Database для таблицы.  Отказ от удаленных данных для таблицы в Azure.  
  
    > [!NOTE]
    > Отключение Stretch Database для таблицы не приводит к удалению удаленных данных или удаленной таблицы. Если вы хотите удалить размещенную удаленно таблицу, вам нужно сделать это с помощью портала управления Azure. Пока расположенная удаленно таблица не будет удалена, ее хранение будет сопровождаться затратами в Azure. Дополнительные сведения о ценах на использование SQL Server Stretch Database см. на [этой странице](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
### <a name="use-transact-sql-to-disable-stretch-database-for-a-table"></a>Отключение Stretch Database для таблицы с помощью Transact-SQL  
  
-   Чтобы отключить базу данных Stretch для таблицы и скопировать удаленные данные из Azure обратно в SQL Server, запустите следующую команду. После копирования всех удаленных данных из Azure в SQL Server база данных Stretch для таблицы будет отключена.

    Эту команду нельзя отменить.  
  
    ```sql  
    USE <Stretch-enabled database name>;
    GO
    ALTER TABLE <Stretch-enabled table name>  
       SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = INBOUND ) ) ; 
    GO 
    ```  
  
    > [!NOTE]
    > Копирование удаленных данных для таблицы из Azure обратно в SQL Server предусматривает расходы на передачу данных. Дополнительные сведения см. на странице [Сведения о ценах —передача данных](https://azure.microsoft.com/pricing/details/data-transfers/).    
  
-   Чтобы отключить растяжение для таблицы и оставить удаленные данные в Azure, выполните следующую команду.  
  
    ```sql  
    USE <Stretch-enabled database name>;
    GO
    ALTER TABLE <Stretch-enabled table name>  
       SET ( REMOTE_DATA_ARCHIVE = OFF_WITHOUT_DATA_RECOVERY ( MIGRATION_STATE = PAUSED ) ) ; 
    GO
    ```  
  
> [!NOTE]
> Отключение Stretch Database для таблицы не приводит к удалению удаленных данных или удаленной таблицы. Если вы хотите удалить размещенную удаленно таблицу, вам нужно сделать это с помощью портала управления Azure. Пока расположенная удаленно таблица не будет удалена, ее хранение будет сопровождаться затратами в Azure. Дополнительные сведения о ценах на использование SQL Server Stretch Database см. на [этой странице](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
## <a name="disable-stretch-database-for-a-database"></a>Отключение Stretch Database для базы данных  
 Перед отключением службы Stretch Database для базы данных необходимо отключить ее для отдельных таблиц базы данных, для которых она было включена.  
  
### <a name="use-sql-server-management-studio-to-disable-stretch-database-for-a-database"></a>Отключение Stretch Database для базы данных с помощью SQL Server Management Studio  
  
1.  В среде SQL Server Management Studio в обозревателе объектов выберите базу данных, для которой необходимо отключить Stretch Database.  
  
2.  Щелкните правой кнопкой **Задачи**, выберите **Stretch**и щелкните **Отключить**.  
  
> [!NOTE]
> Отключение Stretch Database для базы данных не приводит к удалению удаленной базы данных. Если вы хотите удалить расположенную удаленно базу данных, вам потребуется сделать это с помощью портала управления Azure. Пока расположенная удаленно база данных не будет удалена, ее хранение будет сопровождаться затратами в Azure. Дополнительные сведения о ценах на использование SQL Server Stretch Database см. на [этой странице](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
### <a name="use-transact-sql-to-disable-stretch-database-for-a-database"></a>Отключение Stretch Database для базы данных с помощью Transact-SQL  
 Выполните следующую команду.  
  
```sql  
ALTER DATABASE <Stretch-enabled database name>  
    SET REMOTE_DATA_ARCHIVE = OFF ;  
GO 
```  
  
> [!NOTE]
> Отключение Stretch Database для базы данных не приводит к удалению удаленной базы данных. Если вы хотите удалить расположенную удаленно базу данных, вам потребуется сделать это с помощью портала управления Azure. Пока расположенная удаленно база данных не будет удалена, ее хранение будет сопровождаться затратами в Azure. Дополнительные сведения о ценах на использование SQL Server Stretch Database см. на [этой странице](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
## <a name="see-also"></a>См. также:  
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [Приостановка и возобновление переноса данных (Stretch Database)](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)  
  
  
