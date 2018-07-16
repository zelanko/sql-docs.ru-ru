---
title: Настройка маршрутизации только для чтения в группе доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- read-only routing
- Availability Groups [SQL Server], readable secondary replicas
- Availability Groups [SQL Server], read-only routing
- readable secondary replicas
- Availability Groups [SQL Server], client connectivity
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 7bd89ddd-0403-4930-a5eb-3c78718533d4
caps.latest.revision: 30
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 07a56151370935f0162afd3a6e4013628d04045c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245722"
---
# <a name="configure-read-only-routing-for-an-availability-group-sql-server"></a>Настройка маршрутизации только для чтения в группе доступности (SQL Server)
  Чтобы настроить группу доступности AlwaysOn для поддержки маршрутизации только для чтения в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], можно использовать процедуру [!INCLUDE[tsql](../../../includes/tsql-md.md)] или PowerShell. *Маршрутизация только для чтения* означает способность [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] направлять уточняющие запросы на соединение только для чтения к имеющейся [доступной для чтения вторичной реплике](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) AlwaysOn (то есть реплике, настроенной для разрешения рабочих нагрузок только для чтения при выполнении вторичной роли). Для поддержки маршрутизации только для чтения группа доступности должна иметь [прослушиватель группы доступности](../../listeners-client-connectivity-application-failover.md). Клиент, запрашивающий данные в режиме только чтения, должен направлять свои запросы к данному прослушивателю, а строки подключения клиента должны определять намерение приложения как «только для чтения». Это означает, что они должны быть *запросами на соединение с правами чтения*.  
  
> [!NOTE]  
>  Дополнительные сведения о настройке доступной для чтения вторичной реплики см. в разделе [Настройка доступа только для чтения в реплике доступности (SQL Server)](configure-read-only-access-on-an-availability-replica-sql-server.md).  
  

  
    > [!NOTE]  
    >  Configuring read-only routing is not supported by [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  

  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Группа доступности должна обладать прослушивателем группы доступности. Дополнительные сведения см. в разделе [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md).  
  
-   Один или несколько реплик доступности необходимо настроить для принятия только для чтения во вторичной роли (то есть быть [вторичные реплики для чтения](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)(AlwaysOn % 20Availability % 20Groups\).md)). Дополнительные сведения см. в статье [Настройка доступа только для чтения в реплике доступности (SQL Server)](configure-read-only-access-on-an-availability-replica-sql-server.md).  
  
-   Необходимо подключиться к экземпляру сервера, на котором размещена текущая первичная реплика.  
  
###  <a name="RORReplicaProperties"></a> Какие свойства реплики необходимо настроить для поддержки маршрутизации только для чтения?  
  
-   Для каждой доступной для чтения вторичной реплики, которая поддерживает маршрутизацию только для чтения, необходимо указать *URL-адрес маршрутизации только для чтения*. Этот URL-адрес задействуется, только если локальная реплика выполняется под вторичной ролью. URL-адрес маршрутизации только для чтения должен быть указан для каждой реплики отдельно (если для реплики требуется подобная маршрутизация). Все URL-адреса маршрутизации только для чтения используются для направления запросов на соединение с намерением чтения к определенной доступной для чтения вторичной реплике. Как правило, каждой доступной для чтения вторичной реплике назначается URL-адрес маршрутизации только для чтения.  
  
     Дополнительные сведения о вычислении URL-адреса маршрутизации только для чтения для реплики доступности см. в разделе [Вычисление для AlwaysOn](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-alwayson.aspx).  
  
-   Для каждой реплики доступности, которая должна поддерживать маршрутизацию только для чтения и при этом являющейся первичной, необходимо задать *список маршрутизации только для чтения*. Определенный список маршрутизации только для чтения вступает в силу, только если локальная реплика выполняется под первичной ролью. Такой список должен указываться для тех конкретных реплик, для которых он требуется. Как правило, каждый список маршрутизации только для чтения будет содержать все URL-адреса маршрутизации только для чтения, причем URL-адрес локальной реплики будет идти в конце списка.  
  
    > [!NOTE]  
    >  Запросы на соединение с намерением чтения направляются в первую имеющуюся вторичную реплику доступную для чтения из списка маршрутизации только для чтения текущей первичной реплики. Балансировка нагрузки отсутствует.  
  
> [!NOTE]  
>  Сведения о прослушивателях групп доступности и дополнительные сведения о маршрутизации только для чтения см. в разделе [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../listeners-client-connectivity-application-failover.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
  
|Задача|Разрешения|  
|----------|-----------------|  
|Настройка реплик при создании группы доступности|Требуется членство в фиксированной роли сервера **sysadmin** и одно из разрешений: CREATE AVAILABILITY GROUP, ALTER ANY AVAILABILITY GROUP или CONTROL SERVER.|  
|Изменение реплики доступности|Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.|  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Чтобы настроить маршрутизацию только для чтения**  
  
> [!NOTE]  
>  Пример кода см. в подразделе [Пример (Transact-SQL)](#TsqlExample)далее в этом разделе.  
  
1.  Подключитесь к экземпляру сервера, на котором находится первичная реплика.  
  
2.  Если вы указываете реплику для новой группы доступности, воспользуйтесь инструкцией [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] . Если вы добавляете или изменяете реплику для существующей группы доступности, воспользуйтесь инструкцией [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] .  
  
    -   Чтобы настроить маршрутизацию только для чтения для вторичной роли, укажите в предложении ADD REPLICA или MODIFY REPLICA WITH параметр SECONDARY_ROLE следующим образом:  
  
         SECONDARY_ROLE **(** READ_ONLY_ROUTING_URL **= "** TCP **://*`system-address`*:*`port`*")**  
  
         Существуют следующие параметры URL-адреса маршрутизации только для чтения.  
  
         *system-address*  
         Это строка, такая как адрес системы, полное доменное имя или IP-адрес, однозначно идентифицирующий целевую компьютерную систему.  
  
         *port*  
         Номер порта, который используется компонентом ядра СУБД экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
         Например:   `SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433')`  
  
         В предложении MODIFY REPLICA параметр ALLOW_CONNECTIONS не является обязательным, если реплика уже настроена для соединений только для чтения.  
  
         Дополнительные сведения см. в разделе [Вычисления для AlwaysOn](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-alwayson.aspx).  
  
    -   Чтобы настроить маршрутизацию только для чтения для первичной роли, в предложении ADD REPLICA или MODIFY REPLICA WITH укажите параметр PRIMARY_ROLE следующим образом:  
  
         PRIMARY_ROLE **(** READ_ONLY_ROUTING_LIST **= ("*`server`*"** [ **,**... *n* ] **))**  
  
         Здесь *server* идентифицирует экземпляр сервера, на котором размещена вторичная реплика только для чтения в группе доступности.  
  
         Например:   `PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('Server1','Server2'))`  
  
        > [!NOTE]  
        >  Необходимо настроить URL-адрес маршрутизации только для чтения перед настройкой списка маршрутизации только для чтения.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере изменяются две реплики доступности существующей группы доступности `AG1` для поддержки маршрутизации только для чтения в том случае, если одна из этих реплик в настоящий момент обладает первичной ролью. Чтобы определить экземпляры сервера, на которых размещена реплика доступности, в этом примере указаны имена экземпляров —`COMPUTER01` и `COMPUTER02`.  
  
```  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER02.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER02','COMPUTER01')));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER01','COMPUTER02')));  
GO  
  
```  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Чтобы настроить маршрутизацию только для чтения**  
  
> [!NOTE]  
>  Пример кода см. в подразделе [Пример (PowerShell)](#PSExample)далее в этом разделе.  
  
1.  Значение по умолчанию (`cd`) к экземпляру сервера, на котором размещена первичная реплика.  
  
2.  При добавлении реплики доступности в группу доступности воспользуйтесь командлетом `New-SqlAvailabilityReplica`. При изменении существующей реплики доступности воспользуйтесь командлетом `Set-SqlAvailabilityReplica`. Соответствующие параметры:  
  
    -   Чтобы настроить маршрутизацию только для чтения для вторичной роли, укажите **ReadonlyRoutingConnectionUrl»*`url`*"** параметра.  
  
         Здесь *url* — это полное доменное имя и порт, которые используются для маршрутизации к реплике соединений только для чтения. Например:  `-ReadonlyRoutingConnectionUrl "TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024"`  
  
         Дополнительные сведения см. в разделе [Вычисления для AlwaysOn](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-alwayson.aspx).  
  
    -   Чтобы настроить доступ соединения для первичной роли, укажите **ReadonlyRoutingList»*`server`*"** [ **,**... *n* ], где *server* обозначает экземпляр сервера, на котором размещена вторичная реплика только для чтения в группе доступности. Например:  `-ReadOnlyRoutingList "SecondaryServer","PrimaryServer"`  
  
        > [!NOTE]  
        >  Необходимо настроить URL-адрес маршрутизации только для чтения для реплики перед тем, как перейти к настройке ее списка маршрутизации.  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, используйте `Get-Help` командлет в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] среде PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Получение справок по SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
###  <a name="PSExample"></a> Пример (PowerShell)  
 В следующем примере выполняется настройка первичной реплики и одной вторичной реплики в группе доступности с использованием маршрутизации только для чтения. С начала примера каждой реплике присваивается URL-адрес для маршрутизации только для чтения. Затем для первичной реплики задается список маршрутизации только для чтения. Соединения со свойством «ReadOnly» в строке подключения будут перенаправляться на вторичную реплику. Если такая вторичная реплика недоступна для чтения (в соответствии со значением параметра `ConnectionModeInSecondaryRole`), соединение направляется обратно в первичную реплику.  
  
```  
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  
$secondaryReplica = Get-Item "AvailabilityReplicas\SecondaryServer"  
  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://PrimaryServer.domain.com:1433" -InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://SecondaryServer.domain.com:1433" -InputObject $secondaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingList "SecondaryServer","PrimaryServer" -InputObject $primaryReplica  
```  
  
##  <a name="FollowUp"></a> Продолжение: после настройки маршрутизации только для чтения  
 Как только текущая первичная реплика и предназначенные для чтения вторичные реплики будут настроены для поддержки маршрутизации только для чтения в обеих ролях, предназначенные для чтения вторичные реплики смогут принимать запросы соединения с намерением чтения от клиентов, которые подключаются через прослушиватель группы доступности.  
  
> [!TIP]  
>  При использовании [служебная программа bcp](../../../tools/bcp-utility.md) или [служебная программа sqlcmd](../../../tools/sqlcmd-utility.md), можно указать доступ только для чтения к любой вторичной реплике, которая включена для доступа только для чтения, указав `-K ReadOnly` переключения.  
  
###  <a name="ConnStringReqsRecs"></a> Требования и рекомендации для строк подключения клиента  
 В случае если клиентское приложение использует маршрутизацию только для чтения, его строка подключения должна удовлетворять следующим требованиям.  
  
-   Используйте протокол TCP.  
  
-   Задайте атрибут/свойство намерения приложения как «только для чтения».  
  
-   Создайте ссылку на прослушиватель группы доступности, настроенный для поддержки маршрутизации только для чтения.  
  
-   Сошлитесь на базу данных в этой группе доступности.  
  
 Кроме того, рекомендуется, чтобы строки подключения использовали отработку отказа резервных подсетей при сбое, что поддерживает параллельный клиентский поток для каждой реплики в каждой подсети. Это позволяет свести к минимуму повторное подключение клиента после отработки отказа.  
  
 Синтаксис строки подключения зависит от поставщика SQL Server, который использует приложение. Следующий пример строки подключения для поставщика данных .NET Framework 4.0.2 для SQL Server демонстрирует фрагменты строки подключения, которые необходимы и рекомендуются для работы с маршрутизацией только для чтения.  
  
```  
Server=tcp:MyAgListener,1433;Database=Db1;IntegratedSecurity=SSPI;ApplicationIntent=ReadOnly;MultiSubnetFailover=True  
```  
  
 Дополнительные сведения о намерении приложения и маршрутизации только для чтения см. в разделе [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../listeners-client-connectivity-application-failover.md).  
  
### <a name="if-read-only-routing-is-not-working-correctly"></a>Маршрутизация только для чтения работает неправильно  
 Сведения об устранении неполадок с конфигурацией маршрутизации только для чтения, см. в разделе [ Маршрутизация только для чтения работает неправильно —](troubleshoot-always-on-availability-groups-configuration-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Просмотр конфигурации маршрутизации только для чтения**  
  
-   [sys.availability_read_only_routing_lists (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
  
-   [sys.availability_replicas (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) (столбец **read_only_routing_url**)  
  
 **Настройка доступа соединения клиентов**  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Настройка доступа только для чтения в реплике доступности (SQL Server)](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
 **Использование строк подключения в приложениях**  
  
-   [Поддержка высокого уровня доступности и аварийного восстановления собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [Использование ключевых слов строки подключения с собственным клиентом SQL Server](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
##  <a name="RelatedContent"></a> См. также  
  
-   **Блоги**  
  
     [Вычисление значения read_only_routing_url для AlwaysOn](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-alwayson.aspx)  
  
     [Блоги группы AlwaysOn SQL Server: Официальный блог SQL Server AlwaysOn Team](http://blogs.msdn.com/b/sqlalwayson/)  
  
     [Блоги инженеров CSS SQL Server](http://blogs.msdn.com/b/psssql/)  
  
-   **Технические документы**  
  
     [Технические документы Майкрософт Microsoft по SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Технические документы группы консультантов по SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Активные вторичные реплики: Для чтения вторичные реплики (группы доступности AlwaysOn)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)   
 [Сведения о доступе клиентского подключения к репликам доступности (SQL Server)](about-client-connection-access-to-availability-replicas-sql-server.md)   
 [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../listeners-client-connectivity-application-failover.md)  
  
  
