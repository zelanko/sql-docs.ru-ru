---
title: "Восстановление баз данных с поддержкой Stretch (Stretch Database) | Документация Майкрософт"
ms.custom: 
ms.date: 07/06/2016
ms.prod: stretch-database
ms.prod_service: sql-non-specified
ms.service: database-engine
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cebc1f6d-d5ea-460d-ae60-d047d29c2723
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b6f86b3d181ee105d3b7aaab7967ac9bada448b5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="restore-stretch-enabled-databases-stretch-database"></a>Восстановление баз данных с поддержкой Stretch (Stretch Database)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Восстановление резервной копии базы данных после различных типов сбоев, ошибок и аварийных ситуаций.
  
  Дополнительные сведения о создании резервной копии см. в статье [Резервное копирование баз данных с поддержкой Stretch](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md).

> [!TIP]
> Резервная копия — только часть комплексного решения обеспечения высокой доступности и бесперебойной работы. Дополнительные сведения о высокой доступности см. в статье [Решения высокого уровня доступности](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md).

## <a name="restore-your-sql-server-data"></a>Восстановление данных SQL Server
После сбоя или повреждения оборудования базу данных SQL Server можно восстановить из резервной копии. Для этого можно использовать привычные методы восстановления SQL Server. Дополнительные сведения см. в статье [Обзор процессов восстановления](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).

После восстановления базы данных SQL Server необходимо выполнить хранимую процедуру **sys.sp_rda_reauthorize_db** , чтобы восстановить подключение базы данных SQL Server с поддержкой Stretch к удаленной базе данных Azure. Дополнительные сведения см. в статье [Восстановление подключения базы данных SQL Server к удаленной базе данных Azure](#reconnect).

## <a name="restore-your-remote-azure-data"></a>Восстановление удаленных данных Azure

### <a name="recover-a-live-azure-database"></a>Восстановление активной базы данных Azure
Служба SQL Server Stretch Database в Azure делает моментальные снимки всех активных данных не реже, чем каждые 8 часов, используя моментальные снимки хранилища Azure. Эти снимки хранятся в течение 7 дней. Это позволяет восстановить данные до одного из как минимум 21 момента времени за прошедшие 7 дней вплоть до времени последнего моментального снимка.

Для восстановления активной базы данных Azure до наиболее раннего момента времени с помощью портала Azure необходимо выполнить указанные ниже действия.

1. Войдите на [портал Azure][].
2. В левой части экрана выберите **ОБЗОР** , а затем **База данных SQL**.
3. Найдите и выберите базу данных.
4. В верхней части колонки базы данных щелкните **Восстановить**.
5. Укажите новое **имя базы данных**, выберите **точку восстановления** и нажмите кнопку **Создать**.
6. Начнется процесс восстановления базы данных, который можно отслеживать с помощью области **УВЕДОМЛЕНИЯ**.

### <a name="recover-a-deleted-azure-database"></a>Восстановление удаленной базы данных Azure
Перед удалением базы данных служба SQL Server Stretch Database в Azure делает ее моментальный снимок и хранит его в течение 7 дней. После этого моментальные снимки активной базы данных сохраняться не будут. Это позволяет восстановить удаленную базу данных до момента ее удаления.

Для восстановления удаленной базы данных Azure до момента ее удаления с помощью портала Azure необходимо выполнить указанные ниже действия.

1. Войдите на [портал Azure][].
2. В левой части экрана выберите **ОБЗОР** , а затем **Серверы SQL Server**.
3. Найдите и выберите сервер.
4. Прокрутите список вниз до раздела операций в колонке сервера и щелкните плитку **Удаленные базы данных** .
5. Выберите удаленную базу данных, которую нужно восстановить.
5. Укажите новое **имя базы данных** и нажмите кнопку **Создать**.
6. Начнется процесс восстановления базы данных, который можно отслеживать с помощью области **УВЕДОМЛЕНИЯ**.

## <a name="reconnect"></a>Восстановление подключения базы данных SQL Server к удаленной базе данных Azure

1.  Если вы собираетесь подключиться к восстановленной базе данных Azure под другим именем или в другом регионе, выполните хранимую процедуру [sys.sp_rda_deauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md) , чтобы отключиться от предыдущей базы данных Azure.  
  
2.  Запустите хранимую процедуру [sys.sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) , чтобы заново установить подключение локальной базы данных с поддержкой Stretch к Azure.  
  
    -   Укажите учетные данные для имеющейся базы данных как значение sysname или varchar(128). (Не используйте varchar(max).) Учетные данные можно найти в представлении **sys.database_scoped_credentials**.  
  
    -   Укажите, нужно ли сделать копию удаленных данных или подключиться к копии (рекомендуется).  
  
    ```sql  
    USE <Stretch-enabled database name>;
    GO
    EXEC sp_rda_reauthorize_db
        @credential = N'<existing_database_scoped_credential_name>',
        @with_copy = 1 ;  
    GO  
    ```  
    
  ## <a name="see-also"></a>См. также:  
 [Резервное копирование баз данных с поддержкой Stretch](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md)  
 [Управление Stretch Database и устранение связанных с ней неполадок](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)   
 [sys.sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) 
 [sys.sp_rda_deauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)  
 [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
 
 [портал Azure]: https://portal.azure.com/
 
