---
title: Настройка группы доступности для SQL Server на Linux
description: Сведения о настройке группы доступности Always On SQL Server для обеспечения высокой доступности в Linux.
author: MikeRayMSFT
ms.custom: seo-lt-2019
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 2e234e0057db852b6b741a0103412bbacd108287
ms.sourcegitcommit: 035ad9197cb9799852ed705432740ad52e0a256d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/31/2019
ms.locfileid: "75558404"
---
# <a name="configure-sql-server-always-on-availability-group-for-high-availability-on-linux"></a>Настройка группы доступности Always On SQL Server для обеспечения высокой доступности в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье содержатся сведения о настройке группы доступности (AG) Always On SQL Server для обеспечения высокой доступности в Linux. Существует два типа конфигурации групп доступности. В конфигурации *высокой доступности* используется диспетчер кластеров, обеспечивающий непрерывность бизнес-процессов. В эту конфигурацию также могут входить реплики для чтения и масштабирования. В этом документе описывается создание группы доступности для обеспечения высокой доступности.

Группу доступности для *чтения и масштабирования* можно создать без диспетчера кластеров. Такая группа предоставляет доступные только для чтения реплики в целях масштабирования производительности. Она не поддерживает высокий уровень доступности. Сведения о создании группы доступности для чтения и масштабирования см. в статье [Настройка группы доступности SQL Server для чтения и масштабирования в Linux](sql-server-linux-availability-group-configure-rs.md).

Конфигурации, гарантирующие высокую доступность и защиту данных, должны иметь две или три синхронные реплики фиксации. При наличии трех синхронных реплик группа доступности может выполнить автоматическое восстановление даже при недоступности одного сервера. Дополнительные сведения см. в статье [Высокий уровень доступности и защита данных для конфигураций группы доступности](sql-server-linux-availability-group-ha.md). 

Все серверы должны быть физическими или виртуальными. Виртуальные серверы должны находиться на одной платформе виртуализации. Это требование обусловлено тем, что агенты ограждения зависят от платформы. См. статью [Политики для гостевых кластеров](https://access.redhat.com/articles/29440#guest_policies).

## <a name="roadmap"></a>Схема действий

Действия по созданию группы доступности на серверах Linux для обеспечения высокой доступности отличаются от действий, выполняемых в отказоустойчивом кластере Windows Server. Ниже описывается общий порядок действий. 

1. [Настройте SQL Server на трех серверах кластера](sql-server-linux-setup.md).

   >[!IMPORTANT]
   >Все три сервера в группе доступности должны находиться на одной платформе (физической или виртуальной), так как для обеспечения высокой доступности в Linux используются агенты ограждения, позволяющие изолировать ресурсы на серверах. Агенты ограждения специфичны для каждой платформы.

2. Создайте группу доступности. Этот шаг рассматривается в этой статье. 

3. Настройте диспетчер ресурсов кластера, например Pacemaker.
   
   Способ настройки диспетчера ресурсов кластера зависит от конкретного дистрибутива Linux. Инструкции по работе с дистрибутивами см. по следующим ссылкам: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   * [SUSE](sql-server-linux-availability-group-cluster-sles.md)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   >[!IMPORTANT]
   >Для обеспечения высокого уровня доступности в рабочих средах требуется агент ограждения, например STONITH. В примерах в этой документации агенты ограждения не используются. Примеры приводятся только для тестирования и проверки. 
   
   >Кластер Linux использует ограждение для возврата кластера в известное состояние. Способ настройки ограждения зависит от дистрибутива и среды. Сейчас ограждение недоступно в некоторых облачных средах. Дополнительные сведения см. в статье о [политиках поддержки для кластеров RHEL с высоким уровнем доступности на платформах виртуализации](https://access.redhat.com/articles/29440).
   
   >Сведения о SLES см. в статье о [расширении для обеспечения высокой доступности SUSE Linux Enterprise](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing).

5. Добавьте группу доступности в качестве ресурса в кластер.  

   Способ добавления группы доступности в качестве ресурса в кластере зависит от дистрибутива Linux. Инструкции по работе с дистрибутивами см. по следующим ссылкам: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)
   * [SLES](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource)

[!INCLUDE [Create Prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>Создание группы доступности

В примерах этого раздела объясняется, как создать группу доступности с помощью Transact-SQL. Можно также использовать мастер создания групп доступности в SQL Server Management Studio. Если вы создаете группу доступности с помощью мастера, при присоединении реплик к группе будет возникать ошибка. Чтобы устранить эту проблему, предоставьте Pacemaker разрешения `ALTER`, `CONTROL` и `VIEW DEFINITIONS` в группе доступности на всех репликах. После предоставления разрешений на первичной реплике присоедините узлы к группе доступности с помощью мастера, но для правильного функционирования высокой доступности предоставьте разрешение на всех репликах.

В конфигурации высокой доступности, которая обеспечивает автоматический переход на другой ресурс, группа доступности должна иметь по крайней мере три реплики. Высокий уровень доступности поддерживается в любой из следующих конфигураций:

- [Три синхронные реплики](sql-server-linux-availability-group-ha.md#threeSynch)

- [две синхронные реплики и реплика конфигурации](sql-server-linux-availability-group-ha.md#twoSynch).

Дополнительные сведения см. в статье [Высокий уровень доступности и защита данных для конфигураций группы доступности](sql-server-linux-availability-group-ha.md).

>[!NOTE]
>Группы доступности могут содержать вторичные синхронные или асинхронные реплики. 

Создайте группу доступности для обеспечения высокой доступности в Linux. Используйте инструкцию [CREATE AVAILABILITY GROUP](https://docs.microsoft.com/sql/t-sql/statements/create-availability-group-transact-sql) с `CLUSTER_TYPE = EXTERNAL`. 

* Группа доступности — `CLUSTER_TYPE = EXTERNAL`. Указывает, что группой доступности управляет сущность внешнего кластера. Примером сущности внешнего кластера является Pacemaker. Если тип кластера группы доступности является внешним, 

* задайте для первичной и вторичной реплик `FAILOVER_MODE = EXTERNAL`. 
   Указывает, что реплика взаимодействует с диспетчером внешнего кластера, например Pacemaker. 

Следующие сценарии Transact-SQL используются для создания группы доступности `ag1` для обеспечения высокой доступности. Сценарий настраивает реплики группы доступности с параметром `SEEDING_MODE = AUTOMATIC`. Если этот параметр задан, SQL Server будет автоматически создавать базы данных на каждом сервере-получателе. Обновите следующий сценарий для своей среды. Замените значения `<node1>`, `<node2>` и `<node3>` на имена экземпляров SQL Server, где размещаются реплики. Замените значение `<5022>` на порт, заданный для конечной точки зеркального отображения данных. Чтобы создать группу доступности, выполните на экземпляре SQL Server, где размещена первичная реплика, следующий сценарий Transact-SQL:

Выполните **только один** из приведенных ниже сценариев. 

- [Создание группы доступности с тремя синхронными репликами](#threeSynch)
- [Создание группы доступности с двумя синхронными репликами и репликой конфигурации](#configOnly)
- [Создание группы доступности с тремя синхронными репликами](#readScale)

<a name="threeSynch"></a>

- Создание группы доступности с тремя синхронными репликами

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
   >После выполнения предыдущего сценария для создания группы доступности с тремя синхронными репликами не запускайте следующий сценарий:

<a name="configOnly"></a>
- Создание группы доступности с двумя синхронными репликами и репликой конфигурации

   >[!IMPORTANT]
   >Эта архитектура позволяет размещать третью реплику в любом выпуске SQL Server. Например, третью реплику можно разместить в выпуске SQL Server Express. В выпуске Express единственным допустимым типом конечной точки является `WITNESS`. 

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

- Создание группы доступности с тремя синхронными репликами

   Включите две реплики с синхронным режимом доступности. Например, следующий сценарий создает группу доступности `ag1`. Группы доступности `node1` и `node2` поддерживают размещение реплик в синхронном режиме с автоматическим заполнением и автоматическим переходом на другой ресурс.

   >[!IMPORTANT]
   >Для создания группы доступности с двумя синхронными репликами выполните только следующий сценарий. Не выполняйте следующий сценарий, если вы запускали любой из предыдущих. 

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


Кроме того, группу доступности с `CLUSTER_TYPE=EXTERNAL` можно настроить с помощью SQL Server Management Studio или PowerShell. 

### <a name="join-secondary-replicas-to-the-ag"></a>Присоединение вторичных реплик к группе доступности

Пользователю Pacemaker требуются разрешения `ALTER`, `CONTROL` и `VIEW DEFINITION` для группы доступности на всех репликах. Чтобы предоставить разрешения, выполните следующий сценарий Transact-SQL после создания группы доступности на первичной реплике и каждой вторичной реплики сразу после их добавления в группу доступности. Перед запуском сценария замените `<pacemakerLogin>` на имя учетной записи пользователя Pacemaker. Если у вас нет имени входа для Pacemaker, [создайте учетные данные SQL Server для Pacemaker](sql-server-linux-availability-group-cluster-ubuntu.md#create-a-sql-server-login-for-pacemaker).

```sql
GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::ag1 TO <pacemakerLogin>
GRANT VIEW SERVER STATE TO <pacemakerLogin>
```

Следующий сценарий Transact-SQL присоединяет экземпляр SQL Server к группе доступности `ag1`. Обновите сценарий для своей среды. На каждом экземпляре SQL Server, где размещена вторичная реплика, выполните следующий сценарий Transact-SQL для присоединения группы доступности.

```sql
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

>[!IMPORTANT]
>После создания группы доступности необходимо настроить интеграцию с кластерной технологией, такой как Pacemaker, для обеспечения высокой доступности. Начиная с [!INCLUDE [SQL Server version](../includes/sssqlv14-md.md)] в конфигурации для чтения и масштабирования настраивать кластер не требуется.

Если вы выполнили действия, описанные в этом документе, то в вашем распоряжении находится еще не кластеризованная группа доступности. Далее следует добавить кластер. Такая конфигурация допустима для сценариев чтения и масштабирования или балансировки нагрузки, но она является неполной для обеспечения высокой доступности. Для обеспечения высокой доступности необходимо добавить группу доступности в качестве ресурса кластера. Инструкции см. в разделе [Следующие шаги](#next-steps). 

## <a name="notes"></a>Примечания

>[!IMPORTANT]
>После настройки кластера и добавления группы доступности в качестве ресурса кластера вы не можете использовать Transact-SQL для отработки отказа ресурсов группы доступности. Ресурсы кластера SQL Server в Linux не так сильно зависят от операционной системы, как если бы они находились в отказоустойчивом кластере Windows Server (WSFC). Служба SQL Server не имеет сведений о наличии кластера. Вся оркестрация осуществляется с помощью средств управления кластерами. В RHEL или Ubuntu используйте `pcs`. В SLES используйте `crm`. 

>[!IMPORTANT]
>Если группа доступности является ресурсом кластера, в текущем выпуске существует известная ошибка, когда принудительный переход (с потерей данных) на асинхронную реплику не работает. Эта проблема будет устранена в следующем выпуске. Переход на синхронную реплику вручную или автоматически выполняется успешно.


## <a name="next-steps"></a>Дальнейшие действия

[Настройка кластера Red Hat Enterprise Linux для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Настройка кластера SUSE Linux Enterprise Server для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Настройка кластера Ubuntu для ресурсов кластера группы доступности SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)
