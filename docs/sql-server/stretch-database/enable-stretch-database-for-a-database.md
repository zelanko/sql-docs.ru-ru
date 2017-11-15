---
title: "Настройка Stretch Database для базы данных | Документация Майкрософт"
ms.custom: SQL2016_New_Updated
ms.date: 08/05/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, enabling database
- enabling database for Stretch Database
ms.assetid: 37854256-8c99-4566-a552-432e3ea7c6da
caps.latest.revision: "70"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 59ad1742daa12e2ea501888b15b9aa8075b7001d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="enable-stretch-database-for-a-database"></a>Включение Stretch Database для базы данных
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Чтобы настроить существующую базу данных для Stretch Database, в SQL Server Management Studio выберите для базы данных команду **Задачи | Растяжение | Включить**, чтобы открыть мастер **разрешения операции растяжения для базы данных**. Кроме того, вы можете использовать Transact-SQL, чтобы включить Stretch Database для базы данных.  
  
 Если выбрать для таблицы команду **Задачи |Растяжение | Включить** , предварительно не включив базу данных для Stretch Database, мастер сначала настроит базу данных для Stretch Database и позволит вам выбрать таблицы в рамках этого процесса. Выполните шаги из этой статьи вместо статьи [Enable Stretch Database for a table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).  
  
 Чтобы настроить Stretch Database для таблицы или базы данных, требуются права db_owner. Кроме того, чтобы настроить Stretch Database для базы данных, требуются права CONTROL DATABASE.  

 >   [!NOTE]
 > Если позднее вы решите отключить Stretch Database, помните, что ее отключение для таблицы или базы данных не ведет к удалению удаленного объекта. Если вы хотите удалить удаленную таблицу или базу данных, это нужно сделать с помощью портала управления Azure. Пока удаленные объекты не будут удалены вручную, их хранение будет сопровождаться затратами в Azure. 
 
## <a name="before-you-get-started"></a>Перед началом работы  
  
-   Перед настройкой базы данных для Stretch рекомендуется запустить помощник по настройке Stretch Database, чтобы определить базы данных и таблицы, подходящие для Stretch. Помощник по настройке Stretch Database, кроме того, обнаруживает блокирующие проблемы. Дополнительные сведения см. в статье [Определение баз данных и таблиц для Stretch Database с использованием помощника Stretch Database](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md).  
  
-   Изучите раздел [Ограничения для Stretch Database](../../sql-server/stretch-database/limitations-for-stretch-database.md).  
  
-   Stretch Database перемещает данные в Azure. Таким образом, необходимо иметь учетную запись Azure и подписку для выставления счетов. Для получения учетной записи Azure [нажмите здесь](http://azure.microsoft.com/en-us/pricing/free-trial/).  
  
-   Убедитесь в наличии информации о подключении и данных входа, необходимых для создания нового сервера Azure или выбора существующего сервера Azure.  
  
##  <a name="EnableTSQLServer">
            </a> Обязательное требование: включение Stretch Database на сервере  
 Перед включением Stretch Database в базе данных или таблице необходимо включить ее на локальном сервере. Для этой операции требуются права sysadmin или serveradmin.  
  
-   При наличии нужных административных разрешений мастер **включения базы данных для Stretch** настроит сервер для Stretch.  
  
-   Если у вас нет необходимых разрешений, администратор должен вручную включить этот параметр, выполнив команду **sp_configure** перед запуском мастера, либо администратор должен запустить этот мастер.  
  
 Чтобы включить Stretch Database на сервере вручную, выполните команду **sp_configure** и включите параметр **remote data archive** . В следующем примере включается параметр **remote data archive** путем изменения его значения на 1.  
  
```sql
EXEC sp_configure 'remote data archive' , '1';  
GO

RECONFIGURE;  
GO  
```  
  
 Дополнительные сведения см. в разделе [Настройка параметра конфигурации сервера для удаленного архива данных](../../database-engine/configure-windows/configure-the-remote-data-archive-server-configuration-option.md) и [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
##  <a name="Wizard">
            </a> Настройка Stretch Database в базе данных с помощью мастера  
 Сведения о мастере включения базы данных для Stretch, включая описание информации, которую необходимо указать, и вариантов, из которых необходимо выбрать, см. в разделе [Запуск мастера включения базы данных для Stretch](../../sql-server/stretch-database/get-started-by-running-the-enable-database-for-stretch-wizard.md).  
  
##  <a name="EnableTSQLDatabase">
            </a> Настройка Stretch Database в базы данных с помощью Transact-SQL  
 Перед включением Stretch Database в отдельных таблицах необходимо включить ее в базе данных.  
  
 Чтобы настроить Stretch Database для таблицы или базы данных, требуются права db_owner. Кроме того, чтобы настроить Stretch Database для базы данных, требуются права CONTROL DATABASE.  
  
1.  Прежде чем начать, выберите существующий сервер Azure для данных, миграцию которых выполняет Stretch Database, или создайте новый сервер Azure.  
  
2.  На сервере Azure создайте правило брандмауэра с диапазоном IP-адресов SQL Server, позволяющим SQL Server обмениваться данными с удаленным сервером.  

    Вы можете легко найти нужные значения и создать правило брандмауэра, попытавшись подключиться к серверу Azure из обозревателя объектов в среде SQL Server Management Studio (SSMS). Среда SSMS поможет вам создать правило, открыв приведенное ниже диалоговое окно, где уже указаны необходимые значения IP-адресов.
    
    ![Правило брандмауэра для Stretch](../../sql-server/stretch-database/media/firewall-rule-for-stretch.png)
  
3.  Чтобы настроить в базе данных SQL Server базу данных Stretch Database, эта база данных должна иметь главный ключ базы данных. Главный ключ базы данных защищает учетные данные, которые Stretch Database использует для подключения к удаленной базе данных. Ниже приведен пример, в котором создается новый главный ключ базы данных.  
  
    ```sql  
    USE <database>; 
    GO  
  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD='<password>'; 
    GO
    ```  
    Дополнительные сведения о главном ключе базы данных см. в разделах [CREATE MASTER KEY (Transact-SQL)](../../t-sql/statements/create-master-key-transact-sql.md) и [Создание главного ключа базы данных](../../relational-databases/security/encryption/create-a-database-master-key.md).
    
4.  При настройке базы данных для Stretch Database вы должны предоставить учетные данные, которые Stretch Database будет использовать для обмена данными между локальным SQL Server и удаленным сервером Azure. Имеются две возможности.  
  
    -   Можно предоставить учетные данные администратора.  
  
        -   При включении Stretch Database с помощью мастера можно создать учетные данные в это время.  
  
        -   Если Stretch Database включается путем выполнения команды **ALTER DATABASE**, необходимо вручную создать учетные данные, прежде чем выполнять команду **ALTER DATABASE** для включения Stretch Database. 
        
        Ниже приведен пример, в котором создаются новые учетные данные.
  
        ```sql  
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
  
5.  Чтобы настроить базу данных для Stretch Database, выполните команду ALTER DATABASE.  
  
    1.  Для аргумента SERVER укажите имя существующего сервера Azure, включая часть `.database.windows.net` имени, например `MyStretchDatabaseServer.database.windows.net`.  
  
    2.  Предоставьте существующие учетные данные администратора с аргументом CREDENTIAL или укажите FEDERATED_SERVICE_ACCOUNT = ON. В следующем примере предоставляются существующие учетные данные.  
  
    ```sql  
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
 [Определение баз данных и таблиц для Stretch Database с использованием помощника Stretch Database](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md)   
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  
