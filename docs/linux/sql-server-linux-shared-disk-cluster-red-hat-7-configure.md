---
title: Настройка кластера как общего Red Hat Enterprise Linux для SQL Server | Документация Майкрософт
description: Реализации высокого уровня доступности, настроив кластер общих дисков Red Hat Enterprise Linux для SQL Server.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: dcc0a8d3-9d25-4208-8507-a5e65d2a9a15
ms.openlocfilehash: 1801551b179cf7040f1eb5cbaa05d8eb3bebc564
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62634021"
---
# <a name="configure-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>Настройка кластера общий диск Red Hat Enterprise Linux для SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Это руководство содержит инструкции по созданию двухузлового общего диска кластера для SQL Server в Red Hat Enterprise Linux. Кластеризации уровень основан на Red Hat Enterprise Linux (RHEL) [дополнение HA](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf) создаются на основе [Pacemaker](https://clusterlabs.org/). Экземпляр SQL Server активен на одном узле или в другой.

> [!NOTE] 
> Доступ к Red Hat высокого уровня ДОСТУПНОСТИ надстройки и документацию требуется подписка. 

На следующей схеме показано, хранения показано на двух серверах. Кластеризации компонентов - Corosync и Pacemaker - координату связи и управления ресурсами. Один из серверов имеет активное подключение к ресурсам хранилища и SQL Server. Когда Pacemaker обнаруживает сбой кластеризации компоненты управления перемещения ресурсов на другой узел.  

![Red Hat Enterprise Linux 7 кластер с общими дисками SQL](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 

Дополнительные сведения о конфигурации кластера, параметры агентов ресурсов и управления, см. в статье [RHEL справочная документация по](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html).


> [!NOTE] 
> На этом этапе интеграции SQL Server с помощью Pacemaker не, а также как WSFC в Windows. Из в SQL, есть нет сведений о наличии кластера, все оркестрации выходит в и служба определяется как отдельный экземпляр Pacemaker. Также для этого кластера sys.dm_os_cluster_nodes динамические административные представления и sys.dm_os_cluster_properties будет ни одной записи.
Чтобы использовать строку подключения, указывающую на имя сервера строку и не используйте IP-адрес, их нужно зарегистрировать в их DNS-сервера IP-адрес, используемый для создания виртуальный IP-адрес (как описано в следующих разделах) с именем выбранного сервера.

Следующие разделы содержат описано, как можно настроить решение отказоустойчивого кластера. 

## <a name="prerequisites"></a>предварительные требования

Чтобы выполнить следующий сценарий end-to-end, вам понадобятся две машины, чтобы развернуть два узла кластера и другой сервер, чтобы настроить NFS-сервер. Следующие действия описывают настройку этих серверов.

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>Установка и настройка операционной системы на каждом узле кластера

Первым шагом является настройка операционной системы на узлах кластера. Для в этом пошаговом руководстве используйте RHEL с действительной подпиской для надстройки высокого уровня ДОСТУПНОСТИ. 

## <a name="install-and-configure-sql-server-on-each-cluster-node"></a>Установка и настройка SQL Server на каждом узле кластера

1. Установка и настройка SQL Server на обоих узлах.  Подробные инструкции см. в разделе [Установка SQL Server в Linux](sql-server-linux-setup.md).

1. Назначить один узел в качестве основного, а другой — как дополнительный для целей конфигурации. Использовать эти термины для следующих в этом руководстве.  

1. На вторичном узле остановка и отключение SQL Server.

   В следующем примере останавливается и отключает SQL Server: 

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl disable mssql-server
   ```
> [!NOTE] 
> Во время установки экземпляра SQL Server и поместить в главный ключ сервера `/var/opt/mssql/secrets/machine-key`. В Linux SQL Server всегда выполняется как локальная учетная запись называется mssql. Так как это локальной учетной записи удостоверения нет общего доступа между узлами. Таким образом необходимо скопировать ключ шифрования из основного узла на каждый дополнительный узел, поэтому каждая учетная запись локального mssql можно получить доступ к его для расшифровки главного ключа сервера. 

1. На основном узле, создайте имя входа SQL server для Pacemaker и предоставить имени входа разрешение на запуск `sp_server_diagnostics`. Pacemaker использует эту учетную запись, чтобы проверить, какой узел работает под управлением SQL Server. 

   ```bash
   sudo systemctl start mssql-server
   ```

   Подключение к SQL Server `master` базы данных с помощью учетной записи sa и выполните следующую команду:

   ```bashsql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'

   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```
   Вы также можете задать разрешения на более детальном уровне. Требует входа с помощью Pacemaker `VIEW SERVER STATE` запросить состояние работоспособности с sp_server_diagnostics, `setupadmin` и `ALTER ANY LINKED SERVER` обновить имя экземпляра отказоустойчивого Кластера с именем ресурса, запустив sp_dropserver и sp_addserver. 

1. На основном узле остановка и отключение SQL Server. 

1. Настройка файла hosts для каждого узла кластера. Файл узлов должна содержать IP-адрес и имя каждого узла кластера. 

    Проверьте IP-адрес для каждого узла. Следующий скрипт показывает IP-адрес вашего текущего узла. 

   ```bash
   sudo ip addr show
   ```

   Задайте имя компьютера, на каждом узле. Присвойте каждому узлу уникальное имя, которое не более 15 символов или меньше. Задайте имя компьютера, добавив его `/etc/hosts`. Следующий сценарий позволяет изменить `/etc/hosts` с помощью `vi`. 

   ```bash
   sudo vi /etc/hosts
   ```
   В следующем примере показан `/etc/hosts` с дополнениями для двух узлов с именем `sqlfcivm1` и `sqlfcivm2`.

   ```bash
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.128 sqlfcivm1
   10.128.16.77 sqlfcivm2
   ```

В следующем разделе будет настройки общего хранилища и перемещение файлов базы данных в хранилище. 

## <a name="configure-shared-storage-and-move-database-files"></a>Настройка общего хранилища и перемещение файлов базы данных 

Существует множество решений для предоставления общего хранилища. В этом пошаговом руководстве демонстрируется настройка общего хранилища с помощью NFS. Мы рекомендуем следовать рекомендации и использовать Kerberos для защиты NFS (можно найти здесь пример: https://www.certdepot.net/rhel7-use-kerberos-control-access-nfs-network-shares/). 

>[!Warning]
>Если не защитить NFS, всем, кто может получить доступ к сети и подмены IP-адрес узла SQL будет возможность доступа к файлам данных. Как всегда убедитесь, что вы угроз модели системы перед его использованием в рабочей среде. Другой вариант хранения — использовать общую папку SMB.

### <a name="configure-shared-storage-with-nfs"></a>Настройка общего хранилища с помощью NFS

> [!IMPORTANT] 
> Размещение файлов базы данных на NFS-сервер с версией < 4 не поддерживается в этом выпуске. Это подразумевает использование NFS для общего диска отказоустойчивой кластеризации, а также баз данных на некластеризованные экземпляры. Мы работаем над реализацией других версий сервера NFS в будущих выпусках. 

NFS-сервера выполните следующие действия.

1. Установка `nfs-utils`

   ```bash
   sudo yum -y install nfs-utils
   ```

1. Включение и запуск `rpcbind`

   ```bash
   sudo systemctl enable rpcbind && sudo systemctl start rpcbind
   ```

1. Включение и запуск `nfs-server`
 
   ```bash
   sudo systemctl enable nfs-server && sudo systemctl start nfs-server
   ```
 
1.  Изменить `/etc/exports` для экспорта в каталог, нужно предоставить общий доступ. Вам нужна 1 строка для каждой общей папки, которые нужно. Пример: 

   ```bash
   /mnt/nfs  10.8.8.0/24(rw,sync,no_subtree_check,no_root_squash)
   ```

1. Экспорт общих ресурсов

   ```bash
   sudo exportfs -rav
   ```

1. Убедитесь, что пути совместно или экспортировать, запустите на сервере для NFS

   ```bash
   sudo showmount -e
   ```

1. Добавить исключение в SELinux

   ```bash
   sudo setsebool -P nfs_export_all_rw 1
   ```
   
1. Откройте брандмауэр сервера.

   ```bash 
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

### <a name="configure-all-cluster-nodes-to-connect-to-the-nfs-shared-storage"></a>Настройки всех узлов кластера для подключения к хранилищу общих NFS

Выполните следующие действия на всех узлах кластера.

1.  Установка `nfs-utils`

   ```bash
   sudo yum -y install nfs-utils
   ```

1. Откройте брандмауэр на клиентах и NFS-сервера

   ```bash
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

1. Убедитесь, что вы видите общих ресурсов NFS на клиентских компьютерах

   ```bash
   sudo showmount -e <IP OF NFS SERVER>
   ```

1. Повторите эти шаги на всех узлах кластера.

Дополнительные сведения об использовании NFS см. следующие ресурсы:

* [NFS серверов и firewalld | Stack Exchange](https://unix.stackexchange.com/questions/243756/nfs-servers-and-firewalld)
* [Подключить том NFS | Руководство для администраторов сети Linux](https://www.tldp.org/LDP/nag2/x-087-2-nfs.mountd.html)
* [Конфигурации NFS-сервера | Клиентский портал Red Hat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/storage_administration_guide/nfs-serverconfig)

### <a name="mount-database-files-directory-to-point-to-the-shared-storage"></a>Подключить каталог файлов базы данных, указав общее хранилище

1.  **На основном узле только**, сохранить во временное расположение файлов базы данных. Следующий скрипт создает новый временный каталог и копирует файлы базы данных в новый каталог удаляет старые файлы базы данных. Как SQL Server выполняется как mssql локального пользователя, необходимо убедиться, что после передачи данных в подключенный общий ресурс, локальный пользователь имеет доступ для чтения и записи к общей папке. 

   ``` 
   $ sudo su mssql
   $ mkdir /var/opt/mssql/tmp
   $ cp /var/opt/mssql/data/* /var/opt/mssql/tmp
   $ rm /var/opt/mssql/data/*
   $ exit
   ``` 

1.  На всех узлах кластера измените `/etc/fstab` файл, чтобы включить команду mount.  

   ```bash
   <IP OF NFS SERVER>:<shared_storage_path> <database_files_directory_path> nfs timeo=14,intr 
   ```
   
   Следующий сценарий является примером редактирования.  

   ``` 
   10.8.8.0:/mnt/nfs /var/opt/mssql/data nfs timeo=14,intr 
   ``` 
> [!NOTE] 
>При использовании ресурсов системы файлов (FS) согласно рекомендациям здесь нет необходимости сохранять команда подключения в/etc/fstab. Pacemaker позаботится о монтирования папку при запуске FS кластеризованных ресурсов. С помощью ограждения он будет убедитесь, что служб Федерации не может быть смонтирована дважды. 

1.  Запустите `mount -a` команду для системы, чтобы обновить подключенные пути.  

1.  Скопируйте файлы базы данных и журнала, которые сохранены в `/var/opt/mssql/tmp` к общей папке только что подключенном `/var/opt/mssql/data`. Это необходимо сделать **на основном узле**. Убедитесь, что вы предоставляете разрешения чтения и записи локального пользователя «mssql».

   ``` 
   $ sudo chown mssql /var/opt/mssql/data
   $ sudo chgrp mssql /var/opt/mssql/data
   $ sudo su mssql
   $ cp /var/opt/mssql/tmp/* /var/opt/mssql/data/
   $ rm /var/opt/mssql/tmp/*
   $ exit
   ``` 
 
1.  Проверьте, что SQL Server успешно начинается новый путь к файлу. Для этого на каждом узле. На этом этапе только один узел должен запустить SQL Server за раз. Они оба невозможна, в то же время, так как они оба попытается получить доступ к файлам данных одновременно (Чтобы избежать случайного запуск SQL Server на обоих узлах, убедитесь, что ресурс не подключен дважды с различными узлами с помощью ресурса кластера файловой системы). Следующие команды запуска SQL Server, проверьте состояние и затем остановить SQL Server.
 
   ```bash
   sudo systemctl start mssql-server
   sudo systemctl status mssql-server
   sudo systemctl stop mssql-server
   ```
 
На этом этапе оба экземпляра SQL Server настроены для запуска с файлами базы данных в общем хранилище. Следующим шагом является настройка SQL Server для Pacemaker. 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Установка и настройка Pacemaker на каждом узле кластера


2. На обоих узлах кластера создайте файлы для хранения имени пользователя и пароля SQL Server для входа с помощью Pacemaker. Следующая команда создает и заполняет такой файл:

   ```bash
   sudo touch /var/opt/mssql/secrets/passwd
   echo '<loginName>' | sudo tee -a /var/opt/mssql/secrets/passwd
   echo '<loginPassword>' | sudo tee -a /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd 
   sudo chmod 600 /var/opt/mssql/secrets/passwd    
   ```

3. В брандмауэрах на обоих узлах кластера откройте порты для Pacemaker. Чтобы открыть эти порты с помощью `firewalld`, выполните следующую команду:

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Если вы используете другой брандмауэр, который не имеет встроенной конфигурации высокого уровня доступности, следующие порты должны быть открыты для Pacemaker иметь возможность связываться с другими узлами в кластере
   >
   > * TCP: Порты с кодом 2224, 3121, 21064.
   > * UDP: Порт 5405.

1. Установите пакеты Pacemaker на каждом узле.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```

    

2. Задайте пароль для пользователя по умолчанию, который создается при установке пакетов Pacemaker и Corosync. Используйте одинаковый пароль на обоих узлах. 

   ```bash
   sudo passwd hacluster
   ```

    

3. Включите и запустите службу `pcsd` и Pacemaker. Это позволит узлам повторно подключаться к кластеру после перезагрузки. Выполните следующую команду на обоих узлах:

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. Установите агент ресурсов отказоустойчивого кластера для SQL Server. Выполните следующие команды на обоих узлах: 

   ```bash
   sudo yum install mssql-server-ha
   ```

## <a name="create-the-cluster"></a>Создание кластера 

1. На одном из узлов Создайте кластер.

   ```bash
   sudo pcs cluster auth <nodeName1 nodeName2 ...> -u hacluster
   sudo pcs cluster setup --name <clusterName> <nodeName1 nodeName2 ...>
   sudo pcs cluster start --all
   ```

   > Надстройка RHEL HA имеет ограждения агентов для VMWare и KVM. Ограждения должна быть отключена на всех остальных низкоуровневых оболочек. Отключение агентов ограждения в производственных средах не рекомендуется. По состоянию на период времени отсутствуют агенты ограждения для Hyper-v или облачных сред. Если вы используете одну из этих конфигураций, необходимо отключить ограждения. \**Это не рекомендуется в рабочей системе!**

   Следующая команда отключает агентов ограждения.

   ```bash
   sudo pcs property set stonith-enabled=false
   sudo pcs property set start-failure-is-fatal=false
   ```

2. Настройте кластерные ресурсы для SQL Server, файловую систему и виртуальный IP-ресурсов и передача конфигурации кластера. Вам потребуются следующие сведения:

   - **Имя ресурса SQL Server**: Имя кластеризованного ресурса SQL Server. 
   - **Плавающий IP-имя ресурса**: Имя виртуального ресурса IP-адреса.
   - **IP-адрес**: IP-адрес, который будет использоваться клиентами для подключения к кластеризованного экземпляра SQL Server. 
   - **Имя файловой системы ресурсов**: Имя ресурса файловой системы.
   - **устройство**: Путь к общей папке NFS
   - **устройство**: Локальный путь, что он подключен к общей папке
   - **fstype**: Тип общей папки (т. е. nfs)

   Обновите значения из следующий сценарий для вашей среды. Запустите на одном узле, настройки и запуска кластерной службы.  

   ```bash
   sudo pcs cluster cib cfg 
   sudo pcs -f cfg resource create <sqlServerResourceName> ocf:mssql:fci
   sudo pcs -f cfg resource create <floatingIPResourceName> ocf:heartbeat:IPaddr2 ip=<ip Address>
   sudo pcs -f cfg resource create <fileShareResourceName> Filesystem device=<networkPath> directory=<localPath>         fstype=<fileShareType>
   sudo pcs -f cfg constraint colocation add <virtualIPResourceName> <sqlResourceName>
   sudo pcs -f cfg constraint colocation add <fileShareResourceName> <sqlResourceName> 
   sudo pcs cluster cib-push cfg
   ```

   Например, следующий скрипт создает ресурс кластеризованный SQL Server с именем `mssqlha`и с плавающей запятой ресурсы IP-адрес с IP-адресом `10.0.0.99`. Он также создает ресурс файловой системы и добавляет ограничения, поэтому все ресурсы будут совместно располагаться на том же узле, ресурс SQL. 

   ```bash
   sudo pcs cluster cib cfg
   sudo pcs -f cfg resource create mssqlha ocf:mssql:fci
   sudo pcs -f cfg resource create virtualip ocf:heartbeat:IPaddr2 ip=10.0.0.99
   sudo pcs -f cfg resource create fs Filesystem device="10.8.8.0:/mnt/nfs" directory="/var/opt/mssql/data" fstype="nfs"
   sudo pcs -f cfg constraint colocation add virtualip mssqlha
   sudo pcs -f cfg constraint colocation add fs mssqlha
   sudo pcs cluster cib-push cfg
   ```

   После конфигурации помещается, SQL Server запускается на одном узле. 

3. Убедитесь, что SQL Server запущена. 

   ```bash
   sudo pcs status 
   ```

   Приведенных ниже примерах показаны результаты, когда Pacemaker успешно начата кластеризованного экземпляра SQL Server. 

   ```
   fs     (ocf::heartbeat:Filesystem):    Started sqlfcivm1
   virtualip     (ocf::heartbeat:IPaddr2):      Started sqlfcivm1
   mssqlha  (ocf::mssql:fci): Started sqlfcivm1
   
   PCSD Status:
    slqfcivm1: Online
    sqlfcivm2: Online
   
   Daemon Status:
    corosync: active/disabled
    pacemaker: active/enabled
    pcsd: active/enabled
   ```

## <a name="additional-resources"></a>Дополнительные ресурсы

* [Кластер с нуля](https://clusterlabs.org/doc/Cluster_from_Scratch.pdf) руководство из Pacemaker

## <a name="next-steps"></a>Следующие шаги

[Эксплуатация SQL Server на кластер общих дисков Red Hat Enterprise Linux](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
