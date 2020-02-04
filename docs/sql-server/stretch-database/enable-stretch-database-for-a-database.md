---
title: Включение Stretch Database для базы данных
ms.date: 08/05/2016
ms.service: sql-server-stretch-database
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database, enabling database
- enabling database for Stretch Database
ms.assetid: 37854256-8c99-4566-a552-432e3ea7c6da
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: db08d84dd1619d8c9e2e4d8e796abdd0c9d202fc
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "73844593"
---
# <a name="enable-stretch-database-for-a-database"></a>Включение Stretch Database для базы данных
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly.md)]


  Чтобы настроить имеющуюся базу данных для использования со службой Stretch Database, выберите **Задачи | Stretch Database | Включить** для базы данных в SQL Server Management Studio. После этого откроется мастер **включения Stretch Database для базы данных**. Кроме того, вы можете использовать Transact-SQL, чтобы включить Stretch Database для базы данных.  
  
 Если при выборе **Задачи &gt; Перенос &gt; Включить** для отдельной таблицы служба Stretch Database для базы данных еще не включена, то мастер сначала настроит базу данных для Stretch Database и позволит выбрать таблицы в ходе этого процесса. Выполните шаги из этой статьи вместо шагов из статьи [Включение Stretch Database для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).  
  
 Чтобы настроить Stretch Database для таблицы или базы данных, требуются права db_owner. Для включения Stretch Database для базы данных также требуются разрешения CONTROL DATABASE.  

> [!NOTE]
> В случае последующего отключения Stretch Database для таблицы или базы данных помните, что такое отключение не приводит к удалению дистанционного объекта. Если вы хотите удалить удаленную таблицу или базу данных, это нужно сделать с помощью портала управления Azure. Пока удаленные объекты не будут удалены вручную, их хранение будет сопровождаться затратами в Azure. 
 
## <a name="before-you-get-started"></a>Необходимые условия  
  
-   Перед настройкой базы данных для Stretch Database рекомендуется запустить Помощник по Stretch Database, чтобы определить базы данных и таблицы, которые можно использовать со Stretch Database. Помощник по Stretch Database также определит критические препятствия. Дополнительные сведения см. в статье [Определение баз данных и таблиц для Stretch Database с использованием помощника Stretch Database](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md).  
  
-   Ознакомьтесь со статьей [Ограничения контактной зоны и критические препятствия для использования Stretch Database](../../sql-server/stretch-database/limitations-for-stretch-database.md).  
  
-   Служба Stretch Database переносит данные в Azure. Таким образом, необходимо иметь учетную запись Azure и подписку для выставления счетов. Для получения учетной записи Azure [нажмите здесь](https://azure.microsoft.com/pricing/free-trial/).  
  
-   Убедитесь в наличии информации о подключении и данных входа, необходимых для создания нового сервера Azure или выбора существующего сервера Azure.  
  
##  <a name="EnableTSQLServer"></a> Обязательное требование: включение Stretch Database на сервере  
 Перед включением службы Stretch Database для базы данных или таблицы необходимо включить ее на локальном сервере. Для этой операции требуются права sysadmin или serveradmin.  
  
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
  
##  <a name="Wizard"></a> Настройка Stretch Database в базе данных с помощью мастера  
 Сведения о мастере включения базы данных для Stretch, включая описание информации, которую необходимо указать, и вариантов, из которых необходимо выбрать, см. в разделе [Запуск мастера включения базы данных для Stretch](../../sql-server/stretch-database/get-started-by-running-the-enable-database-for-stretch-wizard.md).  
  
##  <a name="EnableTSQLDatabase"></a> Настройка Stretch Database в базы данных с помощью Transact-SQL  
 Перед включением службы Stretch Database для отдельных таблиц необходимо включить ее для базы данных.  
  
 Чтобы настроить Stretch Database для таблицы или базы данных, требуются права db_owner. Для включения Stretch Database для базы данных также требуются разрешения CONTROL DATABASE.  
  
1.  Прежде чем начать, выберите существующий или создайте новый сервер Azure для данных, которые будут перенесены службой Stretch Database.  
  
2.  На сервере Azure создайте правило брандмауэра с диапазоном IP-адресов сервера SQL Server. Это правило позволит SQL Server обмениваться данными с удаленным сервером.  

    Вы можете легко найти нужные значения и создать правило брандмауэра, попытавшись подключиться к серверу Azure из обозревателя объектов в среде SQL Server Management Studio (SSMS). Среда SSMS поможет вам создать правило, открыв приведенное ниже диалоговое окно, где уже указаны необходимые значения IP-адресов.
    
    ![Правило брандмауэра для Stretch](../../sql-server/stretch-database/media/firewall-rule-for-stretch.png)
  
3.  Для настройки базы данных SQL Server для использования со Stretch Database необходим главный ключ базы данных. Главный ключ базы данных защищает учетные данные, используемые для подключения к удаленной базе данных, использующей Stretch Database. Ниже приведен пример, в котором создается новый главный ключ базы данных.  
  
    ```sql  
    USE <database>; 
    GO  
  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD='<password>'; 
    GO
    ```  
    Дополнительные сведения о главном ключе базы данных см. в разделах [CREATE MASTER KEY (Transact-SQL)](../../t-sql/statements/create-master-key-transact-sql.md) и [Создание главного ключа базы данных](../../relational-databases/security/encryption/create-a-database-master-key.md).
    
4.  При настройке базы данных для Stretch Database необходимо предоставить учетные данные, которые будут использоваться для обмена данными между локальным SQL Server и удаленным сервером Azure. Имеются две возможности.  
  
    -   Можно предоставить учетные данные администратора.  
  
        -   Если вы включаете Stretch Database с помощью мастера, можно указать учетные данные с помощью мастера.  
  
        -   Если вы собираетесь включить Stretch Database, используя инструкцию **ALTER DATABASE**, вам нужно создать учетные данные вручную, прежде чем запускать инструкцию **ALTER DATABASE**. 
        
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
  
5.  Чтобы настроить базу данных для использования со Stretch Database, выполните инструкцию ALTER DATABASE.  
  
    1.  Для аргумента SERVER укажите имя существующего сервера Azure, включая часть `.database.windows.net` имени, например `MyStretchDatabaseServer.database.windows.net`.  
  
    2.  Предоставьте существующие учетные данные администратора с аргументом CREDENTIAL или укажите FEDERATED_SERVICE_ACCOUNT = ON. В примере ниже приведены существующие учетные данные.  
  
    ```sql  
    ALTER DATABASE <database name>  
        SET REMOTE_DATA_ARCHIVE = ON  
            (  
                SERVER = '<server_name>' ,  
                CREDENTIAL = <db_scoped_credential_name>  
            ) ;  
    GO
    ```  
  
## <a name="next-steps"></a>Дальнейшие действия  
-   [Включение Stretch Database для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md), чтобы активировать дополнительные таблицы.  
  
-   Инструкции по отслеживанию статуса переноса данных см. в разделе [Мониторинг и устранение неполадок переноса данных (Stretch Database)](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).  
  
-   [Приостановка и возобновление переноса данных (Stretch Database)](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)  
  
-   [Управление Stretch Database и устранение связанных с ней неполадок](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)  
  
-   [Резервное копирование баз данных с поддержкой Stretch](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md)  
  
-   [Восстановление баз данных с поддержкой Stretch](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)  
  
## <a name="see-also"></a>См. также:  
 [Определение баз данных и таблиц для Stretch Database с использованием помощника Stretch Database](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md)   
 [Параметры ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  
