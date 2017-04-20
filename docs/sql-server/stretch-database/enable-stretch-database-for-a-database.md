---
title: "Настройка базы данных Stretch для базы данных | Документация Майкрософт"
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
- Stretch Database, enabling database
- enabling database for Stretch Database
ms.assetid: 37854256-8c99-4566-a552-432e3ea7c6da
caps.latest.revision: 70
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 15d9caa3c474d5cbe2e16e158e6f2fcfe7959ed6
ms.lasthandoff: 04/11/2017

---
# <a name="enable-stretch-database-for-a-database"></a>Настройка базы данных Stretch для базы данных
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Чтобы настроить существующую базу данных для базы данных Stretch, в SQL Server Management Studio выберите для базы данных команду **Задачи | Растяжение | Включить**, чтобы открыть мастер **разрешения операции растяжения для базы данных**. Кроме того, вы можете использовать Transact-SQL, чтобы включить базу данных Stretch для базы данных.  
  
 Если выбрать для таблицы команду **Задачи |Растяжение | Включить** , предварительно не включив базу данных для базы данных Stretch, мастер сначала настроит базу данных для базы данных Stretch и позволит вам выбрать таблицы в рамках этого процесса. Выполните шаги из этой статьи вместо статьи [Enable Stretch Database for a table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).  
  
 Чтобы настроить базу данных Stretch для таблицы или базы данных, требуются права db_owner. Кроме того, чтобы настроить базу данных Stretch для базы данных, требуются права CONTROL DATABASE.  

 >   [!NOTE]
 > Если позднее вы решите отключить Базу данных Stretch, помните, что ее отключение для таблицы или базы данных не ведет к удалению удаленного объекта. Если вы хотите удалить удаленную таблицу или базу данных, это нужно сделать с помощью портала управления Azure. Пока удаленные объекты не будут удалены вручную, их хранение будет сопровождаться затратами в Azure. 
 
## <a name="before-you-get-started"></a>Перед началом работы  
  
-   Перед настройкой базы данных для Stretch рекомендуется запустить помощник по настройке базы данных Stretch, чтобы определить базы данных и таблицы, подходящие для Stretch. Помощник по настройке базы данных Stretch, кроме того, обнаруживает блокирующие проблемы. Дополнительные сведения см. в разделе [Определение баз данных и таблиц для базы данных Stretch с использованием помощника базы данных Stretch](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md).  
  
-   Изучите раздел [Ограничения для базы данных Stretch](../../sql-server/stretch-database/limitations-for-stretch-database.md).  
  
-   База данных Stretch перемещает данные в Azure. Таким образом, необходимо иметь учетную запись Azure и подписку для выставления счетов. Для получения учетной записи Azure [нажмите здесь](http://azure.microsoft.com/en-us/pricing/free-trial/).  
  
-   Убедитесь в наличии информации о подключении и данных входа, необходимых для создания нового сервера Azure или выбора существующего сервера Azure.  
  
##  <a name="EnableTSQLServer"></a> Обязательное требование: включение базы данных Stretch на сервере  
 Перед включением базы данных Stretch в базе данных или таблице необходимо включить ее на локальном сервере. Для этой операции требуются права sysadmin или serveradmin.  
  
-   При наличии нужных административных разрешений мастер **включения базы данных для Stretch** настроит сервер для Stretch.  
  
-   Если у вас нет необходимых разрешений, администратор должен вручную включить этот параметр, выполнив команду **sp_configure** перед запуском мастера, либо администратор должен запустить этот мастер.  
  
 Чтобы включить базу данных Stretch на сервере вручную, выполните команду **sp_configure** и включите параметр **remote data archive** . В следующем примере включается параметр **remote data archive** путем изменения его значения на 1.  
  
```  
EXEC sp_configure 'remote data archive' , '1';  
GO

RECONFIGURE;  
GO  
```  
  
 Дополнительные сведения см. в разделе [Настройка параметра конфигурации сервера для удаленного архива данных](../../database-engine/configure-windows/configure-the-remote-data-archive-server-configuration-option.md) и [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
##  <a name="Wizard"></a> Настройка базы данных Stretch в базе данных с помощью мастера  
 Сведения о мастере включения базы данных для Stretch, включая описание информации, которую необходимо указать, и вариантов, из которых необходимо выбрать, см. в разделе [Запуск мастера включения базы данных для Stretch](../../sql-server/stretch-database/get-started-by-running-the-enable-database-for-stretch-wizard.md).  
  
##  <a name="EnableTSQLDatabase"></a> Настройка базы данных Stretch в базы данных с помощью Transact-SQL  
 Перед включением базы данных Stretch в отдельных таблицах необходимо включить ее в базе данных.  
  
 Чтобы настроить базу данных Stretch для таблицы или базы данных, требуются права db_owner. Кроме того, чтобы настроить базу данных Stretch для базы данных, требуются права CONTROL DATABASE.  
  
1.  Прежде чем начать, выберите существующий сервер Azure для данных, миграцию которых выполняет база данных Stretch, или создайте новый сервер Azure.  
  
2.  На сервере Azure создайте правило брандмауэра с диапазоном IP-адресов SQL Server, позволяющим SQL Server обмениваться данными с удаленным сервером.  

    Вы можете легко найти нужные значения и создать правило брандмауэра, попытавшись подключиться к серверу Azure из обозревателя объектов в среде SQL Server Management Studio (SSMS). Среда SSMS поможет вам создать правило, открыв приведенное ниже диалоговое окно, где уже указаны необходимые значения IP-адресов.
    
    ![Правило брандмауэра для Stretch](../../sql-server/stretch-database/media/firewall-rule-for-stretch.png)
  
3.  Чтобы настроить в базе данных SQL Server базу данных Stretch, эта база данных должна иметь главный ключ базы данных. Главный ключ базы данных защищает учетные данные, которые база данных Stretch использует для подключения к удаленной базе данных. Ниже приведен пример, в котором создается новый главный ключ базы данных.  
  
    ```tsql  
    USE <database>; 
    GO  
  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD='<password>'; 
    GO
    ```  
    Дополнительные сведения о главном ключе базы данных см. в разделах [CREATE MASTER KEY (Transact-SQL)](../../t-sql/statements/create-master-key-transact-sql.md) и [Создание главного ключа базы данных](../../relational-databases/security/encryption/create-a-database-master-key.md).
    
4.  При настройке базы данных для базы данных Stretch вы должны предоставить учетные данные, которые база данных Stretch будет использовать для обмена данными между локальным SQL Server и удаленным сервером Azure. Имеются две возможности.  
  
    -   Можно предоставить учетные данные администратора.  
  
        -   При включении базы данных Stretch с помощью мастера можно создать учетные данные в это время.  
  
        -   Если база данных Stretch включается путем выполнения команды **ALTER DATABASE**, необходимо вручную создать учетные данные, прежде чем выполнять команду **ALTER DATABASE** для включения базы данных Stretch. 
        
        Ниже приведен пример, в котором создаются новые учетные данные.
  
        ```tsql  
        CREATE DATABASE SCOPED CREDENTIAL <db_scoped_credential_name>  
            WITH IDENTITY = '<identity>' , SECRET = '<secret>' ;
        GO   
        ```  

         Дополнительные сведения об этих учетных данных см. в разделе [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md). Для создания учетных данных требуется разрешение ALTER ANY CREDENTIAL.  

    -   Вы можете использовать федеративную учетную запись службы для взаимодействия SQL Server с удаленным сервером Azure при выполнении следующих условий.  
  
        -   Учетная запись службы, под которой работает экземпляр SQL Server, является доменной учетной записью.  
  
        -   Учетная запись домена принадлежит к домену, Active Directory которого входит в федерацию с Azure Active Directory.  
  
        -   Удаленный сервер Azure настроен для поддержки проверки подлинности Azure Active Directory.  
  
        -   Учетная запись службы, под которой выполняется экземпляр SQL Server, должна быть настроена как учетная запись dbmanager или sysadmin на удаленном сервере Azure.  
  
5.  Чтобы настроить базу данных для базы данных Stretch, выполните команду ALTER DATABASE.  
  
    1.  Для аргумента SERVER укажите имя существующего сервера Azure, включая часть `.database.windows.net` имени, например `MyStretchDatabaseServer.database.windows.net`.  
  
    2.  Предоставьте существующие учетные данные администратора с аргументом CREDENTIAL или укажите FEDERATED_SERVICE_ACCOUNT = ON. В следующем примере предоставляются существующие учетные данные.  
  
    ```tsql  
    ALTER DATABASE <database name>  
        SET REMOTE_DATA_ARCHIVE = ON  
            (  
                SERVER = '<server_name>' ,  
                CREDENTIAL = <db_scoped_credential_name>  
            ) ;  
    GO
    ```  
  
## <a name="next-steps"></a>Следующие шаги  
-   Перемещение дополнительных таблиц описано в статье[Enable Stretch Database for a table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) .  
  
-   Инструкции по отслеживанию статуса переноса данных см. в разделе [Мониторинг и устранение неполадок переноса данных (база данных Stretch)](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).  
  
-   [Приостановка и возобновление переноса данных (база данных Stretch)](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)  
  
-   [Управление базой данных Stretch и устранение связанных с ней неполадок](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)  
  
-   [Резервное копирование баз данных с поддержкой Stretch](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md)  
  
-   [Восстановление баз данных с поддержкой Stretch](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)  
  
## <a name="see-also"></a>См. также:  
 [Определение баз данных и таблиц для базы данных Stretch с использованием помощника базы данных Stretch](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md)   
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  

