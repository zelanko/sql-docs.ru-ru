---
title: Создание группы доступности (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: 8b0a6301-8b79-4415-b608-b40876f30066
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 13d14fafd18fb9e0cdb156617798c8d2f15ff661
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62815367"
---
# <a name="create-an-availability-group-transact-sql"></a>Создание группы доступности (Transact-SQL)
  В данном разделе описывается использование [!INCLUDE[tsql](../../../includes/tsql-md.md)] для создания и настройки группы доступности на основе экземпляров [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , на которых включена функция [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] . *Группа доступности* определяет набор пользовательских баз данных, которые будут действовать при сбое как единое целое, и набор партнеров по обеспечению отработки отказа, называемых *репликами доступности*и поддерживающих отработку отказа.  
  
> [!NOTE]  
>  Базовые сведения о группах доступности см. в разделе [Обзор групп доступности AlwaysOn (SQL Server)](overview-of-always-on-availability-groups-sql-server.md).  
  

  
> [!NOTE]  
>  Вместо [!INCLUDE[tsql](../../../includes/tsql-md.md)]можно использовать мастер создания групп доступности или командлеты [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Использование мастера групп доступности (среда SQL Server Management Studio)](use-the-availability-group-wizard-sql-server-management-studio.md), [Использование диалогового окна "Создание группы доступности" (среда SQL Server Management Studio)](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)или [Создание группы доступности (SQL Server PowerShell)](../../../powershell/sql-server-powershell.md).  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 Настоятельно рекомендуется прочитать этот раздел, прежде чем пытаться настроить свою первую группу доступности.  
  
###  <a name="PrerequisitesRestrictions"></a> Предварительные условия, ограничения и рекомендации  
  
-   Перед созданием группы доступности необходимо, чтобы экземпляры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на которых находятся реплики доступности, были расположены на различных узлах одной отказоустойчивой кластеризации Windows Server (WSFC). Кроме того, убедитесь, что каждый из экземпляров сервера соответствует всем другим обязательным условиям [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Для получения дополнительных сведений настоятельно рекомендуется изучить раздел [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется членство в фиксированной роли сервера **sysadmin** и одно из разрешений: CREATE AVAILABILITY GROUP, ALTER ANY AVAILABILITY GROUP или CONTROL SERVER.  
  
###  <a name="SummaryTsqlStatements"></a> Сводка задач и соответствующих инструкций Transact-SQL  
 В следующей таблице перечислены основные задачи, связанные с созданием и настройкой группы доступности, а также инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] , используемые при выполнении этих задач. Задачи [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] должны выполняться в той последовательности, в которой они перечислены в таблице.  
  
|Задача|Инструкции Transact-SQL|Место выполнения задачи**<sup>*</sup>**|  
|----------|----------------------------------|-------------------------------------------|  
|Создание конечной точки зеркального отображения базы данных (одна точка на экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] )|[CREATE ENDPOINT](/sql/t-sql/statements/create-endpoint-transact-sql) *endpointName* ... ДЛЯ DATABASE_MIRRORING|Выполнить на каждом экземпляре сервера, у которого нет конечной точки зеркального отображения базы данных.|  
|Создание группы доступности|[CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)|Выполнить на экземпляре сервера, где будет размещена исходная первичная реплика.|  
|Присоединить вторичную реплику к группе доступности|[ALTER AVAILABILITY GROUP](join-a-secondary-replica-to-an-availability-group-sql-server.md) *group_name* JOIN|Выполнить на каждом экземпляре сервера, размещающем вторичную реплику.|  
|Подготовьте базу данных-получатель|[BACKUP](/sql/t-sql/statements/backup-transact-sql) и [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql).|Создайте резервные копии на экземпляре сервера, размещающем первичную реплику.<br /><br /> Восстановить резервные копии на каждом экземпляре сервера, размещающем вторичную реплику, используя инструкцию RESTORE WITH NORECOVERY.|  
|Запуск синхронизации данных с помощью присоединения каждой базы данных-получателя к группе доступности|[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) *database_name* SET HADR AVAILABILITY GROUP = *group_name*|Выполнить на каждом экземпляре сервера, размещающем вторичную реплику.|  
  
 **<sup>*</sup>**  Для выполнения данной задачи, подключитесь к указанный экземпляр или экземпляры сервера.  
  
##  <a name="TsqlProcedure"></a> Создание и настройка группы доступности с помощью Transact-SQL  
  
> [!NOTE]  
>  Образец процедуры настройки с примерами кода для каждой из этих инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)] см. в разделе [Пример. Настройка группы доступности, использующей проверку подлинности Windows](#ExampleConfigAGWinAuth)  
  
1.  Подключитесь к экземпляру сервера, на котором должна быть размещена первичная реплика.  
  
2.  Создайте группу доступности с помощью инструкции [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] .  
  
3.  Присоедините новую вторичную реплику к группе доступности. Дополнительные сведения см. в разделе [Присоединение вторичной реплики к группе доступности (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
4.  Для каждой базы данных в группе доступности создайте базу данных-получатель путем восстановления последней резервной копии базы данных-источника с помощью инструкции RESTORE WITH NORECOVERY. Дополнительные сведения см. в разделе [Пример. Настройка группы доступности с использованием проверки подлинности Windows (Transact-SQL)](create-an-availability-group-transact-sql.md), начиная с шага восстановления резервной копии базы данных.  
  
5.  Присоедините каждую новую базу данных-получатель к группе доступности. Дополнительные сведения см. в разделе [Присоединение вторичной реплики к группе доступности (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
##  <a name="ExampleConfigAGWinAuth"></a> Пример. Настройка группы доступности, использующей проверку подлинности Windows  
 В этом примере создается образец процедуры настройки [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , где [!INCLUDE[tsql](../../../includes/tsql-md.md)] используется для настройки конечных точек зеркального отображения базы данных, использующих проверку подлинности Windows для создания и настройки группы доступности и ее баз данных-получателей.  
  
 Этот пример содержит следующие разделы:  
  
-   [Предварительные требования для использования процедуры настройки образца](#PrerequisitesForExample)  
  
-   [Образец процедуры настройки](#SampleProcedure)  
  
-   [Выполните пример кода для процедуры настройки образца](#CompleteCodeExample)  
  
###  <a name="PrerequisitesForExample"></a> Предварительные требования для использования процедуры настройки образца  
 Этот образец процедуры имеет следующие требования.  
  
-   Экземпляры сервера должны поддерживать [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Дополнительные сведения см. в разделе [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md).  
  
-   Оба образца баз данных, *MyDb1* и *MyDb2*, должны существовать на экземпляре сервера, где будет размещаться первичная реплика. В следующем примере кода создаются и настраиваются эти две базы данных и создается полная резервная копия каждой из них. Выполните эти примеры кода на экземпляре сервера, где планируется создавать образец группы доступности. На этом экземпляре сервера будет размещаться первоначальная первичная реплика образца группы доступности.  
  
    1.  В следующем примере [!INCLUDE[tsql](../../../includes/tsql-md.md)] эти базы данных создаются и переключаются на модель полного восстановления:  
  
        ```  
        -- Create sample databases:  
        CREATE DATABASE MyDb1;  
        GO  
        ALTER DATABASE MyDb1 SET RECOVERY FULL;  
        GO  
  
        CREATE DATABASE MyDb2;  
        GO  
        ALTER DATABASE MyDb2 SET RECOVERY FULL;  
        GO  
        ```  
  
    2.  В следующем примере кода создается полная резервная копия баз данных *MyDb1* и *MyDb2*. В этом примере кода используется вымышленная общая папка резервных копий \\\\*FILESERVER*\\*SQLbackups*.  
  
        ```  
        -- Backup sample databases:  
        BACKUP DATABASE MyDb1   
        TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
            WITH FORMAT  
        GO  
  
        BACKUP DATABASE MyDb2   
        TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
            WITH FORMAT  
        GO  
  
        ```  
  
###  <a name="SampleProcedure"></a> Образец процедуры настройки  
 В этом образце настройки реплика доступности будет создана на двух изолированных экземплярах сервера, у которых учетные записи служб выполняются в разных доверенных доменах (`DOMAIN1` и `DOMAIN2`).  
  
 В следующей таблице приведена сводка по значениям, использованным в этом образце конфигурации.  
  
|Первоначальная роль|Система|Узловой экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|------------------|------------|---------------------------------------------|  
|Первичная|`COMPUTER01`|`AgHostInstance`|  
|Вторичная|`COMPUTER02`|Экземпляр по умолчанию.|  
  
1.  Создайте конечную точку зеркального отображения базы данных с именем *dbm_endpoint* в экземпляре сервера, где планируется создать группу доступности (это экземпляр с именем `AgHostInstance` на компьютере `COMPUTER01`). Эта конечная точка использует порт 7022. Обратите внимание, что на экземпляре сервера, где создается группа доступности, будет размещаться первичная реплика.  
  
    ```  
    -- Create endpoint on server instance that hosts the primary replica:  
    CREATE ENDPOINT dbm_endpoint  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
  
    ```  
  
2.  Создайте конечную точку *dbm_endpoint* в экземпляре сервера, где будет размещаться вторичная реплика (это экземпляр сервера по умолчанию на компьютере `COMPUTER02`). Эта конечная точка использует порт 5022.  
  
    ```  
    -- Create endpoint on server instance that hosts the secondary replica:   
    CREATE ENDPOINT dbm_endpoint  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=5022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
  
    ```  
  
3.  > [!NOTE]  
    >  Если учетные записи служб на экземплярах серверов, где планируется размещать реплики доступности, выполняются под одной учетной записью домена, этот шаг выполнять не нужно. Пропустите его и перейдите к следующему шагу.  
  
     Если учетные записи служб на экземплярах серверов работают под разными пользователями домена, создайте на каждом экземпляре сервера имя входа для другого экземпляра сервера и предоставьте этому имени входа разрешение на доступ к конечной точке зеркального отображения локальной базы данных.  
  
     В следующем примере кода приведены инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] для создания имени входа и предоставления ему разрешения для конечной точки. Учетная запись домена на удаленном экземпляре сервера представлена здесь как *имя_домена*\\*имя_пользователя*.  
  
    ```  
    -- If necessary, create a login for the service account, domain_name\user_name  
    -- of the server instance that will host the other replica:  
    USE master;  
    GO  
    CREATE LOGIN [domain_name\user_name] FROM WINDOWS;  
    GO  
    -- And Grant this login connect permissions on the endpoint:  
    GRANT CONNECT ON ENDPOINT::dbm_endpoint   
       TO [domain_name\user_name];  
    GO  
    ```  
  
4.  На экземпляре сервера, размещающем пользовательские базы данных, создайте группу доступности.  
  
     В следующем примере кода создается группа доступности с именем *MyAG* на экземпляре сервера, на котором были созданы образцы баз данных *MyDb1* и *MyDb2*. Сначала указывается локальный экземпляр сервера, `AgHostInstance`, размещенный на компьютере *COMPUTER01* . На этом экземпляре сервера будет размещаться первоначальная первичная реплика. Указано, что на удаленном экземпляре сервера, являющемся экземпляром сервера по умолчанию, размещенном на компьютере *COMPUTER02*, размещена вторичная реплика. Обе реплики доступности настроены для использования асинхронного режима фиксации с переходом на другой ресурс вручную (для реплик с асинхронной фиксацией переход на другой ресурс вручную означает принудительное переключение с возможной потерей данных).  
  
    ```  
  
              -- Create the availability group, MyAG:   
    CREATE AVAILABILITY GROUP MyAG   
       FOR   
          DATABASE MyDB1, MyDB2   
       REPLICA ON   
          'COMPUTER01\AgHostInstance' WITH   
             (  
             ENDPOINT_URL = 'TCP://COMPUTER01.Adventure-Works.com:7022',   
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             ),  
          'COMPUTER02' WITH   
             (  
             ENDPOINT_URL = 'TCP://COMPUTER02.Adventure-Works.com:5022',  
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             );   
    GO  
    ```  
  
     Дополнительные примеры кода [!INCLUDE[tsql](../../../includes/tsql-md.md)], предназначенного для создания группы доступности, см. в разделе [CREATE AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/create-availability-group-transact-sql).  
  
5.  На экземпляре сервера, размещающем вторичную реплику, присоедините ее к группе доступности.  
  
     В следующем примере кода вторичная реплика на компьютере `COMPUTER02` присоединяется к группе доступности `MyAG` .  
  
    ```  
    -- On the server instance that hosts the secondary replica,   
    -- join the secondary replica to the availability group:  
    ALTER AVAILABILITY GROUP MyAG JOIN;  
    GO  
    ```  
  
6.  На экземпляре сервера, размещающем вторичную реплику, создайте базы данных-получатели.  
  
     В следующем примере кода создаются базы данных-получатели *MyDb1* и *MyDb2* путем восстановления резервных копий с помощью инструкции RESTORE WITH NORECOVERY.  
  
    ```  
    -- On the server instance that hosts the secondary replica,   
    -- Restore database backups using the WITH NORECOVERY option:  
    RESTORE DATABASE MyDb1   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH NORECOVERY  
    GO  
  
    RESTORE DATABASE MyDb2   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITH NORECOVERY  
    GO  
  
    ```  
  
7.  На экземпляре сервера, размещающем первичную реплику, создайте резервную копию журнала транзакций каждой из баз данных-источников.  
  
    > [!IMPORTANT]  
    >  При настройке реальной группы доступности рекомендуется перед созданием такой резервной копии журнала приостановить задачи резервного копирования журнала для баз данных-источников до тех пор, пока к группе доступности не будут присоединены соответствующие базы данных-получатели.  
  
     В следующем примере кода создается резервная копия журнала транзакций для баз данных MyDb1 и MyDb2.  
  
    ```  
    -- On the server instance that hosts the primary replica,   
    -- Backup the transaction log on each primary database:  
    BACKUP LOG MyDb1   
    TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH NOFORMAT  
    GO  
  
    BACKUP LOG MyDb2   
    TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITHNOFORMAT  
    GO  
  
    ```  
  
    > [!TIP]  
    >  Как правило, резервная копия журнала должна создаваться для каждой базы данных-источника а затем восстанавливаться в соответствующей базе данных-получателе (с помощью инструкции WITH NORECOVERY). Однако в этой резервной копии журнала может не быть необходимости, если база данных только что создана и резервной копии журнала еще нет либо модель восстановления только что сменили с SIMPLE на FULL.  
  
8.  На экземпляре сервера, размещающем вторичную реплику, примените резервные копии журналов к базам данных-получателям.  
  
     В следующем примере кода показано применение резервных копий к базам данных-получателям *MyDb1* и *MyDb2* путем восстановления резервных копий с помощью инструкции RESTORE WITH NORECOVERY.  
  
    > [!IMPORTANT]  
    >  При подготовке производственной базы данных-получателя следует применить все резервные копии журналов, созданные после резервного копирования базы данных, из которой была создана база данных-получатель, начиная с самой ранней, обязательно с помощью инструкции RESTORE WITH NORECOVERY. Естественно, при восстановлении как полной, так и разностной резервной копии потребуется применить резервные копии журналов, созданные только после разностного резервного копирования.  
  
    ```  
    -- Restore the transaction log on each secondary database,  
    -- using the WITH NORECOVERY option:  
    RESTORE LOG MyDb1   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    RESTORE LOG MyDb2   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
9. На экземпляре сервера, размещающем вторичную реплику, присоедините новую базу данных-получателя к группе доступности.  
  
     В следующем примере кода к группе доступности *MyDb1* присоединяется база данных-получатель *MyDb2* , а затем база данных-получатель *MyAG* .  
  
    ```  
    -- On the server instance that hosts the secondary replica,   
    -- join each secondary database to the availability group:  
    ALTER DATABASE MyDb1 SET HADR AVAILABILITY GROUP = MyAG;  
    GO  
  
    ALTER DATABASE MyDb2 SET HADR AVAILABILITY GROUP = MyAG;  
    GO  
  
    ```  
  
###  <a name="CompleteCodeExample"></a> Выполните пример кода для процедуры настройки образца  
 Следующий пример кода объединяет в себе примеры кода из всех шагов с образцом процедуры настройки. В следующей таблице приведена сводка значений заполнителей, использованных в этом примере кода. Дополнительные сведения о шагах в этом примере кода см. в подразделах [Предварительные требования для использования процедуры настройки образца](#PrerequisitesForExample) и [Образец процедуры настройки](#SampleProcedure)выше в этом разделе.  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|\\\\*FILESERVER*\\*SQLbackups*|Вымышленная общая папка резервных копий.|  
|\\\\*FILESERVER*\\*SQLbackups\MyDb1.bak*|Файл резервной копии для базы данных MyDb1.|  
|\\\\*FILESERVER*\\*SQLbackups\MyDb2.bak*|Файл резервной копии для базы данных MyDb2.|  
|*7022*|Номер порта, присвоенный каждой конечной точке зеркального отображения базы данных.|  
|*COMPUTER01\AgHostInstance*|Экземпляр сервера, на котором размещается первоначальная первичная реплика.|  
|*COMPUTER02*|Экземпляр сервера, на котором размещается первоначальная вторичная реплика. Это экземпляр сервера по умолчанию на компьютере `COMPUTER02`.|  
|*dbm_endpoint*|Имя, заданное для каждой конечной точки зеркального отображения базы данных.|  
|*MyAG*|Имя образца группы доступности.|  
|*MyDb1*|Имя первого образца базы данных.|  
|*MyDb2*|Имя второго образца базы данных.|  
|*Домен1\пользователь1*|Учетная запись службы экземпляра сервера, на котором планируется размещать первоначальную основную реплику.|  
|*Домен2\пользователь2*|Учетная запись службы экземпляра сервера, на котором планируется размещать первоначальную вторичную реплику.|  
|TCP://*COMPUTER01.Adventure-Works.com*:*7022*|URL-адрес конечной точки экземпляра AgHostInstance сервера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на компьютере COMPUTER01.|  
|TCP://*COMPUTER02.Adventure-Works.com*:*5022*|URL-адрес конечной точки экземпляра сервера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по умолчанию на компьютере COMPUTER02.|  
  
> [!NOTE]  
>  Дополнительные примеры кода [!INCLUDE[tsql](../../../includes/tsql-md.md)], предназначенного для создания группы доступности, см. в разделе [CREATE AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/create-availability-group-transact-sql).  
  
```  
-- on the server instance that will host the primary replica,   
-- create sample databases:  
CREATE DATABASE MyDb1;  
GO  
ALTER DATABASE MyDb1 SET RECOVERY FULL;  
GO  
  
CREATE DATABASE MyDb2;  
GO  
ALTER DATABASE MyDb2 SET RECOVERY FULL;  
GO  
  
-- Backup sample databases:  
BACKUP DATABASE MyDb1   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH FORMAT  
GO  
  
BACKUP DATABASE MyDb2   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH FORMAT  
GO  
  
-- Create the endpoint on the server instance that will host the primary replica:  
CREATE ENDPOINT dbm_endpoint  
    STATE=STARTED   
    AS TCP (LISTENER_PORT=7022)   
    FOR DATABASE_MIRRORING (ROLE=ALL)  
GO  
  
-- Create the endpoint on the server instance that will host the secondary replica:   
CREATE ENDPOINT dbm_endpoint  
    STATE=STARTED   
    AS TCP (LISTENER_PORT=7022)   
    FOR DATABASE_MIRRORING (ROLE=ALL)  
GO  
  
-- If both service accounts run under the same domain account, skip this step. Otherwise,   
-- On the server instance that will host the primary replica,   
-- create a login for the service account   
-- of the server instance that will host the secondary replica, DOMAIN2\user2,   
-- and grant this login connect permissions on the endpoint:  
USE master;  
GO  
CREATE LOGIN [DOMAIN2\user2] FROM WINDOWS;  
GO  
GRANT CONNECT ON ENDPOINT::dbm_endpoint   
   TO [DOMAIN2\user2];  
GO  
  
-- If both service accounts run under the same domain account, skip this step. Otherwise,   
-- On the server instance that will host the secondary replica,  
-- create a login for the service account   
-- of the server instance that will host the primary replica, DOMAIN1\user1,   
-- and grant this login connect permissions on the endpoint:  
USE master;  
GO  
  
CREATE LOGIN [DOMAIN1\user1] FROM WINDOWS;  
GO  
GRANT CONNECT ON ENDPOINT::dbm_endpoint   
   TO [DOMAIN1\user1];  
GO  
  
-- On the server instance that will host the primary replica,   
-- create the availability group, MyAG:  
CREATE AVAILABILITY GROUP MyAG   
   FOR   
      DATABASE MyDB1, MyDB2   
   REPLICA ON   
      'COMPUTER01\AgHostInstance' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER01.Adventure-Works.com:7022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC  
         ),  
      'COMPUTER02' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER02.Adventure-Works.com:7022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC  
         );   
GO  
  
-- On the server instance that hosts the secondary replica,   
-- join the secondary replica to the availability group:  
ALTER AVAILABILITY GROUP MyAG JOIN;  
GO  
  
-- Restore database backups onto this server instance, using RESTORE WITH NORECOVERY:  
RESTORE DATABASE MyDb1   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH NORECOVERY  
GO  
  
RESTORE DATABASE MyDb2   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH NORECOVERY  
GO  
  
-- Back up the transaction log on each primary database:  
BACKUP LOG MyDb1   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH NOFORMAT  
GO  
  
BACKUP LOG MyDb2   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITHNOFORMAT  
GO  
  
-- Restore the transaction log on each secondary database,  
-- using the WITH NORECOVERY option:  
RESTORE LOG MyDb1   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH FILE=1, NORECOVERY  
GO  
RESTORE LOG MyDb2   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH FILE=1, NORECOVERY  
GO  
  
-- On the server instance that hosts the secondary replica,   
-- join each secondary database to the availability group:  
ALTER DATABASE MyDb1 SET HADR AVAILABILITY GROUP = MyAG;  
GO  
  
ALTER DATABASE MyDb2 SET HADR AVAILABILITY GROUP = MyAG;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Настройка свойств группы доступности и реплики**  
  
-   [Смена режима доступности для реплики доступности (SQL Server)](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Смена режима отработки отказа для реплики доступности (SQL Server)](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Настройка гибкой политики отработки отказа для обеспечения контроля над для автоматической отработки отказа (группы доступности AlwaysOn)](configure-flexible-automatic-failover-policy.md)  
  
-   [Укажите URL-адрес конечной точки при добавлении или изменении реплики доступности (SQL Server)](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Настройка резервного копирования в репликах доступности (SQL Server)](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Настройка доступа только для чтения в реплике доступности (SQL Server)](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Настройка маршрутизации только для чтения в группе доступности (SQL Server)](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Изменение периода ожидания сеанса для реплики доступности (SQL Server)](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **Завершение настройки группы доступности**  
  
-   [Присоединение вторичной реплики к группе доступности (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Подготовка базы данных-получателя для присоединения к группе доступности вручную (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Присоединение базы данных-получателя к группе доступности (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **Другие способы создания группы доступности**  
  
-   [Использование мастера групп доступности (среда SQL Server Management Studio)](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Использование диалогового окна "Создание группы доступности" (среда SQL Server Management Studio)](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Создание группы доступности (SQL Server PowerShell)](../../../powershell/sql-server-powershell.md)  
  
 **Чтобы включить группы доступности AlwaysOn**  
  
-   [Включение и отключение групп доступности AlwaysOn (SQL Server)](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 **Настройка конечной точки зеркального отображения базы данных**  
  
-   [Создание базы данных конечной точки зеркального отображения для групп доступности AlwaysOn &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Использование сертификатов для конечной точки зеркального отображения базы данных (Transact-SQL)](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [Укажите URL-адрес конечной точки при добавлении или изменении реплики доступности (SQL Server)](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **Устранение неполадок с конфигурацией групп доступности AlwaysOn**  
  
-   [Устранение неполадок конфигурации групп доступности AlwaysOn (SQL Server) удалена](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Устранение неполадок с операцией добавления файла, завершившейся сбоем &#40;группы доступности AlwaysOn&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> См. также  
  
-   **Блоги**  
  
     [AlwaysON — HADRON обучающая серия. Использование рабочего пула для баз данных с HADRON](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [Блоги группы AlwaysOn SQL Server: Официальный блог по SQL Server AlwaysOn Team](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Блоги инженеров CSS SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Видеоролики**  
  
     [Серия Microsoft SQL Server с кодовым названием «Denali» AlwaysOn, часть 1: вводные сведения о решении следующего поколения по обеспечению высокого уровня доступности](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Серия Microsoft SQL Server с кодовым названием «Denali» AlwaysOn, часть 2: Создание решения критически важных высокого уровня доступности с помощью AlwaysOn](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Технические документы**  
  
     [Microsoft SQL Server AlwaysOn Solutions Guide for высокий уровень доступности и аварийного восстановления](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Технические документы Майкрософт Microsoft по SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Технические документы группы консультантов по SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>См. также:  
 [Конечная точка зеркального отображения базы данных (SQL Server)](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../listeners-client-connectivity-application-failover.md)   
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
