---
title: Работа кластера как общего Red Hat Enterprise Linux для SQL Server | Документация Майкрософт
description: Реализации высокого уровня доступности, настроив кластер общих дисков Red Hat Enterprise Linux для SQL Server.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 075ab7d8-8b68-43f3-9303-bbdf00b54db1
ms.openlocfilehash: 2967277ca109b9ee55221a7b12f5af891a5e45a2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62635590"
---
# <a name="operate-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>Работать кластер общих дисков Red Hat Enterprise Linux для SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом документе описывается, как выполнить следующие задачи для SQL Server на отказоустойчивый кластер общего диска с Red Hat Enterprise Linux.

- Вручную выполните отработку отказа кластера
- Мониторинг кластера отработки отказа службы SQL Server
- Добавить узел к кластеру
- Удалить узел кластера
- Изменение ресурса SQL Server, мониторинг частоты

## <a name="architecture-description"></a>Описание архитектуры

Кластеризации уровень основан на Red Hat Enterprise Linux (RHEL) [дополнение HA](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf) создаются на основе [Pacemaker](https://clusterlabs.org/). Corosync и Pacemaker координировать кластерной связи и управления ресурсами. Экземпляр SQL Server активен на одном узле или в другой.

На следующей схеме показана компонентов в кластере Linux с SQL Server. 

![Red Hat Enterprise Linux 7 кластер с общими дисками SQL](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 

Дополнительные сведения о конфигурации кластера, параметры агентов ресурсов и управления, см. в статье [RHEL справочная документация по](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html).

## <a name = "failManual"></a>Отказоустойчивый кластер вручную

`resource move` Команда создает ограничение, принудительно ресурсов для запуска на целевом узле.  После выполнения `move` команды, ресурс `clear` приведет к удалению ограничения, можно снова переместить ресурс или ресурс автоматически выполнить отработку отказа. 

```bash
sudo pcs resource move <sqlResourceName> <targetNodeName>  
sudo pcs resource clear <sqlResourceName> 
```

В следующем примере выполняется перемещение **mssqlha** ресурсов на узел с именем **sqlfcivm2**, а затем удаляется ограничение таким образом, чтобы позже ресурс можно переместить на другой узел.  

```bash
sudo pcs resource move mssqlha sqlfcivm2 
sudo pcs resource clear mssqlha 
```

## <a name="monitor-a-failover-cluster-sql-server-service"></a>Мониторинг кластера отработки отказа службы SQL Server

Просмотрите текущее состояние кластера:

```bash
sudo pcs status  
```

Просмотр динамической состояния кластера и ресурсы:

```bash
sudo crm_mon 
```

Просмотр журналов агента ресурсов по адресу `/var/log/cluster/corosync.log`

## <a name="add-a-node-to-a-cluster"></a>Добавление узла в кластер

1. Проверьте IP-адрес для каждого узла. Следующий скрипт показывает IP-адрес вашего текущего узла. 

   ```bash
   ip addr show
   ```

3. Новый узел должен уникальное имя, которое не более 15 символов или меньше. По умолчанию в Red Hat Linux — имя компьютера `localhost.localdomain`. Это имя по умолчанию могут не быть уникальными и слишком длинное. Задайте имя компьютера на новый узел. Задайте имя компьютера, добавив его `/etc/hosts`. Следующий сценарий позволяет изменить `/etc/hosts` с помощью `vi`. 

   ```bash
   sudo vi /etc/hosts
   ```

   В следующем примере показан `/etc/hosts` с дополнениями для трех узлов с именем `sqlfcivm1`, `sqlfcivm2`, и`sqlfcivm3`.

   ```
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1         localhost localhost6 localhost6.localdomain6
   10.128.18.128 fcivm1
   10.128.16.77 fcivm2
   10.128.14.26 fcivm3
    ```
    
   Файл должен быть одинаковым на каждом узле. 

1. Остановите службу SQL Server на новом узле.

1. Следуйте инструкциям для подключения к общей папке каталога файла базы данных:

   Начиная с NFS-сервер установить `nfs-utils`

   ```bash
   sudo yum -y install nfs-utils 
   ``` 

   Откройте брандмауэр на клиентах и NFS-сервера 

   ```bash
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

   Измените файл/etc/fstab, чтобы включить команду mount: 

   ```bash
   <IP OF NFS SERVER>:<shared_storage_path> <database_files_directory_path> nfs timeo=14,intr
   ```

   Запустите `mount -a` изменения вступили в силу.
   
1. На новом узле создайте файл для хранения SQL Server имя пользователя и пароль для входа Pacemaker. Следующая команда создает и заполняет такой файл:

   ```bash
   sudo touch /var/opt/mssql/passwd
   sudo echo "<loginName>" >> /var/opt/mssql/secrets/passwd
   sudo echo "<loginPassword>" >> /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/passwd
   sudo chmod 600 /var/opt/mssql/passwd
   ```

3. На новом узле откройте порты брандмауэра для Pacemaker. Чтобы открыть эти порты с помощью `firewalld`, выполните следующую команду:

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > [!NOTE]
   > Если вы используете другой брандмауэр, который не имеет встроенной конфигурации высокого уровня доступности, следующие порты должны быть открыты для Pacemaker иметь возможность связываться с другими узлами в кластере
   >
   > * TCP: Порты с кодом 2224, 3121, 21064.
   > * UDP: Порт 5405.

1. Установите пакеты Pacemaker на новом узле.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```
 
2. Задайте пароль для пользователя по умолчанию, который создается при установке пакетов Pacemaker и Corosync. Используйте тот же пароль, что и существующие узлы. 

   ```bash
   sudo passwd hacluster
   ```
 
3. Включите и запустите службу `pcsd` и Pacemaker. Таким образом, новый узел к кластеру после перезагрузки. Выполните следующую команду на новом узле.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. Установите агент ресурсов отказоустойчивого кластера для SQL Server. Выполните следующие команды на новом узле. 

   ```bash
   sudo yum install mssql-server-ha
   ```

1. На существующий узел из кластера проверку подлинности новый узел и добавьте его в кластер:

    ```bash
    sudo pcs    cluster auth <nodeName3> -u hacluster 
    sudo pcs    cluster node add <nodeName3> 
    ```

    В следующем примере добавляется узел с именем **vm3** в кластер.

    ```bash
    sudo pcs    cluster auth  
    sudo pcs    cluster start 
    ```

## <a name="remove-nodes-from-a-cluster"></a>Удаление узлов из кластера

Чтобы удалить узел из кластера, выполните следующую команду:

```bash
sudo pcs    cluster node remove <nodeName>  
```

## <a name="change-the-frequency-of-sqlservr-resource-monitoring-interval"></a>Изменение частоты интервал мониторинга ресурсов sqlservr

```bash
sudo pcs    resource op monitor interval=<interval>s <sqlResourceName> 
```

Следующий пример задает интервал мониторинга до 2 секунд для ресурса mssql:

```bash
sudo pcs    resource op monitor interval=2s mssqlha 
```
## <a name="troubleshoot-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>Устранение неполадок кластера общий диск Red Hat Enterprise Linux для SQL Server

При устранении неполадок кластера может помочь понять, как три управляющие программы работают вместе для управления ресурсами кластера. 

| Управляющая программа | Описание 
| ----- | -----
| Corosync | Предоставляет кворума членства и обмен сообщениями между узлами кластера.
| Pacemaker | Размещается поверх Corosync и предоставляет конечные автоматы для ресурсов. 
| PCSD | Управляет Pacemaker и Corosync через `pcs` средства

Для использования должен работать под управлением PCSD `pcs` средства. 

### <a name="current-cluster-status"></a>Текущее состояние кластера 

`sudo pcs status` Возвращает основные сведения о состоянии для каждого узла кластера, кворума, узлов, ресурсы и управляющей программы. 

Пример вывода Исправен pacemaker кворума будет следующим:

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

В примере `partition with quorum` означает, что кворума большинства узлов находится в сети. Если потери кворума большинства узлов, `pcs status` вернет `partition WITHOUT quorum` и все ресурсы будут остановлены. 

`online: [sqlvmnode1 sqlvmnode2 sqlvmnode3]` Возвращает имя всех узлов, в настоящее время участвует в кластере. Если все узлы не участвуют, `pcs status` возвращает `OFFLINE: [<nodename>]`.

`PCSD Status` Показывает состояние для каждого узла кластера.

### <a name="reasons-why-a-node-may-be-offline"></a>Причины, почему узел может быть отключен

Когда узел находится в автономном режиме, выполните следующие действия.

- **Брандмауэр**

    Следующие порты должны быть открыты на разных узлах для Pacemaker иметь возможность обмениваться данными.
    
    - **TCP: 2224, 3121, 21064

- **Pacemaker и Corosync службам**

- **Узел связи**

- **Сопоставления имен узлов**

## <a name="additional-resources"></a>Дополнительные ресурсы

* [Кластер с нуля](https://clusterlabs.org/doc/Cluster_from_Scratch.pdf) руководство из Pacemaker

## <a name="next-steps"></a>Следующие шаги

[Настройка кластера общий диск Red Hat Enterprise Linux для SQL Server](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)

