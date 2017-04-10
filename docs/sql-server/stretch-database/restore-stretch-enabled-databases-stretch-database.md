---
title: "Восстановление баз данных с поддержкой Stretch (база данных Stretch) | Microsoft Docs"
ms.custom: ""
ms.date: "07/06/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cebc1f6d-d5ea-460d-ae60-d047d29c2723
caps.latest.revision: 15
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Восстановление баз данных с поддержкой Stretch (база данных Stretch)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Восстановление резервной копии базы данных после различных типов сбоев, ошибок и аварийных ситуаций.
  
  Дополнительные сведения о создании резервной копии см. в статье [Резервное копирование баз данных с поддержкой Stretch](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md).

> [!TIP] Резервная копия — только часть комплексного решения обеспечения высокой доступности и бесперебойной работы. Дополнительные сведения о высокой доступности см. в статье [Решения высокого уровня доступности](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md).

## Восстановление данных SQL Server
После сбоя или повреждения оборудования базу данных SQL Server можно восстановить из резервной копии. Для этого можно использовать привычные методы восстановления SQL Server. Дополнительные сведения см. в статье [Обзор процессов восстановления](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).

После восстановления базы данных SQL Server необходимо выполнить хранимую процедуру **sys.sp_rda_reauthorize_db**, чтобы восстановить подключение базы данных SQL Server с поддержкой Stretch к удаленной базе данных Azure. Дополнительные сведения см. в статье [Восстановление подключения базы данных SQL Server к удаленной базе данных Azure](#reconnect).

## Восстановление удаленных данных Azure

### Восстановление активной базы данных Azure
Службы базы данных SQL Server Stretch в Azure делает моментальные снимки всех активных данных не реже, чем каждые 8 часов, используя моментальные снимки хранилища Azure. Эти снимки хранятся в течение 7 дней. Это позволяет восстановить данные до одного из как минимум 21 момента времени за прошедшие 7 дней вплоть до времени последнего моментального снимка.

Для восстановления активной базы данных Azure до наиболее раннего момента времени с помощью портала Azure необходимо выполнить указанные ниже действия.

1. Войдите на [портал Azure][].
2. В левой части экрана выберите **ОБЗОР**, а затем **База данных SQL**.
3. Найдите и выберите базу данных.
4. В верхней части колонки базы данных щелкните **Восстановить**.
5. Укажите новое **имя базы данных**, выберите **точку восстановления** и нажмите кнопку **Создать**.
6. Начнется процесс восстановления базы данных, который можно отслеживать с помощью области **УВЕДОМЛЕНИЯ**.

### Восстановление удаленной базы данных Azure
Перед удалением базы данных служба базы данных SQL Server Stretch в Azure делает ее моментальный снимок и хранит его в течение 7 дней. После этого моментальные снимки активной базы данных сохраняться не будут. Это позволяет восстановить удаленную базу данных до момента ее удаления.

Для восстановления удаленной базы данных Azure до момента ее удаления с помощью портала Azure необходимо выполнить указанные ниже действия.

1. Войдите на [портал Azure][].
2. В левой части экрана выберите **ОБЗОР**, а затем **Серверы SQL Server**.
3. Найдите и выберите сервер.
4. Прокрутите список вниз до раздела операций в колонке сервера и щелкните плитку **Удаленные базы данных**.
5. Выберите удаленную базу данных, которую нужно восстановить.
5. Укажите новое **имя базы данных** и нажмите кнопку **Создать**.
6. Начнется процесс восстановления базы данных, который можно отслеживать с помощью области **УВЕДОМЛЕНИЯ**.

## <a name="reconnect"></a>Восстановление подключения базы данных SQL Server к удаленной базе данных Azure

1.  Если вы собираетесь подключиться к восстановленной базе данных Azure под другим именем или в другом регионе, выполните хранимую процедуру [sys.sp_rda_deauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md), чтобы отключиться от предыдущей базы данных Azure.  
  
2.  Запустите хранимую процедуру [sys.sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md), чтобы заново установить подключение локальной базы данных с поддержкой Stretch к Azure.  
  
    -   Укажите учетные данные для имеющейся базы данных как значение sysname или varchar(128). (Не используйте varchar(max).) Учетные данные можно найти в представлении **sys.database_scoped_credentials**.  
  
    -   Укажите, нужно ли сделать копию удаленных данных или подключиться к копии (рекомендуется).  
  
    ```tsql  
    USE <Stretch-enabled database name>;
    GO
    EXEC sp_rda_reauthorize_db
        @credential = N'<existing_database_scoped_credential_name>',
        @with_copy = 1 ;  
    GO  
    ```  
    
  ## См. также:  
 [Резервное копирование баз данных с поддержкой Stretch](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md)  
 [Управление базой данных Stretch и устранение связанных с ней неполадок](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)   
 [sys.sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) 
 [sys.sp_rda_deauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)  
 [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
 
 [Портал Azure]: https://portal.azure.com/
 