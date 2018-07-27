---
title: Репликация с помощью Управляемого экземпляра Базы данных SQL | Документация Майкрософт
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Database replication
- replication, SQL Database
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8dd8931bcc3fdaaa489d0a190c5ce1f6210e5f64
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088657"
---
# <a name="replication-with-sql-database-managed-instance"></a>Репликация с помощью Управляемого экземпляра Базы данных SQL

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Управляемый экземпляр Базы данных SQL Azure поддерживает репликацию транзакций. В Управляемом экземпляре могут размещаться базы данных издателя, распространителя и подписчика.

## <a name="common-configurations"></a>Распространенные конфигурации

Как правило, издатель и распространитель должны находиться либо в облаке, либо в локальной среде. Поддерживаются следующие конфигурации:

- **Издатель и локальный распространитель в управляемом экземпляре**.

   ![Репликация_с_одним_управляемым_экземпляром_базы_данных_sql_azure_для_издателя_и_распространителя](./media/replication-with-sql-database-managed-instance/01-single-instance-asdbmi-pubdist.png)

   Базы данных издателя и распространителя настраиваются в одном управляемом экземпляре.

- **Издатель и удаленный распространитель в управляемом экземпляре**.

   ![Репликация_с_отдельными_управляемыми_экземплярами_базы_данных_sql_azure_для_издателя_и_распространителя](./media/replication-with-sql-database-managed-instance/02-separate-instances-asdbmi-pubdist.png)

   Издатель и распространитель настраиваются в двух управляемых экземплярах. В этой конфигурации:

  - Оба управляемых экземпляра находятся в одной виртуальной сети.

  - Оба управляемых экземпляра находятся в одном расположении.

- **Издатель и распространитель в локальной среде, а подписчик — в управляемом экземпляре**.

   ![Репликация_подписчика_из_локальной_среды_в_базу_данных_SQL_Azure](./media/replication-with-sql-database-managed-instance/03-azure-sql-db-subscriber.png)

   В этой конфигурации база данных SQL Azure является базой данных подписчика. Эта конфигурация поддерживает миграцию из локальной среды в Azure. Для базы данных SQL в роли подписчика не требуется управляемый экземпляр, но вы можете использовать Управляемый экземпляр базы данных SQL в качестве промежуточного этапа при миграции из локальной среды в Azure. Дополнительные сведения о подписчиках базы данных SQL Azure см. в статье [Репликация в базу данных SQL](replication-to-sql-database.md).

## <a name="requirements"></a>Требования

Для издателя и распространителя в базе данных SQL Azure требуется следующее:

- Управляемый экземпляр базы данных SQL Azure.

   >[!NOTE]
   >Базы данных SQL Azure, не настроенные в управляемом экземпляре, могут быть только подписчиками.

- Все экземпляры SQL Server должны находиться в одной виртуальной сети.

- При подключении используется проверка подлинности SQL между участниками репликации.

- Общая папка учетной записи хранения Azure в качестве рабочей папки для репликации.

## <a name="features"></a>Компоненты

Поддерживаются следующие возможности:

- Сочетание репликации транзакций и моментальных снимков для локальных экземпляров и управляемых экземпляров Базы данных SQL Azure.

- Подписчики могут находиться в локальной среде, в Базе данных SQL Azure или в эластичных пулах.

- Одно- или двунаправленная репликация.

## <a name="configure-publishing-and-distribution-example"></a>Пример настройки публикации и распространения

1. [Создайте Управляемый экземпляр Базы данных SQL Azure](http://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-create-tutorial-portal) на портале.

1. [Создайте учетную запись хранения Azure](http://docs.microsoft.com/azure/storage/common/storage-create-storage-account#create-a-storage-account) для рабочей папки. Обязательно скопируйте ключи к хранилищу данных. См. раздел [Просмотр и копирование ключей доступа к хранилищу](http://docs.microsoft.com/azure/storage/common/storage-create-storage-account#manage-your-storage-access-keys).

1. Создайте базу данных для издателя.

   В приведенных ниже примерах скриптов замените `<Publishing_DB>` именем этой базы данных.

1. Создайте пользователя базы данных с проверкой подлинности SQL для распространителя. См. раздел [Создание пользователей базы данных](http://docs.microsoft.com/azure/sql-database/sql-database-security-tutorial#creating-database-users). Используйте надежный пароль.

   В приведенных ниже примерах скриптов вместо `<SQL_USER>` и `<PASSWORD>` укажите пользователя и пароль базы данных SQL Server.

1. [Подключитесь к Управляемому экземпляру Базы данных SQL](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ssms).

1. Выполните следующий запрос для добавления распространителя и базы данных распространителя.

   ```sql
   USE [master]
   GO
   EXEC sp_adddistributor @distributor = @@ServerName;
   EXEC sp_adddistributiondb @database = N'distribution';
   ```

1. Чтобы настроить для издателя использование указанной базы данных распространителя, измените и выполните указанный ниже запрос.

   Вместо `<SQL_USER>` и `<PASSWORD>` укажите учетную запись SQL Server и пароль к ней.

   Замените `\\<STORAGE_ACCOUNT>.file.core.windows.net\<SHARE>` значением для учетной записи хранения. 

   Замените `<STORAGE_CONNECTION_STRING>` значением для ключей доступа.

   После внесения необходимых изменений выполните следующий запрос. 

   ```sql
   USE [master]
   EXEC sp_adddistpublisher @publisher = @@ServerName,
                @distribution_db = N'distribution',
                @security_mode = 0,
                @login = N'<SQL_USER>',
                @password = N'<PASSWORD>',
                @working_directory = N'\\<STORAGE_ACCOUNT>.file.core.windows.net\<SHARE>',
                @storage_connection_string = N'<STORAGE_CONNECTION_STRING>';
   GO
   ```

1. Настройте издатель для репликации. 

    В указанном ниже запросе замените `<Publishing_DB>` именем базы данных издателя.

    Замените `<Publication_Name>` именем публикации.

    Вместо `<SQL_USER>` и `<PASSWORD>` укажите учетную запись SQL Server и пароль к ней.

    После внесения необходимых изменений выполните запрос, чтобы создать публикацию.

   ```sql
   USE [<Publishing_DB>]
   EXEC sp_replicationdboption @dbname = N'<Publishing_DB>',
                @optname = N'publish',
                @value = N'true';

   EXEC sp_addpublication @publication = N'<Publication_Name>',
                @status = N'active';

   EXEC sp_changelogreader_agent @publisher_security_mode = 0,
                @publisher_login = N'<SQL_USER>',
                @publisher_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>',
                @job_password = N'<PASSWORD>';

   EXEC sp_addpublication_snapshot @publication = N'<Publication_Name>',
                @frequency_type = 1,
                @publisher_security_mode = 0,
                @publisher_login = N'<SQL_USER>',
                @publisher_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>',
                @job_password = N'<PASSWORD>'
   ```

1. Добавьте статью, подписку и агент принудительной подписки. 

   Чтобы добавить эти объекты, внесите изменения в указанный ниже скрипт.

   Замените `<Object_Name>` именем объекта публикации.

   Замените `<Object_Schema>` именем исходной схемы. 

   Замените другие параметры в угловых скобках `<>` в соответствии со значениями в предыдущих скриптах. 

   ```sql
   EXEC sp_addarticle @publication = N'<Publication_Name>',
                @type = N'logbased',
                @article = N'<Object_Name>',
                @source_object = N'<Object_Name>',
                @source_owner = N'<Object_Schema>'

   EXEC sp_addsubscription @publication = N'<Publication_Name>',
                @subscriber = @@ServerName,
                @destination_db = N'<Subscribing_DB>',
                @subscription_type = N'Push'

   EXEC sp_addpushsubscription_agent @publication = N'<Publication_Name>',
                @subscriber = @@ServerName,
                @subscriber_db = N'<Subscribing_DB>',
                @subscriber_security_mode = 0,
                @subscriber_login = N'<SQL_USER>',
                @subscriber_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>', 
                @job_password = N'<PASSWORD>'
   GO
   ```

## <a name="limitations"></a>Ограничения

Следующие возможности не поддерживаются:

- обновляемые подписки;

- активная георепликация.

## <a name="see-also"></a>См. также:

- [Общие сведения об Управляемом экземпляре Базы данных SQL Azure (предварительная версия)](http://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)