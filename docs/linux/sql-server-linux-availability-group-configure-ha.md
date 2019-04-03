---
title: Настройка SQL Server группы доступности AlwaysOn для обеспечения высокой доступности в Linux
titleSuffix: SQL Server
description: Сведения о создании SQL Server всегда в группе доступности (AG) для обеспечения высокой доступности в Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 02/14/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux, seodec18
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 95e9ae2bd77bc3042a44b0322ac9a607be3725e8
ms.sourcegitcommit: 1a4aa8d2bdebeb3be911406fc19dfb6085d30b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2019
ms.locfileid: "58872204"
---
# <a name="configure-sql-server-always-on-availability-group-for-high-availability-on-linux"></a>Настройка SQL Server группы доступности AlwaysOn для обеспечения высокой доступности в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается создание SQL Server всегда в группе доступности (AG) для обеспечения высокой доступности в Linux. Существует два типа конфигурации для групп доступности. Объект *высокий уровень доступности* конфигурации использует диспетчер кластеров для обеспечения непрерывности бизнес-процессов. Эта конфигурация может также включать реплик для чтения и масштабирования. В этом документе описывается создание группы Доступности для обеспечения высокой доступности.

Можно также создать группу Доступности без кластера диспетчер для *чтения и масштабирования*. Группы Доступности для масштаба чтения предоставляет только реплик только для чтения для горизонтального масштабирования производительности. Она предоставляет высокий уровень доступности. Чтобы создать группу Доступности для чтения и масштабирования, см. в разделе [Настройка группы доступности SQL Server для чтения и масштабирования в Linux](sql-server-linux-availability-group-configure-rs.md).

Конфигурации, которые гарантируют высокий уровень доступности и защиты данных требуется два или три синхронной фиксации реплик. С тремя синхронными репликами группы Доступности можно автоматически восстановить даже если один сервер недоступен. Дополнительные сведения см. в разделе [высокий уровень доступности и защиты данных в конфигурации групп доступности](sql-server-linux-availability-group-ha.md). 

Все серверы должны быть физическим или виртуальным, и виртуальные серверы должны находиться в одной платформе виртуализации. Это требование обусловлено агентов ограждения относятся к конкретной платформе. См. в разделе [политики для гостевых кластеров](https://access.redhat.com/articles/29440#guest_policies).

## <a name="roadmap"></a>Стратегия развития

Шаги по созданию группы Доступности на серверах Linux для обеспечения высокой доступности, отличаются от действия, указанные на отказоустойчивый кластер Windows Server. Ниже перечислены основные действия. 

1. [Настройка SQL Server на трех серверах кластера](sql-server-linux-setup.md).

   >[!IMPORTANT]
   >Всех трех серверов в группе Доступности должны быть на одной и той же платформе — физический или виртуальный -, так как высокий уровень доступности Linux использует ограждения агенты изолировать ресурсы на серверах. Агентов ограждения характерные для каждой платформы.

2. Создайте группу доступности. Этот шаг описан в этой статье текущей. 

3. Настройте диспетчер кластерных ресурсов, таких как Pacemaker.
   
   Способ настройки диспетчер ресурсов кластера зависит от конкретного дистрибутива Linux. См. в разделе приведены ссылки на конкретные инструкции для распространения: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   * [SUSE](sql-server-linux-availability-group-cluster-sles.md)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   >[!IMPORTANT]
   >Рабочих средах требуется агент ограждения, например STONITH для обеспечения высокой доступности. Демонстрации в данной документации не имеют агентов ограждения. Демонстрации предназначены для тестирования и проверки только. 
   
   >Кластер Linux использует ограждения для возврата кластера в известное состояние. Способ настройки ограждения зависит от распределения и среды. В настоящее время ограждения недоступна в некоторых облачных средах. Дополнительные сведения см. в разделе [политики поддержки для высокой доступности кластеров RHEL - платформ виртуализации](https://access.redhat.com/articles/29440).
   
   >SLES, см. в разделе [расширение высокого уровня доступности SUSE Linux Enterprise](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing).

5. Добавьте группы Доступности в качестве ресурса кластера.  

   Способ добавить в группу Доступности в качестве ресурса кластера зависит от дистрибутива Linux. См. в разделе приведены ссылки на конкретные инструкции для распространения: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)
   * [SLES](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource)

[!INCLUDE [Create Prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>Создание группы доступности

Примеры в этом разделе объясняется, как создать группу доступности с помощью Transact-SQL. Можно также использовать мастер группы доступности SQL Server Management Studio. При создании группы Доступности с помощью мастера, он возвращает ошибку при присоединении реплики к группе Доступности. Чтобы устранить эту проблему, предоставьте `ALTER`, `CONTROL`, и `VIEW DEFINITIONS` для pacemaker на всех репликах группы Доступности. После разрешения предоставляются на первичную реплику, присоедините узлы к группе Доступности в мастере, но для обеспечения высокой ДОСТУПНОСТИ для правильной, предоставьте разрешение на всех репликах.

Для конфигурации высокого уровня доступности, которая обеспечивает автоматическую отработку отказа группы Доступности требуется по крайней мере три реплики. Одно из следующих конфигураций может поддерживать высокий уровень доступности:

- [Три синхронные реплики](sql-server-linux-availability-group-ha.md#threeSynch)

- [Два синхронных реплик, а также конфигурации реплики](sql-server-linux-availability-group-ha.md#twoSynch)

Сведения см. в разделе [высокий уровень доступности и защиты данных в конфигурации групп доступности](sql-server-linux-availability-group-ha.md).

>[!NOTE]
>Группы доступности может включать дополнительные реплики синхронной или асинхронной. 

Создание группы Доступности для обеспечения высокой доступности на платформе Linux. Используйте [CREATE AVAILABILITY GROUP](https://docs.microsoft.com/sql/t-sql/statements/create-availability-group-transact-sql) с `CLUSTER_TYPE = EXTERNAL`. 

* Группа доступности — `CLUSTER_TYPE = EXTERNAL` указывает, что сущность внешнего управляет группой Доступности. Pacemaker является примером внешнего сущности. Если тип кластера группы Доступности — внешними, 

* Задайте первичная и Вторичная реплики `FAILOVER_MODE = EXTERNAL`. 
   Указывает, что реплика взаимодействует с диспетчером внешних кластеров, таких как Pacemaker. 

Следующий сценарий Transact-SQL создает группу Доступности для обеспечения высокой доступности с именем `ag1`. Сценарий настраивает реплики группы доступности с параметром `SEEDING_MODE = AUTOMATIC`. Этот параметр задан, то SQL Server для автоматического создания базы данных на каждом сервере-получателе. Обновите следующий сценарий для своей среды. Замените `<node1>`, `<node2>`, или `<node3>` значения с именами экземпляров SQL Server, на которых размещены реплики. Замените `<5022>` с портом, задайте для конечной точки зеркального отображения данных. Чтобы создать группу Доступности, выполните следующий запрос Transact-SQL на экземпляре SQL Server, на котором размещена первичная реплика.

Запустите **только один** из следующих сценариев: 

- [Создание группы доступности с тремя синхронными репликами](#threeSynch).
- [Создание группы доступности с двумя репликами синхронной и конфигурации реплики](#configOnly)
- [Создание группы доступности с двумя синхронными репликами](#readScale).

<a name="threeSynch"></a>

- Создание группы Доступности с помощью трех синхронных реплик

   ```SQL
   CREATE AVAILABILITY GROUP [ag1]
       WITH (DB_FAILOVER = ON, CLUSTER_TYPE = EXTERNAL)
       FOR REPLICA ON
           N'<node1>' 
            WITH (
               ENDPOINT_URL = N'tcp://<node1>:<5022>',
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'<node2>' 
            WITH ( 
               ENDPOINT_URL = N'tcp://<node2>:<5022>', 
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'<node3>'
           WITH( 
              ENDPOINT_URL = N'tcp://<node3>:<5022>', 
              AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
              FAILOVER_MODE = EXTERNAL,
              SEEDING_MODE = AUTOMATIC
              );
        
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```

   >[!IMPORTANT]
   >После того, как приведенный выше сценарий, чтобы создать группу Доступности с тремя синхронными репликами не выполните следующий сценарий:

<a name="configOnly"></a>
- Создание группы Доступности с двумя репликами синхронной и конфигурации реплики:

   >[!IMPORTANT]
   >Эта архитектура позволяет любого выпуска SQL Server для размещения третья реплика. Например третья реплика может размещаться на SQL Server Enterprise Edition. В выпуске Enterprise Edition — тип конечной точки только допустимые `WITNESS`. 

   ```SQL
   CREATE AVAILABILITY GROUP [ag1] 
      WITH (CLUSTER_TYPE = EXTERNAL) 
      FOR REPLICA ON 
       N'<node1>' WITH ( 
          ENDPOINT_URL = N'tcp://<node1>:<5022>', 
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = EXTERNAL, 
          SEEDING_MODE = AUTOMATIC 
          ), 
       N'<node2>' WITH (  
          ENDPOINT_URL = N'tcp://<node2>:<5022>',  
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = EXTERNAL, 
          SEEDING_MODE = AUTOMATIC 
          ), 
       N'<node3>' WITH ( 
          ENDPOINT_URL = N'tcp://<node3>:<5022>', 
          AVAILABILITY_MODE = CONFIGURATION_ONLY  
          );
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```
<a name="readScale"></a>

- Создание группы Доступности с помощью двух синхронных реплик

   Включать две реплики с режимом синхронной доступности. Например, следующий скрипт создает группу Доступности с именем `ag1`. `node1` и `node2` размещены реплики в синхронном режиме, с помощью автоматического заполнения и автоматической отработки отказа.

   >[!IMPORTANT]
   >Только запустите следующий скрипт, чтобы создать группу Доступности с двумя синхронными репликами. Не запустите следующий сценарий, если вы выполнили либо предыдущий сценарий. 

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


Вы также можете настроить группу Доступности с `CLUSTER_TYPE=EXTERNAL` с помощью SQL Server Management Studio или PowerShell. 

### <a name="join-secondary-replicas-to-the-ag"></a>Присоединение дополнительных реплик к группе Доступности

Требуется pacemaker `ALTER`, `CONTROL`, и `VIEW DEFINITION` разрешений на группу доступности на всех репликах. Чтобы предоставить разрешения, выполните следующий сценарий Transact-SQL, после создания группы доступности на первичной и вторичной реплике сразу же после добавления к группе доступности. Перед выполнением скрипта замените `<pacemakerLogin>` с именем учетной записи пользователя pacemaker.

```Transact-SQL
GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::ag1 TO <pacemakerLogin>
GRANT VIEW SERVER STATE TO <pacemakerLogin>
```

Следующий сценарий Transact-SQL присоединяется к экземпляру SQL Server в группу доступности с именем `ag1`. Обновите сценарий для своей среды. На каждом экземпляре SQL Server, на котором размещена вторичная реплика запустите следующий код Transact-SQL для присоединения к группе Доступности.

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

>[!IMPORTANT]
>После создания группы Доступности, необходимо настроить интеграцию с технологией кластера как Pacemaker для обеспечения высокой доступности. Для чтения и масштабирования конфигурации с помощью групп доступности, начиная с [!INCLUDE [SQL Server version](../includes/sssqlv14-md.md)], настройку кластера не требуется.

Если вы выполнили действия, описанные в этом документе, у вас есть группа Доступности, еще не кластеризован. Следующим шагом является добавление в кластер. Эта конфигурация является допустимым для чтения scale/load балансировки сценариев, не завершена для обеспечения высокой доступности. Для обеспечения высокой доступности необходимо добавить в группу Доступности в качестве ресурса кластера. См. в разделе [дальнейшие действия](#next-steps) инструкции. 

## <a name="notes"></a>Примечания

>[!IMPORTANT]
>После настройки кластера и добавить группу Доступности в качестве ресурса кластера, Transact-SQL нельзя использовать для отработки отказа группы Доступности ресурсов. Ресурсы кластера SQL Server в Linux не связаны тесно как с операционной системой, как они находятся на кластер отработки отказа Windows Server (WSFC). Службы SQL Server не учитывает наличие кластера. Все согласование осуществляется с помощью средства управления кластером. В RHEL или Ubuntu используйте `pcs`. В SLES использовать `crm`. 

>[!IMPORTANT]
>Если ресурс кластера группы Доступности, в текущем выпуске, где не работает Принудительная отработка отказа с потерей данных асинхронную реплику имеется известная проблема. Это будет исправлено в будущем выпуске. Отработка отказа вручную или автоматически для синхронной реплики завершается успешно.


## <a name="next-steps"></a>Следующие шаги

[Настройка кластера Red Hat Enterprise Linux, для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Настройка кластера серверов SUSE Linux Enterprise для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Настройка кластера Ubuntu для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)
