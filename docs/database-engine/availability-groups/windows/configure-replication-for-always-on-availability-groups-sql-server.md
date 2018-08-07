---
title: Настройка репликации для групп доступности AlwaysOn (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 07/09/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 4e001426-5ae0-4876-85ef-088d6e3fb61c
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 1a69bac2eb9cbbb90949be501891fd873684ea36
ms.sourcegitcommit: d9b7625322a2c7444ed25ca311d63fe70eb6fa0a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39509014"
---
# <a name="configure-replication-for-always-on-availability-groups-sql-server"></a>Настройка репликации для групп доступности AlwaysOn (SQL Server)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Настройка репликации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и групп доступности AlwaysOn включает в себя семь шагов. Каждый шаг более подробно описывается в следующих разделах.  
  
1.  [Настройка публикаций и подписок баз данных.](#step1)  
  
2.  [Настройка группы доступности AlwaysOn.](#step2)  
  
3.  [Проверка настройки всех узлов вторичных реплик для репликации.](#step3)  
  
4.  [Настройка узлов вторичных реплик в качестве издателей репликации.](#step4)  
  
5.  [Перенаправление первоначального издателя на имя прослушивателя группы доступности.](#step5)  
  
6.  [Запуск хранимой процедуры проверки для проверки конфигурации.](#step6)  
  
7.  [Добавление первоначального издателя в монитор репликации.](#step7)  
  
 Шаги 1 и 2 могут выполняться в любом порядке.  
  
##  <a name="step1"></a> 1. Настройка публикаций и подписок баз данных  
 **Настройка распространителя**  
  
 Базу данных распространителя нельзя поместить в группу доступности.  
  
1.  Настройка распространения на распространителе. Если хранимые процедуры используются для настройки, запустите **sp_adddistributor**. Используйте параметр *@password* для определения пароля, который будет использоваться при подключении удаленного издателя к распространителю. Кроме того, пароль понадобится для каждого удаленного издателя при настройке удаленного распространителя.  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = '**Strong password for distributor**';  
    ```  
  
2.  Создайте базу данных распространителя на распространителе. Если хранимые процедуры используются для настройки, запустите **sp_adddistributiondb**.  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistributiondb  
        @database = 'distribution',  
        @security_mode = 1;  
    ```  
  
3.  Настройка удаленного издателя. Если хранимые процедуры используются для настройки распространителя, запустите **sp_adddistpublisher**. Параметр *@security_mode* используется для определения того, как хранимая процедура проверки издателя, которая запускается при помощи агентов репликации, подключается к текущей первичной реплике. Если значение равно 1, то для подключения к текущей первичной реплике будет использоваться проверка подлинности Windows. Если значение равно 0, используется проверка подлинности службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с указанными значениями *@login* и *@password* . Указанное имя входа и пароль должны быть действительными на каждой вторичной реплике для хранимой процедуры проверки в целях успешного подключения к этой реплике.  
  
    > [!NOTE]  
    >  Если какие-либо измененные агенты репликации будут работать на компьютере, отличном от распространителя, использование проверки подлинности Windows для подключения к первичной реплике потребует проверки подлинности Kerberos, настроенной для передачи данных между главными компьютерами реплик. Использование имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для соединения с текущей первичной репликой не потребует проверки подлинности Kerberos.  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistpublisher  
        @publisher = 'AGPrimaryReplicaHost',  
        @distribution_db = 'distribution',  
        @working_directory = '\\MyReplShare\WorkingDir',  
        @login = 'MyPubLogin',  
        @password = '**Strong password for publisher**';  
    ```  
  
 Дополнительные сведения см. в статье [sp_adddistpublisher (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md).  
  
 **Настройка издателя на первоначальном издателе**  
  
1.  Настройка удаленного распространения. Если хранимые процедуры используются для настройки издателя, запустите **sp_adddistributor**. Укажите то же значение для *@password* , которое использовалось, когда процедура **sp_adddistrbutor** была запущена на распространителе для настройки распространения.  
  
    ```  
    exec sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = 'MyDistPass'  
    ```  
  
2.  Включите базу данных для репликации. Если хранимые процедуры используются для настройки издателя, запустите **sp_replicationdboption**. Если для базы данных должны быть настроены и репликация транзакций, и репликация слиянием, необходимо включить каждую из них.  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'true';  
  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'merge publish',  
        @value = 'true';  
    ```  
  
3.  Создайте публикацию, статьи и подписки репликации. Дополнительные сведения о том, как настроить репликацию, см. в разделе «Публикация данных и объектов базы данных».  
  
##  <a name="step2"></a> 2. Настройка группы доступности AlwaysOn  
 В будущей первичной реплике создайте группу доступности с опубликованной (или которой предстоит публикация) базой данных в качестве базы данных-участника. При использовании мастера группы доступности можно либо разрешить мастеру выполнить первоначальную синхронизацию базы данных вторичной реплики, либо выполнить инициализацию вручную при помощи резервного копирования и восстановления.  
  
 Создайте прослушиватель DNS для группы доступности, которая будет использоваться агентами репликации для подключения к текущей первичной реплике. Указанное имя прослушивателя будет использоваться в качестве цели перенаправления для первоначального издателя и опубликованной базы данных. Например, если настройка группы доступности выполняется с помощью языка DDL, можно использовать следующий пример кода, чтобы указать прослушиватель для существующей группы доступности с именем `MyAG`:  
  
```  
ALTER AVAILABILITY GROUP 'MyAG'   
    ADD LISTENER 'MyAGListenerName' (WITH IP (('10.120.19.155', '255.255.254.0')));  
```  
  
 Дополнительные сведения см. в статье [Создание и настройка групп доступности (SQL Server)](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md).  
 
> [!NOTE]  
>  Не удается включить репликацию для баз данных в группе доступности при включении DTC_Support с помощью параметра Per_DB.  
  
##  <a name="step3"></a> 3. Проверка настройки всех узлов вторичной реплики для репликации  
 На каждом узле вторичной реплики убедитесь, что служба [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] настроена для поддержки репликации. Следующий запрос можно запустить на каждом узле вторичной реплики, чтобы определить, установлена ли репликация:  
  
```  
USE master;  
GO  
DECLARE @installed int;  
EXEC @installed = sys.sp_MS_replication_installed;  
SELECT @installed;  
```  
  
 Если значение параметра *@installed* равно 0, то необходимо добавить репликацию к установке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
##  <a name="step4"></a> 4. Настройка узлов вторичной реплики в качестве издателей репликации  
 Вторичная реплика не может выступать в роли издателя репликации или переиздающего подписчика, однако репликацию необходимо настроить так, чтобы вторичная реплика могла взять на себя нагрузку после отработки отказа. На распространителе настройте распространение для каждого узла вторичной реплики. Укажите ту же базу данных распространителя и рабочий каталог, что и при добавлении первоначального издателя к распространителю. При использовании хранимых процедур для настройки распространения примените **sp_adddistpublisher** для связи удаленных издателей с распространителем. Если значение параметра *@login* и *@password* использовались для первоначального издателя, укажите те же значения каждого из этих параметров при добавлении узлов вторичной реплики в качестве издателей.  
  
```  
EXEC sys.sp_adddistpublisher  
    @publisher = 'AGSecondaryReplicaHost',  
    @distribution_db = 'distribution',  
    @working_directory = '\\MyReplShare\WorkingDir',  
    @login = 'MyPubLogin',  
    @password = '**Strong password for publisher**';  
```  
  
 На каждом узле вторичной реплики настройте распространение. Укажите распространителя оригинального издателя в качестве удаленного распространителя. Используйте тот же пароль, который применялся при первоначальном запуске **sp_adddistributor** на распространителе. Если хранимые процедуры используются для настройки распространения, параметр *@password* процедуры **sp_adddistributor** применяется для указания пароля.  
  
```  
EXEC sp_adddistributor   
    @distributor = 'MyDistributor',  
    @password = '**Strong password for distributor**';  
```  
  
 На каждом узле вторичной реплики убедитесь, что подписчики по запросу на публикации базы данных отображаются как связанные серверы. Если для настройки удаленных издателей используются хранимые процедуры, примените **sp_addlinkedserver** для добавления подписчиков (если они еще не установлены) в качестве связанных серверов для издателей.  
  
```  
EXEC sys.sp_addlinkedserver   
    @server = 'MySubscriber';  
```  
  
##  <a name="step5"></a> 5. Перенаправление первоначального издателя на имя прослушивателя группы доступности  
 На распространителе в базе данных распространителя запустите хранимую процедуру **sp_redirect_publisher** , чтобы связать первоначального издателя и опубликованную базу данных с именем прослушивателя группы доступности.  
  
```  
USE distribution;  
GO  
EXEC sys.sp_redirect_publisher   
@original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = 'MyAGListenerName';  
```  
  
##  <a name="step6"></a> 6. Запуск хранимой процедуры проверки репликации для проверки конфигурации  
 На распространителе в базе данных распространителя запустите хранимую процедуру **sp_validate_replica_hosts_as_publishers** для проверки настройки всех узлов реплики для работы в качестве издателей опубликованной базы данных.  
  
```  
USE distribution;  
GO  
DECLARE @redirected_publisher sysname;  
EXEC sys.sp_validate_replica_hosts_as_publishers  
    @original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = @redirected_publisher output;  
```  
  
 Хранимая процедура **sp_validate_replica_hosts_as_publishers** должна быть запущена от имени входа с достаточными правами авторизации на каждом узле реплики группы доступности для выполнения запроса сведений о группе доступности. В отличие от **sp_validate_redirected_publisher**, для подключения к репликам группы доступности в ней используются учетные данные вызывающего объекта, а не имя входа, хранимое в msdb.dbo.MSdistpublishers.  
  
> [!NOTE]  
>  Работа**sp_validate_replica_hosts_as_publishers** завершится сбоем со следующей ошибкой при проверке узлов вторичной реплики, которые не допускают доступ для чтения либо требуют указания намерения чтения.  
>   
>  Сообщение 21899, уровень 11, состояние 1, процедура **sp_hadr_verify_subscribers_at_publisher**, строка 109  
>   
>  Запрос на перенаправленном издателе «MyReplicaHostName» для определения того, имеются ли записи sysserver для подписчиков исходного издателя «MyOriginalPublisher» , завершился с ошибкой «976»; сообщение об ошибке: «Ошибка 976, уровень 14, состояние 1, сообщение: Целевая база данных «MyPublishedDB» участвует в группе доступности и в настоящее время недоступна для запросов. Либо перемещение данных приостанавливается, либо реплика доступности не разрешена для чтения. Чтобы разрешить доступ только для чтения к этой и другим базам данных в группе доступности, задайте доступ для чтения одной или нескольким вторичным репликам доступности в группе.  Дополнительные сведения см. в описании инструкции **ALTER AVAILABILITY GROUP** в электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
>   
>  Произошла одна или несколько ошибок проверки издателя для узла реплики «MyReplicaHostName».  
  
 Такой результат является ожидаемым. Необходимо проверить наличие записей сервера подписчика на данных узлах вторичной реплики, выполнив запрос записей sysserver непосредственно на узле.  
  
##  <a name="step7"></a> 7. Добавление первоначального издателя в монитор репликации  
 В каждой реплике группы доступности добавьте оригинального издателя в монитор репликации.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Репликация**  
  
-   [Обслуживание базы данных публикации AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)  
  
-   [Репликация, отслеживание изменений, изменение данных и группы доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/replicate-track-change-data-capture-always-on-availability.md)  
  
-   [Администрирование (репликация)](../../../relational-databases/replication/administration/administration-replication.md)  
  
 **Создание и настройка группы доступности**  
  
-   [Использование мастера групп доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Использование диалогового окна "Создание группы доступности" (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Создание группы доступности (Transact-SQL)](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
-   [Создание группы доступности (SQL Server PowerShell)](../../../database-engine/availability-groups/windows/create-an-availability-group-sql-server-powershell.md)  
  
-   [Указание URL-адреса конечной точки при добавлении или изменении реплики доступности (SQL Server)](../../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Создание конечной точки зеркального отображения базы данных для групп доступности AlwaysOn (SQL Server PowerShell)](../../../database-engine/availability-groups/windows/database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Присоединение вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Подготовка базы данных-получателя для присоединения к группе доступности вручную (SQL Server)](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Присоединение базы данных-получателя к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)   
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Группы доступности AlwaysOn: взаимодействие (SQL Server)](../../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md)   
 [Репликация SQL Server](../../../relational-databases/replication/sql-server-replication.md)  
  
  
