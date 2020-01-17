---
title: Использование RHEL FCI для SQL Server на Linux
description: Узнайте, как использовать экземпляр отказоустойчивого кластера общего диска Red Hat Enterprise Linux (RHEL) для SQL Server, чтобы обеспечить высокую доступность, например вручную отработать отказ отказоустойчивого кластера, и добавить или удалить узлы в кластере.
ms.custom: seo-lt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 075ab7d8-8b68-43f3-9303-bbdf00b54db1
ms.openlocfilehash: 76c59c6c7b821bfcc9eb76ca3a694a1c69095ce1
ms.sourcegitcommit: 035ad9197cb9799852ed705432740ad52e0a256d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/31/2019
ms.locfileid: "75558529"
---
# <a name="operate-rhel-failover-cluster-instance-fci-for-sql-server"></a>Работа экземпляра отказоустойчивого кластера RHEL для SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом документе описывается выполнение следующих задач для SQL Server в отказоустойчивом кластере общих дисков с Red Hat Enterprise Linux.

- Ручная отработка отказа кластера
- Мониторинг службы отказоустойчивого кластера SQL Server
- Добавление узла кластера
- Удаление узла кластера
- Изменение частоты мониторинга ресурсов SQL Server

## <a name="architecture-description"></a>Описание архитектуры

Уровень кластеризации основан на [надстройке высокого уровня доступности](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf) Red Hat Enterprise Linux (RHEL), созданной на базе [Pacemaker](https://clusterlabs.org/). Corosync и Pacemaker координируют обмен данными и управление ресурсами. Экземпляр SQL Server активен либо в одном, либо в другом узле.

На следующей схеме показаны компоненты кластера Linux с SQL Server. 

![Red Hat Enterprise Linux 7, общий диск, кластер SQL](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 

Дополнительные сведения о конфигурации кластера, параметрах агентов ресурсов и управлении см. в [справочной документации по RHEL](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html).

## <a name = "failManual"></a>Ручная отработка отказа кластера

Команда `resource move` создает ограничение, принудительно запуская ресурс на целевом узле.  После выполнения команды `move` ресурс `clear` удалит ограничение, чтобы можно было снова переместить ресурс или автоматически выполнить отработку отказа ресурса. 

```bash
sudo pcs resource move <sqlResourceName> <targetNodeName>  
sudo pcs resource clear <sqlResourceName> 
```

В следующем примере ресурс **mssqlha** перемещается на узел **sqlfcivm2**; затем ограничение удаляется, чтобы ресурс можно было переместить на другой узел позже.  

```bash
sudo pcs resource move mssqlha sqlfcivm2 
sudo pcs resource clear mssqlha 
```

## <a name="monitor-a-failover-cluster-sql-server-service"></a>Мониторинг службы отказоустойчивого кластера SQL Server

Просмотр текущего состояния кластера:

```bash
sudo pcs status  
```

Просмотр динамического состояния кластера и ресурсов:

```bash
sudo crm_mon 
```

Просмотрите журналы агента ресурсов в `/var/log/cluster/corosync.log`.

## <a name="add-a-node-to-a-cluster"></a>Добавление узла в кластер

1. Проверьте IP-адрес для каждого узла. Для отображения IP-адреса текущего узла выполните следующий сценарий. 

   ```bash
   ip addr show
   ```

3. Новому узлу нужно уникальное имя длиной не более 15 символов. По умолчанию в Red Hat Linux имя компьютера — `localhost.localdomain`. Это имя по умолчанию может не быть уникальным и имеет слишком большую длину. Задайте имя компьютера на новом узле. Задайте имя компьютера, добавив его к `/etc/hosts`. Следующий сценарий позволяет изменить `/etc/hosts` с помощью `vi`. 

   ```bash
   sudo vi /etc/hosts
   ```

   В следующем примере показан `/etc/hosts` с дополнениями для трех узлов `sqlfcivm1`, `sqlfcivm2` и `sqlfcivm3`.

   ```
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1         localhost localhost6 localhost6.localdomain6
   10.128.18.128 fcivm1
   10.128.16.77 fcivm2
   10.128.14.26 fcivm3
    ```
    
   Файл должен быть одинаковым на каждом узле. 

1. Остановите службу SQL Server на новом узле.

1. Следуйте инструкциям по подключению каталога файлов базы данных к общему расположению:

   На сервере NFS установите `nfs-utils`.

   ```bash
   sudo yum -y install nfs-utils 
   ``` 

   Откройте брандмауэр в клиентах и на сервере NFS: 

   ```bash
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

   Измените файл /etc/fstab, добавив команду mount: 

   ```bash
   <IP OF NFS SERVER>:<shared_storage_path> <database_files_directory_path> nfs timeo=14,intr
   ```

   Чтобы изменения вступили в силу, выполните команду `mount -a`.
   
1. На новом узле создайте файл для хранения имени пользователя и пароля SQL Server для входа с помощью Pacemaker. Следующая команда создает и заполняет такой файл:

   ```bash
   sudo touch /var/opt/mssql/passwd
   sudo echo "<loginName>" >> /var/opt/mssql/secrets/passwd
   sudo echo "<loginPassword>" >> /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/passwd
   sudo chmod 600 /var/opt/mssql/passwd
   ```

3. В брандмауэрах на новом узле откройте порты для Pacemaker. Чтобы открыть эти порты с помощью `firewalld`, выполните следующую команду:

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > [!NOTE]
   > Если вы используете другой брандмауэр, который не имеет встроенной конфигурации высокого уровня доступности, откройте следующие порты, чтобы Pacemaker мог связываться с другими узлами в кластере.
   >
   > * TCP: порты 2224, 3121, 21064
   > * UDP: порт 5405

1. Установите пакеты Pacemaker на новом узле.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```
 
2. Задайте пароль для пользователя по умолчанию, который создается при установке пакетов Pacemaker и Corosync. Используйте тот же пароль, что и для существующих узлов. 

   ```bash
   sudo passwd hacluster
   ```
 
3. Включите и запустите службу `pcsd` и Pacemaker. Это позволит новым узлам повторно подключаться к кластеру после перезагрузки. Выполните следующую команду на новом узле.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. Установите агент ресурсов отказоустойчивого кластера для SQL Server. Выполните следующую команду на новом узле. 

   ```bash
   sudo yum install mssql-server-ha
   ```

1. На существующем узле кластера выполните проверку подлинности нового узла и добавьте его в кластер:

    ```bash
    sudo pcs    cluster auth <nodeName3> -u hacluster 
    sudo pcs    cluster node add <nodeName3> 
    ```

    В следующем примере в кластер добавляется узел с именем **vm3**.

    ```bash
    sudo pcs    cluster auth  
    sudo pcs    cluster start 
    ```

## <a name="remove-nodes-from-a-cluster"></a>Удаление узлов из кластера

Чтобы удалить узел из кластера, выполните следующую команду:

```bash
sudo pcs    cluster node remove <nodeName>  
```

## <a name="change-the-frequency-of-sqlservr-resource-monitoring-interval"></a>Изменение частоты интервала мониторинга ресурсов sqlservr

```bash
sudo pcs    resource op monitor interval=<interval>s <sqlResourceName> 
```

В следующем примере интервал наблюдения для ресурса mssql устанавливается равным двум секундам:

```bash
sudo pcs    resource op monitor interval=2s mssqlha 
```
## <a name="troubleshoot-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>Устранение неполадок кластера общих дисков Red Hat Enterprise Linux для SQL Server

При устранении неполадок кластера может помочь понимание того, как все три управляющие программы работают вместе для управления ресурсами кластера. 

| Управляющая программа | Description 
| ----- | -----
| Corosync | Обеспечивает членство в кворуме и обмен сообщениями между узлами кластера.
| Pacemaker | Работает поверх Corosync и предоставляет конечные автоматы для ресурсов. 
| PCSD | Управляет Pacemaker и Corosync с помощью средств `pcs`

Для использования средств `pcs` необходимо запустить PCSD. 

### <a name="current-cluster-status"></a>Текущее состояние кластера 

`sudo pcs status` возвращает основные сведения о кластере, кворуме, узлах, ресурсах и состоянии управляющих программ для каждого узла. 

Ниже приведен пример вывода для работоспособного кворума Pacemaker.

```
Cluster name: MyAppSQL 
Last updated: Wed Oct 31 12:00:00 2016  Last change: Wed Oct 31 11:00:00 2016 by root via crm_resource on sqlvmnode1 
Stack: corosync 
Current DC: sqlvmnode1  (version 1.1.13-10.el7_2.4-44eb2dd) - partition with quorum 
3 nodes and 1 resource configured 

Online: [ sqlvmnode1 sqlvmnode2 sqlvmnode3] 

Full list of resources: 

mssqlha (ocf::sql:fci): Started sqlvmnode1 

PCSD Status: 
sqlvmnode1: Online 
sqlvmnode2: Online 
sqlvmnode3: Online 

Daemon Status: 
corosync: active/disabled 
pacemaker: active/enabled 
```

В этом примере `partition with quorum` означает, что большая часть узлов кворума находится в оперативном режиме. Если кластер теряет кворум большинства узлов, `pcs status` будет возвращать `partition WITHOUT quorum` и все ресурсы будут остановлены. 

`online: [sqlvmnode1 sqlvmnode2 sqlvmnode3]` возвращает имена всех узлов, которые сейчас участвуют в кластере. Если какие-то узлы не участвуют, `pcs status` возвращает `OFFLINE: [<nodename>]`.

`PCSD Status` показывает состояние кластера для каждого узла.

### <a name="reasons-why-a-node-may-be-offline"></a>Причины, по которым узел может находиться в автономном режиме

Если узел находится в автономном режиме, проверьте следующие элементы.

- **Брандмауэр**

    Чтобы Pacemaker мог обмениваться данными, на всех узлах должны быть открыты следующие порты.
    
    - **TCP: 2224, 3121, 21064

- **Службы Pacemaker или Corosync работают**

- **Связь между узлами**

- **Сопоставления имен узлов**

## <a name="additional-resources"></a>Дополнительные ресурсы

* Руководство [Кластер с нуля](https://clusterlabs.org/doc/Cluster_from_Scratch.pdf) от Pacemaker

## <a name="next-steps"></a>Дальнейшие действия

[Настройка общего кластера дисков Red Hat Enterprise Linux для SQL Server](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)

