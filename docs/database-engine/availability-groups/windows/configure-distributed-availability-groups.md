---
title: Настройка распределенной группы доступности (группы доступности AlwaysOn) | Документы Майкрософт
ms.custom: ''
ms.date: 08/17/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f7c7acc5-a350-4a17-95e1-e689c78a0900
caps.latest.revision: 28
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d2c059a63e181c6615d1cb60de1a8c8d650e0fc0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="configure-distributed-availability-group"></a>Настройка распределенной группы доступности  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Для создания распределенной группы доступности необходимо создать группу доступности и прослушиватель в каждом отказоустойчивом кластере Windows (WSFC). После этого можно объединить эти группы доступности в распределенную группу доступности. Ниже представлен простой пример c Transact-SQL. В этом примере представлены не все детали создания группы доступности и прослушивателей; основное внимание уделяется ключевым требованиям. 

Технические сведения о распределенных группах доступности см. в статье [Распределенные группы доступности](distributed-availability-groups.md).   

## <a name="prerequisites"></a>предварительные требования

### <a name="set-the-endpoint-listeners-to-listen-to-all-ip-addresses"></a>Настройка прослушивателей конечных точек на прослушивание всех IP-адресов

Убедитесь, что конечные точки могут взаимодействовать между различными группами доступности в распределенной группе доступности. Если в одной группе доступности задана определенная сеть в конечной точке, распределенная группа доступности будет работать неправильно. На каждом сервере, на котором будет размещаться реплика группы доступности, настройте прослушиватель на `LISTENER_IP = ALL`. 

#### <a name="create-a-listener-to-listen-to-all-ip-addresses"></a>Создание прослушивателя для прослушивания всех IP-адресов

Например, следующий скрипт создает в TCP-порте 5022 конечную точку прослушивателя, которая прослушивает все IP-адреса.  

```sql
CREATE ENDPOINT [aodns-hadr] 
    STATE=STARTED
    AS TCP (LISTENER_PORT = 5022, LISTENER_IP = ALL)
FOR DATA_MIRRORING (
   ROLE = ALL, 
   AUTHENTICATION = WINDOWS NEGOTIATE,
   ENCRYPTION = REQUIRED ALGORITHM AES
)
GO
```

#### <a name="alter-a-listener-to-listen-to-all-ip-addresses"></a>Изменение прослушивателя для прослушивания всех IP-адресов

Например, следующий скрипт изменяет конечную точку прослушивателя таким образом, чтобы прослушивались все IP-адреса.  

```sql
ALTER ENDPOINT [aodns-hadr] 
    AS TCP (LISTENER_IP = ALL)
GO
```

## <a name="create-first-availability-group"></a>Создание первой группы доступности

### <a name="create-the-primary-availability-group-on-the-first-cluster"></a>Создание первичной группы доступности в первом кластере  
Создайте группу доступности в первом кластере WSFC.   В этом примере это группа доступности с именем `ag1` для базы данных `db1`.      
  
```sql  
CREATE AVAILABILITY GROUP [ag1]   
FOR DATABASE db1   
REPLICA ON N'server1' WITH (ENDPOINT_URL = N'TCP://server1.contoso.com:5022',  
    FAILOVER_MODE = AUTOMATIC,  
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server2' WITH (ENDPOINT_URL = N'TCP://server2.contoso.com:5022',   
    FAILOVER_MODE = AUTOMATIC,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
  
```  
  
>[!NOTE]
>В предыдущем примере используется прямое присвоение начальных значений, где **SEEDING_MODE** получает значение **AUTOMATIC** как для реплик, так и для распределенной группы доступности. С такой конфигурацией вторичные реплики и вторичная группа доступности заполняются автоматически и не требуют резервного копирования и восстановления первичной базы данных вручную.  
  
### <a name="join-the-secondary-replicas-to-the-primary-availability-group"></a>Присоединение вторичной реплики к первичной группе доступности  
Все вторичные реплики должны быть присоединены к группе доступности **ALTER AVAILABILITY GROUP** с параметром **JOIN** . Поскольку в этом примере используется прямое присвоение начальных значений, необходимо, помимо прочего, вызвать метод  **ALTER AVAILABILITY GROUP** с параметром **GRANT CREATE ANY DATABASE** . Это позволяет группе доступности создать базу данных и начать ее автоматическое заполнение из первичной реплики.  
  
В этом примере во вторичной реплике `server2`выполняются указанные ниже команды, предназначенные для присоединения группы доступности `ag1` . После этого группа доступности получает возможность создавать базы данных во вторичной реплике.  
  
```sql  
ALTER AVAILABILITY GROUP [ag1] JOIN   
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE  
GO  
```  

>[!NOTE]
>Когда группа доступности создает базу данных во вторичной реплике, она устанавливает в качестве владельца базы данных учетную запись, от имени которой была выполнена инструкция `ALTER AVAILABILITY GROUP`, предоставляя этой учетной записи разрешение на создание любых баз данных. Дополнительные сведения см. в разделе [Предоставление группе доступности разрешения на создание базы данных во вторичной реплике](automatic-seeding-secondary-replicas.md#grantCreate).
  
### <a name="create-a-listener-for-the-primary-availability-group"></a>Создание прослушивателя для первичной группы доступности  

После этого добавьте прослушиватель для первичной группы доступности в первый кластер WSFC. В этом примере прослушиватель имеет имя `ag1-listener`. Подробные инструкции по созданию прослушивателя см. в разделе [Создание или настройка прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
  
```sql
ALTER AVAILABILITY GROUP [ag1]    
    ADD LISTENER 'ag1-listener' ( 
        WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , 
        PORT = 60173);    
GO  
```  
  

## <a name="create-second-availability-group"></a>Создание второй группы доступности  
 Создайте вторую группу доступности, `ag2`, во втором кластере WSFC. В этом случае база данных не указана, так как она автоматически заполняется данными из первичной группы доступности.  
  
```sql  
CREATE AVAILABILITY GROUP [ag2]   
FOR   
REPLICA ON N'server3' WITH (ENDPOINT_URL = N'TCP://server3.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server4' WITH (ENDPOINT_URL = N'TCP://server4.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
```  
  
> [!NOTE]  
> Во вторичной группе доступности необходимо использовать ту же конечную точку зеркального отображения базы данных (в этом примере — порт 5022). В противном случае после локальной отработки отказа репликация будет остановлена.  
  
### <a name="join-the-secondary-replicas-to-the-secondary-availability-group"></a>Присоединение вторичных реплик к вторичной группе доступности  
 В этом примере во вторичной реплике `server4`выполняются указанные ниже команды, предназначенные для присоединения группы доступности `ag2` . После этого группа доступности получает возможность создавать базы данных во вторичной реплике для прямого присвоения начальных значений.  
  
```sql  
ALTER AVAILABILITY GROUP [ag2] JOIN   
ALTER AVAILABILITY GROUP [ag2] GRANT CREATE ANY DATABASE  
GO  
```  
  
### <a name="create-a-listener-for--the-secondary-availability-group"></a>Создание прослушивателя для вторичной группы доступности  
 После этого добавьте прослушиватель для вторичной группы доступности во второй кластер WSFC. В этом примере прослушиватель имеет имя `ag2-listener`. Подробные инструкции по созданию прослушивателя см. в разделе [Создание или настройка прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
  
```  
ALTER AVAILABILITY GROUP [ag2]    
    ADD LISTENER 'ag2-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  
## <a name="create-distributed-availability-group-on-first-cluster"></a>Создание распределенной группы доступности в первом кластере  
 В первом WSFC создайте распределенную группу доступности (в этом примере она называется `distributedag` ). Используйте команду **CREATE AVAILABILITY GROUP** с параметром **DISTRIBUTED** . Параметр **AVAILABILITY GROUP ON** указывает группы доступности, входящие в состав распределенной группы доступности: `ag1` и `ag2`.  
  
```sql  
CREATE AVAILABILITY GROUP [distributedag]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO   
```  
  
> [!NOTE]  
>  **LISTENER_URL** указывает прослушиватель для каждой группы доступности, а также конечную точку зеркального отображения базы данных для группы доступности. В этом примере это порт `5022` (а не порт `60173` , который использовался для создания прослушивателя). Если вы используете подсистему балансировки нагрузки, например в Azure, [добавьте правило балансировки нагрузки для порта распределенной группы доступности](http://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-alwayson-int-listener#add-load-balancing-rule-for-distributed-availability-group). Добавьте правило для порта прослушивателя в дополнение к порту экземпляра SQL Server. 
  
## <a name="join-distributed-availability-group-on-second-cluster"></a>Присоединение распределенной группы доступности во втором кластере  
 Присоедините распределенную группу доступности во втором кластере WSFC.  
  
```sql  
ALTER AVAILABILITY GROUP [distributedag]   
   JOIN   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO  
```  

## <a name="failover"></a>Присоединение базы данных во вторичной реплике второй группы доступности
Когда база данных во вторичной реплике второй группы доступности перейдет в состояние восстановления, вам нужно вручную присоединить ее к группе доступности.

```sql  
ALTER DATABASE [db1] SET HADR AVAILABILITY GROUP = [ag2];   
```  
  
## <a name="failover"></a> Отработка отказа во вторичную группу доступности  
В настоящее время поддерживается только отработка отказа вручную. Следующая инструкция Transact-SQL проводит отработку отказа в распределенную группу доступности с именем `distributedag`.  


1. Задайте в качестве режима доступности синхронную фиксацию для обеих групп доступности. 
    
      ```sql  
      ALTER AVAILABILITY GROUP [distributedag] 
      MODIFY 
      AVAILABILITY GROUP ON
      'ag1' WITH 
         ( 
          LISTENER_URL = 'tcp://ag1-listener.contoso.com:5022',  
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = MANUAL, 
          SEEDING_MODE = MANUAL 
          ), 
      'ag2' WITH  
        ( 
        LISTENER_URL = 'tcp://ag2-listener.contoso.com:5022', 
        AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
        FAILOVER_MODE = MANUAL, 
        SEEDING_MODE = MANUAL 
        );  
       
      ```  
   >[!NOTE]
   >Как и в обычных группах доступности, состояние синхронизации между двумя репликами групп доступности, которые входят в распределенную группу доступности, зависит от режима доступности обеих реплик. Например, для синхронной фиксации текущая первичная и вторичная группы доступности должны быть настроены с использованием режима доступности synchronous_commit.  


1. Подождите, пока состояние распределенной группы доступности изменится на `SYNCHRONIZED`. Выполните следующий запрос в SQL Server, где размещена первичная реплика основной группы доступности. 
    
      ```sql  
      SELECT ag.name
             , drs.database_id
             , drs.group_id
             , drs.replica_id
             , drs.synchronization_state_desc
             , drs.end_of_log_lsn 
        FROM sys.dm_hadr_database_replica_states drs,
        sys.availability_groups ag
          WHERE drs.group_id = ag.group_id;      
      ```  

    Продолжите работу, когда параметр **synchronization_state_desc** группы доступности примет значение `SYNCHRONIZED`. Если параметр **synchronization_state_desc** не равен `SYNCHRONIZED`, запускайте команду каждые пять секунд, пока он не изменится. Не продолжайте работу до установки состояния **synchronization_state_desc** = `SYNCHRONIZED`. 

1. На сервере SQL Server, где размещается первичная реплика первичной группы доступности, задайте для роли распределенной группы доступности значение `SECONDARY`. 

    ```sql
    ALTER AVAILABILITY GROUP distributedag SET (ROLE = SECONDARY); 
    ```  

    На этом этапе распределенная группа доступности недоступна.

1. Проверьте готовность к отработке отказа. Выполните следующий запрос:

    ```sql
    SELECT ag.name, 
        drs.database_id, 
        drs.group_id, 
        drs.replica_id, 
        drs.synchronization_state_desc, 
        drs.end_of_log_lsn 
    FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
    WHERE drs.group_id = ag.group_id; 
    ```  
    Группа доступности готова к отработке отказа, если **synchronization_state_desc** имеет значение `SYNCHRONIZED`, а **end_of_log_lsn** совпадает для обеих групп доступности. 

1. Проведите отработку отказа из первичной группы доступности во вторичную. Запустите следующую команду в SQL Server, где размещена первичная реплика дополнительной группы доступности. 

    ```sql
    ALTER AVAILABILITY GROUP distributedag FORCE_FAILOVER_ALLOW_DATA_LOSS; 
    ```  

    После этого этапа распределенная группа доступности будет доступна.
      
После выполнения описанных выше шагов, распределенная группа доступности выполняет отработку отказа без потери данных. Если группы доступности находятся на удаленном расстоянии друг от друга, что приводит к задержке, измените режим доступности обратно на ASYNCHRONOUS_COMMIT. 
  
## <a name="remove-a-distributed-availability-group"></a>Удаление распределенной группы доступности  
 Следующая инструкция Transact-SQL удаляет распределенную группу доступности с именем `distributedag`:  
  
```sql  
DROP AVAILABILITY GROUP [distributedag]  
```  

## <a name="create-distributed-availability-group-on-failover-cluster-instances"></a>Создание распределенной группы доступности в экземплярах отказоустойчивого кластера

Вы можете создать распределенную группу доступности, используя группу доступности на экземпляре отказоустойчивого кластера (FCI). В этом случае прослушиватель группы доступности не требуется. Используйте имя виртуальной сети (VNN) для первичной реплики экземпляра отказоустойчивого кластера. В следующем примере показана распределенная группа доступности с именем SQLFCIDAG. Группа доступности SQLFCIAG SQLFCIAG содержит две реплики FCI. Имя виртуальной сети для первичной реплики FCI имеет значение SQLFCIAG-1, а для вторичной — SQLFCIAG-2. Распределенная группа доступности также включает в себя SQLAG-DR для аварийного восстановления.

![Распределенная группа доступности AlwaysOn](../../../database-engine/availability-groups/windows/media/always-on-availability-group-distributed.png)

 
 
 Следующая инструкция DDL создает эту распределенную группу доступности. 

```sql  
CREATE AVAILABILITY GROUP [SQLFCIDAG]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
  'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-1.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      ),   
  'SQLAG-DR' WITH    
       (   
         LISTENER_URL = 'tcp://SQLAG-DR.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      );   
```  

URL-адрес прослушивателя соответствует имени виртуальной сети первичного экземпляра FCI.

## <a name="manually-fail-over-fci-in-distributed-availability-group"></a>Ручная отработка отказа отказоустойчивого кластера в распределенной группе доступности

Для выполнения ручной отработки отказа в группе доступности отказоустойчивого кластера обновите распределенную группу доступности в соответствии с измененным URL-адресом прослушивателя. Например, выполните следующую инструкцию DDL как в основной, так и в дополнительной группах доступности SQLFCIAG:

```sql  
ALTER AVAILABILITY GROUP [SQLFCIDAG]  
   MODIFY AVAILABILITY GROUP ON  
 'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-2.contoso.com:5022'
    )
```  
  
## <a name="next-steps"></a>Следующие шаги

 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP (Transact-SQL)](../../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
