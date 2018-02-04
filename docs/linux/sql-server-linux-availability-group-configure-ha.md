---
title: "Настройка SQL Server группы доступности AlwaysOn для обеспечения высокой доступности в Linux | Документы Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 01/24/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 
ms.workload: On Demand
ms.openlocfilehash: b9aeae97abc2f60a9bb6c9c54f5061f68b61a1c9
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="configure-sql-server-always-on-availability-group-for-high-availability-on-linux"></a>Настройка SQL Server группы доступности AlwaysOn для обеспечения высокой доступности в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается создание SQL Server всегда в группе доступности (AG) для обеспечения высокой доступности в Linux. Существует два типа конфигурации для групп доступности. Объект *высокий уровень доступности* конфигурации диспетчер кластера используется для обеспечения непрерывности бизнес-процессов. Эта конфигурация может также включать шкалы чтения реплик. В этом документе описывается создание группы Доступности, для обеспечения высокой доступности.

Можно также создать группу Доступности без кластера диспетчера для *шкалы чтения*. Группе Доступности для чтения шкалы для масштабирования производительности предоставляет только реплик только для чтения. Он не обеспечивает высокий уровень доступности. Создание группы Доступности для чтения шкалы — [Настройка группы доступности SQL Server для чтения масштабирования на платформе Linux](sql-server-linux-availability-group-configure-rs.md).

Конфигурации, которые гарантируют высокий уровень доступности и защиты данных требуется два или три синхронной фиксации реплик. Три синхронные реплики группой Доступности может автоматически восстановление даже если один сервер недоступен. Дополнительные сведения см. в разделе [высокий уровень доступности и защиты данных в конфигурации групп доступности](sql-server-linux-availability-group-ha.md). 

Все серверы должны быть физическим или виртуальным и виртуальные серверы должны быть на одной платформе виртуализации. Это требование не так, как агенты разграничения относятся к конкретной платформе. В разделе [политики для гостевых кластеров](https://access.redhat.com/articles/29440#guest_policies).

## <a name="roadmap"></a>Стратегия

Инструкции по созданию группы Доступности на серверах Linux для обеспечения высокой доступности, отличаются от действия, указанные на отказоустойчивом кластере Windows Server. Ниже приводятся общие действия. 

1. [Настройка SQL Server на трех серверах кластера](sql-server-linux-setup.md).

   >[!IMPORTANT]
   >Всех трех серверов в группе Доступности должны быть на одной и той же платформе — физический или виртуальный -, так как высокий уровень доступности Linux использует агенты разграничения для локализации ресурсов на серверах. Агенты разграничения характерные для каждой платформы.

2. Создание группы Доступности. Этот шаг, описанные в этой статье текущей. 

3. Настройте диспетчер ресурсов кластера, например Pacemaker.
   
   Способ настройки диспетчер ресурсов кластера зависит от конкретных дистрибутивах Linux. В разделе приведены ссылки на инструкции для распространения: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   * [SUSE](sql-server-linux-availability-group-cluster-sles.md)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   >[!IMPORTANT]
   >Рабочих средах требуется агент разграничения, например STONITH для обеспечения высокой доступности. Демонстрации в этой документации не используйте разграничения агентов. Для тестирования и проверки только являются демонстраций. 
   
   >Кластер Linux использует разграничения для возвращения известного состояния кластера. Способ настройки разграничения зависит от того, распределение и среды. В настоящее время разграничения недоступна в некоторых средах облака. Дополнительные сведения см. в разделе [политики поддержки для высокой доступности кластеров RHEL - платформ виртуализации](https://access.redhat.com/articles/29440).
   
   >SLES, в разделе [расширения высокого уровня доступности SUSE Linux Enterprise](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing).

5. Добавьте группе Доступности в качестве ресурса кластера.  

   Способ добавления в группу Доступности в качестве ресурса кластера зависит от дистрибутив Linux. В разделе приведены ссылки на инструкции для распространения: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)
   * [SLES](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource)

[!INCLUDE [Create Prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>Создание группы Доступности

Для конфигураций высокой надежности, обеспечивающий автоматический переход на другой группе Доступности требуется по крайней мере три реплики. Одно из следующих конфигураций может поддерживать высокий уровень доступности:

- [Три синхронных реплик](sql-server-linux-availability-group-ha.md#threeSynch)

- [Два синхронных реплик, а также настройки реплики](sql-server-linux-availability-group-ha.md#twoSynch)

Сведения см. в разделе [высокий уровень доступности и защиты данных в конфигурации групп доступности](sql-server-linux-availability-group-ha.md).

>[!NOTE]
>Группы доступности может включать другие реплики синхронным или асинхронным. 

Создание группы Доступности, для обеспечения высокой доступности в Linux. Используйте [создать ГРУППУ ДОСТУПНОСТИ](https://docs.microsoft.com/en-us/sql/t-sql/statements/create-availability-group-transact-sql) с `CLUSTER_TYPE = EXTERNAL`. 

* Группа доступности — `CLUSTER_TYPE = EXTERNAL` указывает, что сущность внешних кластер управляет группой Доступности. Pacemaker является примером внешнего сущности. Если тип кластера группы Доступности — внешними, 

* Задать первичная и Вторичная реплики `FAILOVER_MODE = EXTERNAL`. 
   Указывает, что реплика взаимодействует с Диспетчер внешних кластера, например Pacemaker. 

Следующий сценарий Transact-SQL создает группе Доступности для обеспечения высокой доступности с именем `ag1`. Сценарий настраивает реплик группы Доступности с `SEEDING_MODE = AUTOMATIC`. Этот параметр задан, то SQL Server для автоматического создания базы данных на каждом сервере-получателе. Обновите следующий сценарий для вашей среды. Замените `**<node1>**`, `**<node2>**`, или `**<node3>**` значения с именами экземпляров SQL Server, на которых размещены реплики. Замените `**<5022>**` с портом, задать для конечной точки зеркального отображения данных. Чтобы создать группы Доступности, выполните следующий запрос Transact-SQL на экземпляре SQL Server, на котором размещена первичная реплика.

Запустите **только один** из следующих сценариев: 

- [Создание группы доступности с тремя синхронными репликами](#threeSynch).
- [Создание группы доступности с двумя синхронными репликами и конфигурации реплики](#configOnly)
- [Создание группы доступности с двумя синхронными репликами](#readScale).

<a name="threeSynch"></a>

- Создание группы Доступности с тремя синхронных реплик

   ```SQL
   CREATE AVAILABILITY GROUP [ag1]
       WITH (DB_FAILOVER = ON, CLUSTER_TYPE = EXTERNAL)
       FOR REPLICA ON
           N'**<node1>**' 
            WITH (
               ENDPOINT_URL = N'tcp://**<node1>:**<5022>**',
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'**<node2>**' 
            WITH ( 
               ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**', 
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'**<node3>**'
           WITH( 
              ENDPOINT_URL = N'tcp://**<node3>**:**<5022>**', 
              AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
              FAILOVER_MODE = EXTERNAL,
              SEEDING_MODE = AUTOMATIC
              );
        
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```

   >[!IMPORTANT]
   >После запуска предыдущий сценарий для создания группы Доступности с тремя синхронные реплики не выполните следующий сценарий:

- Создание группы Доступности с двумя синхронными репликами и реплики конфигурации:

   >[!IMPORTANT]
   >Такая архитектура позволяет любого выпуска SQL Server для размещения третья реплика. Например третья реплика может размещаться на SQL Server Enterprise Edition. В выпуске Enterprise Edition является тип конечной точки только допустимые `WITNESS`. 

   ```SQL
   CREATE AVAILABILITY GROUP [ag1] 
      WITH (CLUSTER_TYPE = EXTERNAL) 
      FOR REPLICA ON 
       N'**<node1>**' WITH ( 
          ENDPOINT_URL = N'tcp://**<node1>**:**<5022>**', 
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = EXTERNAL, 
          SEEDING_MODE = AUTOMATIC 
          ), 
       N'**<node2>**' WITH (  
          ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**',  
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = EXTERNAL, 
          SEEDING_MODE = AUTOMATIC 
          ), 
       N'**<node3>**' WITH ( 
          ENDPOINT_URL = N'tcp://**<node3>**:**<5022>**', 
          AVAILABILITY_MODE = CONFIGURATION_ONLY  
          );
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```
<a name="readScale"></a>

- Создание группы Доступности с двумя синхронными репликами

   Включает две реплики в режиме доступности синхронной. Например, следующий скрипт создает группы Доступности с именем `ag1`. `node1`и `node2` размещены реплики в синхронном режиме с автоматическим заполнением и автоматической отработки отказа.

   >[!IMPORTANT]
   >Только запустите следующий сценарий для создания группы Доступности с двумя синхронными репликами. Не запускайте следующий скрипт, если вы запустили либо предыдущий сценарий. 

   ```SQL
   CREATE AVAILABILITY GROUP [ag1]
      WITH (CLUSTER_TYPE = EXTERNAL)
      FOR REPLICA ON
      N'node1' WITH (
         ENDPOINT_URL = N'tcp://node1:5022',
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
         FAILOVER_MODE = EXTERNAL,
         SEEDING_MODE = AUTOMATIC
      ),
      N'node2' WITH ( 
         ENDPOINT_URL = N'tcp://node2:5022', 
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
         FAILOVER_MODE = EXTERNAL,
         SEEDING_MODE = AUTOMATIC
      );
        
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```


Можно также настроить группы Доступности с `CLUSTER_TYPE=EXTERNAL` с помощью SQL Server Management Studio или PowerShell. 

### <a name="join-secondary-replicas-to-the-ag"></a>Присоединение дополнительных реплик к группе Доступности

Следующий сценарий Transact-SQL присоединяет экземпляр SQL Server к группе Доступности с именем `ag1`. Обновите скрипт для вашей среды. На каждом экземпляре SQL Server, на котором размещена вторичная реплика запустите следующий скрипт Transact SQL для присоединения группы Доступности.

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

>[!IMPORTANT]
>После создания группы Доступности, необходимо настроить интеграцию с технологии кластера как Pacemaker для обеспечения высокой доступности. Для масштабирования чтения конфигурации, с помощью групп доступности, начиная с [!INCLUDE [SQL Server version](..\includes\sssqlv14-md.md)], настройка кластера не требуется.

Если вы следовали инструкциям в этом документе, у вас есть группе Доступности, еще не кластеризован. Следующим шагом является добавление в кластер. Данная конфигурация недоступна для чтения нагрузка балансировки сценариев, не завершена, для обеспечения высокой доступности. Для обеспечения высокой доступности необходимо добавить в группу Доступности в качестве ресурса кластера. В разделе [дальнейшие действия](#next-steps) инструкции. 

## <a name="notes"></a>Примечания

>[!IMPORTANT]
>После настройки кластера и добавить группы Доступности в качестве ресурса кластера, Transact-SQL нельзя использовать для отработки отказа группы Доступности ресурсов. Ресурсы кластера SQL Server в Linux не связаны тесно как с операционной системой, как и на кластере отработки отказа Windows Server (WSFC). Службы SQL Server не имеет сведений о присутствии кластера. Все взаимодействие осуществляется с помощью средства управления кластером. В RHEL или Ubuntu использовать `pcs`. В SLES использовать `crm`. 

>[!IMPORTANT]
>Если ресурс кластера группы Доступности, в текущем выпуске, где не поддерживает принудительную отработку отказа с потерей данных для реплики с асинхронной имеется известная проблема. Эта проблема будет устранена в будущей версии. Ручной или автоматический переход на синхронная реплика была выполнена успешно. 


## <a name="next-steps"></a>Следующие шаги

[Настройка Red Hat Enterprise Linux кластера для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Настройка SUSE Linux Enterprise Server кластера для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Настройка кластера Ubuntu для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)
