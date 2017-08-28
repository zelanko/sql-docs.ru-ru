---
title: "Настройка группы доступности для SQL Server для Linux | Документы Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 06/14/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 6ceceaa00b2db22b5f1be9a6e8305da5b4cea49b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/28/2017

---
# <a name="configure-always-on-availability-group-for-sql-server-on-linux"></a>Настройка группы доступности AlwaysOn для SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

В этой статье описывается создание SQL Server всегда на группу доступности для обеспечения высокой доступности в Linux. Существует два типа конфигурации для группы доступности. Объект *высокий уровень доступности* конфигурации диспетчер кластера используется для обеспечения непрерывности бизнес-процессов. Эта конфигурация может также содержать реплики для чтения горизонтального масштабирования. В этом документе описывается создание конфигурации высокого уровня доступности группы доступности.

Можно также создать *чтения масштабирования* группы доступности без диспетчера кластеров. Эта конфигурация предоставляет для масштабирования производительности только реплик только для чтения. Он не обеспечивает высокий уровень доступности. Создание группы доступности чтения масштабируемого см [Настройка чтение группы доступности горизонтального масштабирования для SQL Server в Linux](sql-server-linux-availability-group-configure-rs.md).

Конфигурации, которые гарантируют высокий уровень доступности и защиты данных требуется два или три синхронной фиксации реплик. С трех синхронных реплик группы доступности возможность автоматически восстановления даже если один сервер недоступен. Дополнительные сведения см. в разделе [высокий уровень доступности и защиты данных в конфигурации группы доступности](sql-server-linux-availability-group-ha.md). 

Все серверы должны быть физическим или виртуальным и виртуальные серверы должны быть на одной платформе виртуализации. Это требование не так, как агенты разграничения относятся к конкретной платформе. В разделе [политики для гостевых кластеров](https://access.redhat.com/articles/29440#guest_policies).

## <a name="roadmap"></a>Стратегия

Инструкции по созданию группы доступности на серверах Linux для обеспечения высокой доступности, отличаются от действия, указанные на отказоустойчивом кластере Windows Server. Ниже приводятся шаги высокого уровня. 

1. [Настройка SQL Server на трех серверах кластера](sql-server-linux-setup.md).

   >[!IMPORTANT]
   >Всех трех серверов в группе доступности должны быть на одной и той же платформе — физический или виртуальный -, так как высокий уровень доступности Linux использует агенты разграничения для локализации ресурсов на серверах. Агенты разграничения характерные для каждой платформы.

2. Создайте группу доступности. Этот шаг, описанные в этой статье текущей. 

3. Настройте диспетчер ресурсов кластера, например Pacemaker.
   
   Способ настройки диспетчер ресурсов кластера зависит от конкретных дистрибутивах Linux. В разделе приведены ссылки на инструкции для распространения: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   * [SUSE](sql-server-linux-availability-group-cluster-sles.md)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   >[!IMPORTANT]
   >Рабочих средах требуется агент разграничения, например STONITH для обеспечения высокой доступности. Демонстрации в этой документации не используйте разграничения агентов. Для тестирования и проверки только являются демонстраций. 
   
   >Кластер Linux использует разграничения для возвращения известного состояния кластера. Способ настройки разграничения зависит от того, распределение и среды. В настоящее время разграничения недоступна в некоторых средах облака. Дополнительные сведения см. в разделе [политики поддержки для высокой доступности кластеров RHEL - платформ виртуализации](https://access.redhat.com/articles/29440).
   
   >SLES, в разделе [расширения высокого уровня доступности SUSE Linux Enterprise](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing).

5. Добавьте группы доступности в качестве ресурса кластера.  

   Способ добавления группы доступности в качестве ресурса кластера зависит от дистрибутив Linux. В разделе приведены ссылки на инструкции для распространения: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)
   * [SLES](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource)

[!INCLUDE [Create Prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-availability-group"></a>Создание группы доступности

Существует две конфигурации группы доступности поддерживается для SQL Server в Linux.

- [Три синхронных реплик](sql-server-linux-availability-group-ha.md#threeSynch)

- [Два синхронных реплик](sql-server-linux-availability-group-ha.md#twoSynch)

Сведения см. в разделе [высокий уровень доступности и защиты данных в конфигурации группы доступности](sql-server-linux-availability-group-ha.md).

Создание группы доступности для обеспечения высокой доступности в Linux. Используйте [создать ГРУППУ ДОСТУПНОСТИ](https://docs.microsoft.com/en-us/sql/t-sql/statements/create-availability-group-transact-sql) с `CLUSTER_TYPE = EXTERNAL`. 

* Группа доступности — `CLUSTER_TYPE = EXTERNAL` указывает, что сущность внешних кластер управляет группы доступности. Pacemaker является примером внешнего сущности. Если тип кластера группы доступности является внешним, 

* Задать первичная и Вторичная реплики `FAILOVER_MODE = EXTERNAL`. 
   Указывает, что реплика взаимодействует с Диспетчер внешних кластера, например Pacemaker. 

Следующие сценарии Transact-SQL создает группу доступности для обеспечения высокой доступности с именем `ag1`. Сценарий настраивает реплики группы доступности с `SEEDING_MODE = AUTOMATIC`. Этот параметр задан, то SQL Server для автоматического создания базы данных на каждом сервере-получателе. Обновите следующий сценарий для вашей среды. Замените `**<node1>**`, и `**<node2>**` значения с именами экземпляров SQL Server, на которых размещены реплики. Замените `**<5022>**` с портом, задать для конечной точки зеркального отображения данных. Чтобы создать группу доступности, запустите следующий запрос Transact-SQL на экземпляре SQL Server, на котором размещена первичная реплика.

Запустите **только один** из следующих сценариев: 

- Создание группы доступности с тремя синхронными репликами.

   ```Transact-SQL
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
   >После запуска предыдущий сценарий для создания группы доступности с тремя синхронные реплики не выполните следующий сценарий:

<a name="readScale"></a>

- Создание группы доступности с двумя синхронными репликами

   Включает две реплики в режиме доступности синхронной. Например, следующий скрипт создает группу доступности с именем `ag1`. `node1`и `node2` размещены реплики в синхронном режиме с автоматическим заполнением и автоматической отработки отказа.

   >[!IMPORTANT]
   >Только запустите следующий сценарий для создания группы доступности с двумя синхронными репликами. Не запускайте следующий скрипт, если вы запустили предыдущий сценарий. 

   ```Transact-SQL
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


Можно также настроить группы доступности с `CLUSTER_TYPE=EXTERNAL` с помощью SQL Server Management Studio или PowerShell. 

### <a name="join-secondary-replicas-to-the-availability-group"></a>Присоединение дополнительных реплик к группе доступности

Следующий сценарий Transact-SQL присоединяется к экземпляру SQL Server в группу доступности с именем `ag1`. Обновите скрипт для вашей среды. На каждом экземпляре SQL Server, на котором размещена вторичная реплика, запустите следующий код Transact-SQL для присоединения группы доступности.

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

>[!IMPORTANT]
>После создания группы доступности, необходимо настроить интеграцию с технологии кластера как Pacemaker для обеспечения высокой доступности. Для чтения конфигурации горизонтального масштабирования с использованием групп доступности, начиная с [!INCLUDE [версия SQL Server](..\includes\sssqlv14-md.md)], настройка кластера не требуется.

Если вы следовали инструкциям в этом документе, имеется группа доступности, которая еще не кластеризован. Следующим шагом является добавление в кластер. Эта конфигурация является допустимым для чтения сценариев балансировки-out нагрузка, не завершена, для обеспечения высокой доступности. Для обеспечения высокой доступности необходимо добавить группу доступности в качестве ресурса кластера. В разделе [дальнейшие действия](#next-steps) инструкции. 

## <a name="notes"></a>Примечания

>[!IMPORTANT]
>После настройки кластера и добавить группу доступности в качестве ресурса кластера, Transact-SQL нельзя использовать для отработки отказа ресурсов группы доступности. Ресурсы кластера SQL Server в Linux не связаны тесно как с операционной системой, как и на кластере отработки отказа Windows Server (WSFC). Службы SQL Server не имеет сведений о присутствии кластера. Все взаимодействие осуществляется с помощью средства управления кластером. В RHEL или Ubuntu использовать `pcs`. В SLES использовать `crm`. 

>[!IMPORTANT]
>Если ресурс кластера группы доступности, в текущем выпуске, где не поддерживает принудительную отработку отказа с потерей данных для реплики с асинхронной имеется известная проблема. Эта проблема будет устранена в будущей версии. Ручной или автоматический переход на синхронная реплика была выполнена успешно. 


## <a name="next-steps"></a>Следующие шаги

[Настройка Red Hat Enterprise Linux кластера для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Настройка SUSE Linux Enterprise Server кластера для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Настройка кластера Ubuntu для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)

