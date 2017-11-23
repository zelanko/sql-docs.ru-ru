---
title: "Настройка кластера общего Red Hat Enterprise Linux для SQL Server | Документы Microsoft"
description: "Реализация высокой доступности с помощью конфигурации кластера общего диска Red Hat Enterprise Linux для SQL Server."
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: dcc0a8d3-9d25-4208-8507-a5e65d2a9a15
ms.workload: On Demand
ms.openlocfilehash: 1417e02a0a0c2ef56171a5dd99782cdbb4abe0e1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="configure-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>Настройка кластера общего диска Red Hat Enterprise Linux для SQL Server

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Это руководство содержит инструкции для создания кластера с двумя узлами общего диска для SQL Server в Red Hat Enterprise Linux. Уровень кластеризации основан на Red Hat Enterprise Linux (RHEL) [высокого уровня ДОСТУПНОСТИ надстройки](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf) построены на основе [Pacemaker](http://clusterlabs.org/). Экземпляр SQL Server активен на одном узле или другой.

> [!NOTE] 
> Доступ к Red Hat HA надстройки и документации требует подписку. 

В диаграмме ниже показан хранилище представляется двумя серверами. Кластерные компоненты - Corosync и Pacemaker - координировать связи и управление ресурсами. Один из серверов имеет активное подключение к ресурсам хранилища и SQL Server. Когда Pacemaker обнаруживает сбой кластеризации компоненты управления перемещения ресурсов на другой узел.  

![Red Hat Enterprise Linux 7 общий диск кластера SQL](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 

Дополнительные сведения о конфигурации кластера, параметры агентов ресурсов и управления на сайте [RHEL справочной документации](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html).


> [!NOTE] 
> На этом этапе интеграции SQL Server с Pacemaker не, а также как WSFC в Windows. Из в SQL, неизвестно о наличии кластера, все orchestration находится за пределами в и служба управляется как отдельный экземпляр Pacemaker. Также к примеру, кластер sys.dm_os_cluster_nodes динамические административные представления и sys.dm_os_cluster_properties будет ни одной записи.
Чтобы использовать строку подключения, указывающая на строку имя сервера и не используйте IP-адрес, они будут иметь для регистрации в своих DNS-сервера IP-адрес, используемый для создания виртуального IP-ресурс (как описано ниже) с именем выбранного сервера.

Следующие разделы выполните эти шаги для настройки решения отказоустойчивого кластера. 

## <a name="prerequisites"></a>Предварительные требования

Для выполнения сценария конца в конец ниже необходимы две машины для развертывания двух узлов кластера и другой сервер, чтобы настроить NFS-сервер. Шаги, описанные ниже описываются настройки этих серверов.

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>Установка и настройка операционной системы на каждом узле кластера

Первым шагом является настройка операционной системы на узлах кластера. Для этого пошагово используйте RHEL с действительной подпиской для надстройки высокого уровня ДОСТУПНОСТИ. 

## <a name="install-and-configure-sql-server-on-each-cluster-node"></a>Установка и настройка SQL Server на каждом узле кластера

1. Установить и настроить SQL Server на обоих узлах.  Подробные сведения содержатся в разделе [Установка SQL Server в Linux](sql-server-linux-setup.md).

1. Назначить один узел в качестве основной, а другой — как получателя для целей конфигурации. Использовать эти термины для следующих в этом руководстве.  

1. На вторичном узле остановите и отключите SQL Server.

   В следующем примере останавливается и отключает SQL Server: 

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl disable mssql-server
   ```
> [!NOTE] 
> Во время установки, созданный для экземпляра SQL Server и помещается в главный ключ сервера `/var/opt/mssql/secrets/machine-key`. SQL Server в Linux, всегда выполняется под локальной учетной записью, называется mssql. Так как он является локальной учетной записью, его подлинность, не являющихся общими между узлами. Таким образом необходимо скопировать ключ шифрования от основного узла для каждого дополнительного узла, поэтому каждой учетной записи локального mssql можно получить доступ к его расшифровать главный ключ сервера. 

1. На основном узле, создайте имя входа SQL server для Pacemaker и предоставьте имени входа разрешение для запуска `sp_server_diagnostics`. Pacemaker будет использовать эту учетную запись, чтобы проверить, какой узел работает под управлением SQL Server. 

   ```bash
   sudo systemctl start mssql-server
   ```

   Подключиться к серверу SQL `master` базы данных с помощью учетной записи sa и выполните следующую команду:

   ```bashsql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'

   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```
   Вы также можете задать разрешения на более детальном уровне. Требуется имя входа Pacemaker `VIEW SERVER STATE` запросить состояние работоспособности с sp_server_diagnostics, `setupadmin` и `ALTER ANY LINKED SERVER` Чтобы изменить имя экземпляра отказоустойчивого Кластера с именем ресурса, запустив sp_dropserver и sp_addserver. 

1. На основном узле остановите и отключите SQL Server. 

1. Настройка файла hosts для каждого узла кластера. Необходимо включить файл узла, IP-адрес и имя каждого узла кластера. 

    Проверьте IP-адрес для каждого узла. Следующий скрипт показывает IP-адрес вашего текущего узла. 

   ```bash
   sudo ip addr show
   ```

   Задайте имя компьютера, на каждом узле. Присвойте каждому узлу уникальное имя, которое составляет 15 символов или меньше. Задайте имя компьютера, добавив его в `/etc/hosts`. Следующий сценарий позволяет изменить `/etc/hosts` с помощью `vi`. 

   ```bash
   sudo vi /etc/hosts
   ```
   В следующем примере показан `/etc/hosts` дополнений для двух узлов с именем `sqlfcivm1` и `sqlfcivm2`.

   ```bash
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.128 sqlfcivm1
   10.128.16.77 sqlfcivm2
   ```

В следующем разделе будет Настройка общего хранилища и перемещение файлов базы данных в этом хранилище. 

## <a name="configure-shared-storage-and-move-database-files"></a>Настройка общего хранилища и перемещение файлов базы данных 

Существуют различные решения для обеспечения общего хранилища. Это пошаговое руководство демонстрирует Настройка общего хранилища с помощью NFS. Рекомендуется следовать рекомендациям и использовать Kerberos для защиты NFS (можно найти в данном примере: https://www.certdepot.net/rhel7-use-kerberos-control-access-nfs-network-shares/). 

>[!Warning]
>Если не защитить NFS, любой пользователь, можно получить доступ к сети и подмены IP-адрес узла SQL будет может получить доступ к файлам данных. Как всегда убедитесь, что вы угроз модели системы перед его использованием в рабочей среде. Другой вариант хранения данных — использовать общую папку SMB.

### <a name="configure-shared-storage-with-nfs"></a>Настройка общего хранилища с помощью NFS

> [!IMPORTANT] 
> Размещение файлов базы данных на NFS-сервер с версией < 4 не поддерживается в этом выпуске. Сюда относится использование NFS для общего диска отказоустойчивой кластеризации, а также баз данных на некластеризованные экземпляры. Мы работаем над включением других версий сервера NFS в будущих выпусках. 

NFS-сервера выполните следующие действия.

1. Установка`nfs-utils`

   ```bash
   sudo yum -y install nfs-utils
   ```

1. Включение и начало`rpcbind`

   ```bash
   sudo systemctl enable rpcbind && systemctl start rpcbind
   ```

1. Включение и начало`nfs-server`
 
   ```bash
   systemctl enable nfs-server && systemctl start nfs-server
   ```
 
1.  Изменение `/etc/exports` для экспорта в каталог, который вы хотите поделиться. Для каждой общей папки, которые нужно потребуется 1 строка. Например: 

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

1.  От NFS-сервера Установка`nfs-utils`

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

1. Проверка видимости общих ресурсов NFS на клиентских компьютерах

   ```bash
   sudo showmount -e <IP OF NFS SERVER>
   ```

1. Повторите эти действия на всех узлах кластера.

Дополнительные сведения об использовании NFS см. следующие ресурсы:

* [NFS серверов и firewalld | Стек Exchange](http://unix.stackexchange.com/questions/243756/nfs-servers-and-firewalld)
* [Монтирование томов NFS | Руководство по администраторы сети Linux](http://www.tldp.org/LDP/nag2/x-087-2-nfs.mountd.html)
* [Конфигурации NFS-сервера](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/Reference_Guide/s1-nfs-server-export.html)

### <a name="mount-database-files-directory-to-point-to-the-shared-storage"></a>Подключите каталог файлов базы данных для указания общего хранилища

1.  **На основном узле только**, сохранить во временное расположение файлов базы данных. Следующий скрипт создает новый временный каталог и копирует файлы базы данных в новый каталог удаляет старые файлы базы данных. Как SQL Server выполняется как mssql локального пользователя, необходимо убедитесь в том, что после передачи данных в общую папку подключенного, локальный пользователь имеет доступ для чтения и записи к общей папке. 

   ``` 
   $ su mssql
   $ mkdir /var/opt/mssql/tmp
   $ cp /var/opt/mssql/data/* /var/opt/mssql/tmp
   $ rm /var/opt/mssql/data/*
   $ exit
   ``` 

1.  Измените на всех узлах кластера `/etc/fstab` файла следует включить команды mount.  

   ```bash
   <IP OF NFS SERVER>:<shared_storage_path> <database_files_directory_path> nfs timeo=14,intr 
   ```
   
   Следующий сценарий показан пример правки.  

   ``` 
   10.8.8.0:/mnt/nfs /var/opt/mssql/data nfs timeo=14,intr 
   ``` 
> [!NOTE] 
>При использовании ресурсов системы файла (FS), согласно рекомендациям ниже, нет необходимости сохранять команда подключения в/etc/fstab. Pacemaker берет на себя монтирование папку при запуске FS кластеризованных ресурсов. С помощью разграничения он будет ensurethe, он не может быть смонтирована дважды. 

1.  Запустите `mount -a` команду для обновления подключенных пути системы.  

1.  Скопируйте файлы базы данных и журналов, сохраненные на `/var/opt/mssql/tmp` к общей папке только что подключенном `/var/opt/mssql/data`. Это необходимо сделать **на основном узле**. Убедитесь, что предоставить разрешения на чтение и запись к «mssql» локального пользователя.

   ``` 
   $ chown mssql /var/opt/mssql/data
   $ chgrp mssql /var/opt/mssql/data
   $ su mssql
   $ cp /var/opt/mssql/tmp/* /var/opt/mssql/data/
   $ rm /var/opt/mssql/tmp/*
   $ exit
   ``` 
 
1.  Проверьте, что SQL Server успешно начинает новый путь к файлу. Для этого на каждом узле. На этом этапе одновременно только один узел должен запустить SQL Server. Они не работают в то же время, так как они оба попытается получить доступ к файлам данных одновременно (Чтобы избежать случайного запуск SQL Server на обоих узлах, ресурс кластера файловой системы убедитесь, что общий ресурс не подключен дважды на разных узлах). Следующие команды запуска SQL Server, проверьте состояние и затем остановить SQL Server.
 
   ```bash
   sudo systemctl start mssql-server
   sudo systemctl status mssql-server
   sudo systemctl stop mssql-server
   ```
 
На этом этапе оба экземпляра SQL Server, настроенных для запуска с файлами базы данных в общем хранилище. Следующим шагом является настройка SQL Server для Pacemaker. 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Установка и настройка Pacemaker на каждом узле кластера


2. На обоих узлах кластера создайте файлы для хранения имени пользователя и пароля SQL Server для входа с помощью Pacemaker. Следующая команда создает и заполняет такой файл:

   ```bash
   sudo touch /var/opt/mssql/secrets/passwd
   sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
   sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd 
   sudo chmod 600 /var/opt/mssql/secrets/passwd    
   ```

3. В брандмауэрах на обоих узлах кластера откройте порты для Pacemaker. Чтобы открыть эти порты с помощью `firewalld`, выполните следующую команду:

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Если вы используете другой брандмауэр, который не имеет встроенной конфигурации высокого уровня доступности, откройте следующие порты, чтобы Pacemaker мог связываться с другими узлами в кластере.
   >
   > * Порты TCP: 2224, 3121, 21064.
   > * Порт UDP: 5405.

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
   sudo pcs cluster auth <nodeName1 nodeName2 …> -u hacluster
   sudo pcs cluster setup --name <clusterName> <nodeName1 nodeName2 …>
   sudo pcs cluster start --all
   ```

   > RHEL HA надстройки имеет ограждения агентов для VMWare и KVM. Разграничения должна быть отключена на всех остальных низкоуровневые оболочки. Отключение разграничения агентов в производственных средах не рекомендуется. По состоянию на период времени отсутствуют разграничения агенты для Hyper-v или облачных сред. Если вы используете одну из этих конфигураций, необходимо отключить разграничения. \**Это не рекомендуется в рабочей среде!**

   Следующая команда отключает разграничения агентов.

   ```bash
   sudo pcs property set stonith-enabled=false
   sudo pcs property set start-failure-is-fatal=false
   ```

2. Настройка ресурсов кластера для SQL Server, файловую систему и виртуальный IP- и принудительной отправки конфигурации кластера. Требуются следующие сведения:

   - **Имя ресурса SQL Server**: имя кластеризованного ресурса SQL Server. 
   - **Значение времени ожидания**: значение времени ожидания — это объем времени ожидания кластера при подключении ресурса. Для SQL Server, это время, которое предполагается, что SQL Server необходимо выполнить, чтобы перевести `master` базы данных в сети.  
   - **С плавающей запятой IP-имя ресурса**: имя виртуального ресурса IP-адреса.
   - **IP-адрес**: IP-адрес, который будет использоваться клиентами для подключения к кластеризованного экземпляра SQL Server. 
   - **Имя файловой системы ресурсов**: имя ресурса файловой системы.
   - **устройство**: путь к общей папке NFS
   - **устройство**: локальный путь, что он подключен к общей папке
   - **тип_файловой_системы**: тип файла общий ресурс (т. е. nfs)

   Обновление значений из приведенный ниже сценарий для вашей среды. Запустите на одном узле, чтобы настроить и запустить кластеризованной службы.  

   ```bash
   sudo pcs cluster cib cfg 
   sudo pcs -f cfg resource create <sqlServerResourceName> ocf:mssql:fci op defaults timeout=<timeout_in_seconds>
   sudo pcs -f cfg resource create <floatingIPResourceName> ocf:heartbeat:IPaddr2 ip=<ip Address>
   sudo pcs -f cfg resource create <fileShareResourceName> Filesystem device=<networkPath> directory=<localPath>         fstype=<fileShareType>
   sudo pcs -f cfg constraint colocation add <virtualIPResourceName> <sqlResourceName>
   sudo pcs -f cfg constraint colocation add <fileShareResourceName> <sqlResourceName> 
   sudo pcs cluster cib-push cfg
   ```

   Например, следующий скрипт создает ресурса кластеризованного сервера SQL с именем `mssqlha`и с плавающей запятой IP ресурсы с IP-адресом `10.0.0.99`. Он также создает ресурс файловой системы и добавляет ограничения, поэтому все ресурсы совместно размещенные на одном узле в качестве ресурса SQL. 

   ```bash
   sudo pcs cluster cib cfg
   sudo pcs -f cfg resource create mssqlha ocf:mssql:fci op defaults timeout=60s
   sudo pcs -f cfg resource create virtualip ocf:heartbeat:IPaddr2 ip=10.0.0.99
   sudo pcs -f cfg resource create fs Filesystem device="10.8.8.0:/mnt/nfs" directory="/var/opt/mssql/data" fstype="nfs"
   sudo pcs -f cfg constraint colocation add virtualip mssqlha
   sudo pcs -f cfg constraint colocation add fs mssqlha
   sudo pcs cluster cib-push cfg
   ```

   После конфигурации помещается, SQL Server запускается на одном узле. 

3. Убедитесь, что запущен SQL Server. 

   ```bash
   sudo pcs status 
   ```

   В следующих примерах показано результаты после Pacemaker успешно запустить кластеризованный экземпляр SQL Server. 

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

* [Кластер с нуля](http://clusterlabs.org/doc/Cluster_from_Scratch.pdf) из Pacemaker руководства по

## <a name="next-steps"></a>Следующие шаги

[Эксплуатация SQL Server в Red Hat Enterprise Linux общего диска кластера](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
