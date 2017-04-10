---
title: "Распределенные группы доступности (группы доступности AlwaysOn) | Microsoft Docs"
ms.custom: ""
ms.date: "08/30/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7c7acc5-a350-4a17-95e1-e689c78a0900
caps.latest.revision: 28
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 28
---
# Распределенные группы доступности (группы доступности AlwaysOn)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Распределенные группы доступности позволяют связывать две группы доступности, размещенные в разных отказоустойчивых кластерах Windows Server (WSFC). Одна из основных областей применения распределенных групп доступности — это аварийное восстановление, при котором первичный сайт географически отделяется от сайта аварийного восстановления. При этом данные необходимо постоянно реплицировать на сайт аварийного восстановления, но при этом сделать так, чтобы возможная проблема в сети на сайте аварийного восстановления не привела к отказу первичного сайта.  
  
 Представленная ниже схема иллюстрирует архитектуру распределенной группы доступности.  
  
 ![AlwaysOn Distributed Availability Groups](../../../database-engine/availability-groups/windows/media/alwayson-distributed-availability-groups.png "AlwaysOn Distributed Availability Groups")  
  
 На схеме показаны два отдельных отказоустойчивых кластера Windows Server (WFSC 1 и WFSC 2). Каждый кластер имеет собственную группу доступности с соответствующей конфигурацией базы данных. Распределенную группу доступности можно рассматривать как "группу доступности групп доступности". В этом примере AG 1 становится первичной группой доступности. Все вставки и обновления выполняются в первичной реплике, AG 1, а затем реплицируются во вторичные реплики. Кроме того, изменения однократно реплицируются по сети во вторичную группу доступности в кластере WSFC 2. Группа доступности AG 2 реплицирует эти изменения в свою вторичную реплику.  
  
> [!IMPORTANT]  
>  Как только между двумя группами доступности устанавливаются отношения группы доступности, вторичная группа доступности становится доступной только для чтения. Вставки и обновления можно обновлять только в первичной реплике первичной группы доступности (в этом примере это первичная реплика группы доступности 1).  
  
 Распределенные группы доступности имеют следующие отличия от группы доступности в отказоустойчивом кластере Windows Server.  
  
-   Каждый кластер WSFC имеет собственный режим кворума и конфигурацию голосования узлов. Это означает, что работоспособность вторичного кластера WSFC не влияет на первичный WSFC.  
  
-   Данные однократно отправляются по сети во вторичный кластер WSFC, а затем реплицируются в пределах этого кластера. В пределах одного кластера WSFC данные отправляются в каждую реплику отдельно. Распределенные группы доступности более эффективны для географически распределенного вторичного сайта.  
  
-   В первичном и вторичном кластерах могут использоваться разные версии операционной системы. На всех серверах в кластере WSFC должна быть установлена одна и та же версия ОС. Это позволяет использовать распределенные группы доступности для последовательных обновлений и обновлений операционной системы.  
  
-   Первичная и вторичная группы обеспечения доступности должны иметь одинаковую конфигурацию баз данных.  
  
-   Во вторичной группе доступности автоматический переход на другой ресурс не поддерживается.  
  
## Создание распределенной группы доступности  
 Для создания распределенной группы доступности необходимо создать группу доступности и прослушиватель в каждом кластере WSFC. После этого их можно объединить в распределенную группу доступности. Ниже представлен простой пример c Transact-SQL. В этом примере представлены на все детали создания группы доступности и прослушивателей; основное внимание уделяется ключевым требованиям.  
  
### Создание первичной группы доступности в первом кластере  
 Создайте группу доступности в первом кластере WSFC.   В этом примере это группа доступности с именем `ag1` для базы данных `db1`.  
  
```tsql  
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
  
 Обратите внимание, что в этом примере используется прямое присвоение начальных значений, где **SEEDING_MODE** получает значение **AUTOMATIC** как для реплик, так и для распределенной группы доступности. Это означает, что после установки вторичные реплики и вторичная группа доступности заполняются автоматически и не требуют архивирования и восстановления первичной базы данных вручную.  
  
### Присоединение вторичной реплики к первичной группе доступности  
 Все вторичные реплики должны быть присоединены к группе доступности **ALTER AVAILABILITY GROUP** с параметром **JOIN** . Поскольку в этом примере используется прямое присвоение начальных значений, необходимо, помимо прочего, вызвать метод  **ALTER AVAILABILITY GROUP** с параметром **GRANT CREATE ANY DATABASE** . Это позволяет группе доступности создать базу данных и начать ее автоматическое заполнение из первичной реплики.  
  
 В этом примере во вторичной реплике `server2`выполняются указанные ниже команды, предназначенные для присоединения группы доступности `ag1` . После этого группа доступности получает возможность создавать базы данных во вторичной реплике.  
  
```tsql  
ALTER AVAILABILITY GROUP [ag1] JOIN   
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE  
GO  
```  
  
### Создание прослушивателя для первичной группы доступности  
 После этого добавьте прослушиватель для первичной группы доступности в первый кластер WSFC. В этом примере прослушиватель имеет имя `ag1-listener`. Подробные инструкции по созданию прослушивателя см. в разделе [Создание или настройка прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
  
```  
ALTER AVAILABILITY GROUP [ag1]    
    ADD LISTENER 'ag1-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  
### Создание вторичной группы доступности во втором кластере  
 Создайте вторую группу доступности, `ag2`, во втором кластере WSFC. В данном случае база данных не указана, поскольку автоматически заполняется данными из первичной группы доступности.  
  
```tsql  
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
>  Обратите внимание, что во вторичной группе доступности необходимо использовать ту же конечную точку зеркального отображения базы данных (в этом примере — порт 5022). В противном случае после локальной отработки отказа репликация будет остановлена.  
  
### Присоединение вторичных реплик к вторичной группе доступности  
 В этом примере во вторичной реплике `server4`выполняются указанные ниже команды, предназначенные для присоединения группы доступности `ag2` . После этого группа доступности получает возможность создавать базы данных во вторичной реплике для прямого присвоения начальных значений.  
  
```tsql  
ALTER AVAILABILITY GROUP [ag2] JOIN   
ALTER AVAILABILITY GROUP [ag2] GRANT CREATE ANY DATABASE  
GO  
```  
  
### Создание прослушивателя для вторичной группы доступности  
 После этого добавьте прослушиватель для вторичной группы доступности во второй кластер WSFC. В этом примере прослушиватель имеет имя `ag2-listener`. Подробные инструкции по созданию прослушивателя см. в разделе [Создание или настройка прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
  
```  
ALTER AVAILABILITY GROUP [ag2]    
    ADD LISTENER 'ag2-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  
### Создание распределенной группы доступности в первом кластере  
 В первом WSFC создайте распределенную группу доступности (в этом примере она называется `distributedag`). Используйте команду **CREATE AVAILABILITY GROUP** с параметром **DISTRIBUTED** . Параметр **AVAILABILITY GROUP ON** указывает участвующие группы доступности, `ag1` и `ag2`.  
  
```tsql  
CREATE AVAILABILITY GROUP [distributedag]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO   
```  
  
> [!NOTE]  
>  **LISTENER_URL** указывает прослушиватель для каждой группы доступности, а также конечную точку зеркального отображения базы данных для группы доступности. В этом примере это порт `5022` (а не порт `60173`, который использовался для создания прослушивателя).  
  
### Присоединение распределенной группы доступности во втором кластере  
 Присоедините распределенную группу доступности во втором кластере WSFC.  
  
```tsql  
ALTER AVAILABILITY GROUP [distributedag]   
   JOIN   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO  
```  

  
## Отработка отказа с переходом на вторичную группу доступности  
 В настоящее время поддерживается только отработка отказа вручную. Следующая инструкция Transact-SQL вызывает отработку отказа с переходом к распределенной группе доступности с именем `distributedag`:  


1. Задайте режим доступности синхронной фиксации для дополнительной группы доступности. 
    
      ```tsql  
      ALTER AVAILABILITY GROUP [distributedag] 
      MODIFY 
      AVAILABILITY GROUP ON
      'ag1' WITH  
         ( 
          LISTENER_URL = 'tcp://ag1-listener:5022',  
          AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = MANUAL, 
          SEEDING_MODE = MANUAL 
          ), 
      'ag2' WITH  
        ( 
        LISTENER_URL = 'tcp://ag2-listener:5022', 
        AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
        FAILOVER_MODE = MANUAL, 
        SEEDING_MODE = MANUAL 
        );  
       
      ```  
  
1. Подождите, пока состояние распределенной группы доступности изменится на `SYNCHRONIZED`. Выполните следующий запрос в SQL Server, где размещена первичная реплика основной группы доступности. 
    
      ```tsql  
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

1. В SQL Server, где размещается первичная реплика основной группы доступности, задайте для роли распределенной группы доступности значение `SECONDARY`. 

      ```tsql
      ALTER AVAILABILITY GROUP distributedag SET (ROLE = SECONDARY); 
      ```  

    Примечание. На этом этапе распределенная группа доступности недоступна.

1. Проверьте готовность к отработке отказа. Выполните следующий запрос:

      ```tsql
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

1. Выполните отработку отказа из основной группы доступности в дополнительную. Запустите следующую команду в SQL Server, где размещена первичная реплика дополнительной группы доступности. 

      ```tsql
      ALTER AVAILABILITY GROUP distributedag FORCE_FAILOVER_ALLOW_DATA_LOSS; 
      ```  
      Примечание. На этом этапе распределенная группа доступности доступна.
      
После выполнения описанных выше шагов, распределенная группа доступности выполняет отработку отказа без потери данных. Корпорация Майкрософт рекомендует изменить режим доступности обратно на ASYNCHRONOUS_COMMIT, если группы доступности находятся на удаленном расстоянии друг от друга, что приводит к задержке. 
  
## Удаление распределенной группы доступности  
 Следующая инструкция Transact-SQL удаляет распределенную группу доступности с именем `distributedag`:  
  
```tsql  
DROP AVAILABILITY GROUP [distributedag]  
```  

## Создание распределенной группы доступности с экземплярами отказоустойчивого кластера

Вы можете создать распределенную группу доступности, используя группу доступности на экземпляре отказоустойчивого кластера (FCI). В этом случае прослушиватель группы доступности не требуется. Используйте имя виртуальной сети (VNN) для первичной реплики экземпляра отказоустойчивого кластера. В следующем примере показана распределенная группа доступности с именем SQLFCIDAG. Группа доступности SQLFCIAG имеет 2 реплики FCI. Имя виртуальной сети для первичной реплики FCI имеет значение SQLFCIAG-1, а для вторичной — SQLFCIAG-2. Распределенная группа доступности также включает в себя SQLAG-DR для аварийного восстановления.

![Распределенная группа доступности AlwaysOn](../../../database-engine/availability-groups/windows/media/always-on-availability-group-distributed.png)

 
 
 Следующая инструкция DDL создает эту распределенную группу доступности. 

```tsql  
CREATE AVAILABILITY GROUP [SQLFCIDAG]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
  'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-1:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      ),   
  'SQLAG-DR' WITH    
       (   
         LISTENER_URL = 'tcp://SQLAG-DR:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      );   
```  

Обратите внимание, что URL-адрес прослушивателя соответствует имени виртуальной сети первичного экземпляра отказоустойчивого кластера.

## Ручная отработка отказа отказоустойчивого кластера в распределенной группе доступности

Для выполнение ручной отработки отказа для группы доступности отказоустойчивого кластера обновите распределенную группу доступности в соответствии с измененным URL-адресом прослушивателя. Например, выполните следующую инструкцию DDL как в основной, так и в дополнительной группах доступности SQLFCIAG:

```tsql  
ALTER AVAILABILITY GROUP [SQLFCIDAG]  
   MODIFY AVAILABILITY GROUP ON  
 'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-2:5022'
    )
```  
  
## См. также:  
 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP (Transact-SQL)](../../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  