---
title: Настройка общего кластера Red Hat Enterprise Linux для SQL Server
description: Реализуйте высокий уровень доступности, настроив кластер общих дисков Red Hat Enterprise Linux для SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: dcc0a8d3-9d25-4208-8507-a5e65d2a9a15
ms.openlocfilehash: dd320079291199b512bb9d9e8334e7ec8c2803a7
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2019
ms.locfileid: "68810979"
---
# <a name="configure-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>Настройка общего кластера дисков Red Hat Enterprise Linux для SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Это руководство содержит инструкции по созданию кластера общих дисков с двумя узлами для SQL Server на основе Red Hat Enterprise Linux. Уровень кластеризации основан на [надстройке высокого уровня доступности](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf) Red Hat Enterprise Linux (RHEL), созданной на базе [Pacemaker](https://clusterlabs.org/). Экземпляр SQL Server активен либо в одном, либо в другом узле.

> [!NOTE] 
> Для доступа к надстройке высокого уровня доступности и документации по Red Hat требуется подписка. 

Как показано на схеме ниже, хранилище представляется двум серверам. Компоненты кластеризации — Corosync и Pacemaker — координируют обмен данными и управление ресурсами. Один из серверов имеет активное подключение к ресурсам хранилища и SQL Server. Когда Pacemaker обнаруживает сбой, компоненты кластеризации управляют перемещением ресурсов в другой узел.  

![Red Hat Enterprise Linux 7, общий диск, кластер SQL](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 

Дополнительные сведения о конфигурации кластера, параметрах агентов ресурсов и управлении см. в [справочной документации по RHEL](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html).


> [!NOTE] 
> На этом этапе интеграция SQL Server с Pacemaker реализована не на таком уровне, как с WSFC в Windows. Внутри SQL сведения о наличии кластера отсутствуют, вся оркестрация осуществляется снаружи, а сама служба управляется Pacemaker как автономный экземпляр. Кроме того, например, динамические административные представления sys.dm_os_cluster_nodes и sys.dm_os_cluster_properties кластера не будут иметь записи.
Чтобы использовать строку подключения, указывающую на строковое имя сервера, а не IP-адрес, им потребуется зарегистрировать на DNS-сервере IP-адрес, использованный для создания ресурса виртуального IP-адреса (как описано в следующих разделах) с выбранным именем сервера.

В следующих разделах описаны действия по настройке решения отказоустойчивого кластера. 

## <a name="prerequisites"></a>предварительные требования

Для выполнения следующего законченного сценария нужны два компьютера для развертывания двухузлового кластера и сервера для настройки сервера NFS. Ниже описаны действия по настройке этих серверов.

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>Установка и настройка операционной системы в каждом узле кластера

Сначала необходимо настроить операционную систему в узлах кластера. Для этого пошагового руководства используйте RHEL с допустимой подпиской для надстройки высокой доступности. 

## <a name="install-and-configure-sql-server-on-each-cluster-node"></a>Установка и настройка SQL Server в каждом узле кластера

1. Установите и настройте SQL Server в обоих узлах.  Подробные инструкции см. в статье [Установка SQL Server в Linux](sql-server-linux-setup.md).

1. В целях настройки назначьте один узел первичным, а другой — вторичным. Используйте приведенные ниже условия для работы с этим руководством.  

1. Остановите и отключите SQL Server во вторичном узле.

   В следующем примере показаны остановка и отключение SQL Server: 

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl disable mssql-server
   ```
> [!NOTE] 
> Во время установки главный ключ сервера для экземпляра SQL Server создается и помещается в папку `/var/opt/mssql/secrets/machine-key`. На Linux SQL Server всегда выполняется как локальная учетная запись с именем mssql. Так как это локальная учетная запись, ее удостоверение не является общим во всех узлах. Поэтому необходимо скопировать ключ шифрования из первичного узла в каждый вторичный узел, чтобы каждая локальная учетная запись mssql могла получить к нему доступ для расшифровки главного ключа сервера. 

1. В первичном узле создайте имя входа SQL Server для Pacemaker и предоставьте разрешение на выполнение `sp_server_diagnostics`. Pacemaker использует эту учетную запись, чтобы проверить, в каком узле запущен SQL Server. 

   ```bash
   sudo systemctl start mssql-server
   ```

   Подключитесь к базе данных `master` SQL Server с помощью учетной записи SA и выполните следующую команду:

   ```bashsql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'

   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```
   Вы также можете задать разрешения на более детальном уровне. Имени входа Pacemaker требуется разрешение `VIEW SERVER STATE` для запроса состояния работоспособности с помощью sp_server_diagnostics, а также `setupadmin` и `ALTER ANY LINKED SERVER` для изменения имени экземпляра FCI на имя ресурса с помощью sp_dropserver и sp_addserver. 

1. Остановите и отключите SQL Server в первичном узле. 

1. В каждом узле кластера настройте файл hosts. Файл hosts должен содержать IP-адрес и имя каждого узла кластера. 

    Проверьте IP-адрес для каждого узла. Для отображения IP-адреса текущего узла выполните приведенный ниже сценарий. 

   ```bash
   sudo ip addr show
   ```

   Задайте имя компьютера в каждом узле. Присвойте каждому узлу уникальное имя длиной не более 15 символов. Задайте имя компьютера, добавив его к `/etc/hosts`. Следующий сценарий позволяет изменить `/etc/hosts` с помощью `vi`. 

   ```bash
   sudo vi /etc/hosts
   ```
   В следующем примере показан файл `/etc/hosts` с дополнениями для двух узлов `sqlfcivm1` и `sqlfcivm2`.

   ```bash
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.128 sqlfcivm1
   10.128.16.77 sqlfcivm2
   ```

В следующем разделе вы настроите общее хранилище и переместите в него файлы базы данных. 

## <a name="configure-shared-storage-and-move-database-files"></a>Настройка общего хранилища и перемещение файлов базы данных 

Существует множество решений для предоставления общего хранилища. В этом пошаговом руководстве демонстрируется настройка общего хранилища с NFS. Мы рекомендуем следовать рекомендациям и использовать Kerberos для защиты NFS (пример можно найти здесь: https://www.certdepot.net/rhel7-use-kerberos-control-access-nfs-network-shares/) ). 

>[!Warning]
>Если не защитить NFS, любой пользователь, который может получить доступ к вашей сети и подменить IP-адрес узла SQL, сможет получить и доступ к файлам данных. Как всегда, проведите моделирование угроз для вашей системы, прежде чем использовать ее в рабочей среде. Другой вариант хранения — использовать общую папку SMB.

### <a name="configure-shared-storage-with-nfs"></a>Настройка общего хранилища с NFS

> [!IMPORTANT] 
> Размещение файлов базы данных на NFS-сервере с версией ниже 4 не поддерживается в этом выпуске. Это относится и к использованию NFS для отказоустойчивой кластеризации общих дисков, а также для баз данных в некластеризованных экземплярах. Мы работаем над включением других версий сервера NFS в будущих выпусках. 

На сервере NFS выполните указанные ниже действия.

1. Установите `nfs-utils`.

   ```bash
   sudo yum -y install nfs-utils
   ```

1. Включите и запустите `rpcbind`.

   ```bash
   sudo systemctl enable rpcbind && sudo systemctl start rpcbind
   ```

1. Включите и запустите `nfs-server`.
 
   ```bash
   sudo systemctl enable nfs-server && sudo systemctl start nfs-server
   ```
 
1.  Измените `/etc/exports`, чтобы экспортировать каталог, общий доступ к которому необходимо предоставить. Для каждой нужной общей папки требуется одна строка. Пример: 

   ```bash
   /mnt/nfs  10.8.8.0/24(rw,sync,no_subtree_check,no_root_squash)
   ```

1. Экспортируйте общие папки:

   ```bash
   sudo exportfs -rav
   ```

1. Убедитесь в том, что пути являются общими или экспортированными. На сервере NFS выполните следующую команду:

   ```bash
   sudo showmount -e
   ```

1. Добавьте исключение в SELinux:

   ```bash
   sudo setsebool -P nfs_export_all_rw 1
   ```
   
1. Откройте брандмауэр на сервере.

   ```bash 
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

### <a name="configure-all-cluster-nodes-to-connect-to-the-nfs-shared-storage"></a>Настройка всех узлов кластера для подключения к общему хранилищу NFS

Выполните указанные ниже действия во всех узлах кластера.

1.  Установите `nfs-utils`.

   ```bash
   sudo yum -y install nfs-utils
   ```

1. Откройте брандмауэр в клиентах и на сервере NFS:

   ```bash
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

1. Убедитесь в том, что общие папки NFS доступны на клиентских компьютерах.

   ```bash
   sudo showmount -e <IP OF NFS SERVER>
   ```

1. Повторите эти действия во всех узлах кластера.

Дополнительные сведения об использовании NFS см. в следующих статьях:

* [Серверы и брандмауэры NFS | Stack Exchange](https://unix.stackexchange.com/questions/243756/nfs-servers-and-firewalld)
* [Подключение тома NFS | Руководство для сетевых администраторов Linux](https://www.tldp.org/LDP/nag2/x-087-2-nfs.mountd.html)
* [Конфигурация сервера NFS | Портал для клиентов Red Hat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/storage_administration_guide/nfs-serverconfig)

### <a name="mount-database-files-directory-to-point-to-the-shared-storage"></a>Подключение каталога файлов базы данных для указания общего хранилища

1.  **Только в основном узле** сохраните файлы базы данных во временном расположении. Приведенный ниже скрипт создает временный каталог, копирует файлы базы данных в него и удаляет старые файлы базы данных. Так как SQL Server выполняется от имени локального пользователя mssql, необходимо убедиться в том, что после передачи данных в подключенный общий ресурс локальный пользователь имеет доступ к общей папке для чтения и записи. 

   ``` 
   $ sudo su mssql
   $ mkdir /var/opt/mssql/tmp
   $ cp /var/opt/mssql/data/* /var/opt/mssql/tmp
   $ rm /var/opt/mssql/data/*
   $ exit
   ``` 

1.  Во всех узлах кластера измените файл `/etc/fstab`, включив в него команду подключения.  

   ```bash
   <IP OF NFS SERVER>:<shared_storage_path> <database_files_directory_path> nfs timeo=14,intr 
   ```
   
   Пример изменения показан в приведенном ниже скрипте.  

   ``` 
   10.8.8.0:/mnt/nfs /var/opt/mssql/data nfs timeo=14,intr 
   ``` 
> [!NOTE] 
>Если вы используете ресурс файловой системы, как рекомендуется в этой статье, сохранять команду подключения в /etc/fstab не нужно. Pacemaker подключает папки при запуске кластеризованного ресурса файловой системы. Ограждение гарантирует, что файловая система не будет подключена дважды. 

1.  Выполните команду `mount -a`, чтобы система обновила подключенные пути.  

1.  Скопируйте файлы базы данных и журналов, сохраненные в `/var/opt/mssql/tmp`, в новую подключенную общую папку `/var/opt/mssql/data`. Это необходимо сделать только **в основном узле**. Убедитесь в том, что локальному пользователю mssql предоставлены разрешения на чтение и запись.

   ``` 
   $ sudo chown mssql /var/opt/mssql/data
   $ sudo chgrp mssql /var/opt/mssql/data
   $ sudo su mssql
   $ cp /var/opt/mssql/tmp/* /var/opt/mssql/data/
   $ rm /var/opt/mssql/tmp/*
   $ exit
   ``` 
 
1.  Убедитесь в том, что SQL Server успешно запускается с новым путем к файлу. Выполните это действие в каждом узле. На этом этапе SQL Server должен выполняться только в одном узле в каждый момент времени. Они не могут выполняться одновременно из-за того, что пытаются одновременно получить доступ к файлам данных (чтобы избежать случайного запуска SQL Server в обоих узлах, используйте ресурс кластера файловой системы, чтобы убедиться в том, что общий ресурс не подключен дважды в разных узлах). Приведенные ниже команды запускают SQL Server, проверяют его состояние, а затем останавливают SQL Server.
 
   ```bash
   sudo systemctl start mssql-server
   sudo systemctl status mssql-server
   sudo systemctl stop mssql-server
   ```
 
На этом этапе оба экземпляра SQL Server настроены для работы с файлами базы данных в общем хранилище. Следующим шагом является настройка SQL Server для Pacemaker. 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Установка и настройка Pacemaker в каждом узле кластера


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

   > Если вы используете другой брандмауэр, который не имеет встроенной конфигурации высокого уровня доступности, откройте следующие порты, чтобы Pacemaker мог связываться с другими узлами в кластере.
   >
   > * TCP: порты 2224, 3121, 21064
   > * UDP: порт 5405

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

## <a name="create-the-cluster"></a>Создайте кластер. 

1. Создайте кластер в одном из узлов.

   ```bash
   sudo pcs cluster auth <nodeName1 nodeName2 ...> -u hacluster
   sudo pcs cluster setup --name <clusterName> <nodeName1 nodeName2 ...>
   sudo pcs cluster start --all
   ```

   > Надстройка HA для RHEL включает в себя агенты ограждения для VMWare и KVM. В других гипервизорах ограждение должно быть отключено. Отключать агенты ограждения в рабочих средах не рекомендуется. В настоящее время агенты ограждения для HyperV или облачных сред отсутствуют. Если вы используете одну из этих конфигураций, необходимо отключить ограждение. \**В рабочей системе делать это НЕ рекомендуется!* *

   Приведенная ниже команда отключает агенты ограждения.

   ```bash
   sudo pcs property set stonith-enabled=false
   sudo pcs property set start-failure-is-fatal=false
   ```

2. Настройте кластерные ресурсы для SQL Server, файловой системы и виртуального IP-адреса, а затем отправьте конфигурацию в кластер. Потребуются следующие сведения:

   - **Имя ресурса SQL Server**. Имя кластеризованного ресурса SQL Server. 
   - **Имя ресурса плавающего IP-адреса**. Имя ресурса виртуального IP-адреса.
   - **IP-адрес**. IP-адрес, который клиенты будут использовать для подключения к кластеризованному экземпляру SQL Server. 
   - **Имя ресурса файловой системы**. Имя для ресурса файловой системы.
   - **Устройство**. Путь к общей папке NFS.
   - **Устройство**. Локальный путь подключения к общей папке.
   - **fstype**. Тип общей папки (nfs).

   Замените значения в приведенном ниже скрипте значениями для своей среды. Запустите его в одном узле, чтобы настроить и запустить кластеризованную службу.  

   ```bash
   sudo pcs cluster cib cfg 
   sudo pcs -f cfg resource create <sqlServerResourceName> ocf:mssql:fci
   sudo pcs -f cfg resource create <floatingIPResourceName> ocf:heartbeat:IPaddr2 ip=<ip Address>
   sudo pcs -f cfg resource create <fileShareResourceName> Filesystem device=<networkPath> directory=<localPath>         fstype=<fileShareType>
   sudo pcs -f cfg constraint colocation add <virtualIPResourceName> <sqlResourceName>
   sudo pcs -f cfg constraint colocation add <fileShareResourceName> <sqlResourceName> 
   sudo pcs cluster cib-push cfg
   ```

   Например, приведенный ниже скрипт создает кластеризованный ресурс SQL Server с именем `mssqlha` и ресурс плавающего IP-адреса с IP-адресом `10.0.0.99`. Кроме того, он создает ресурс файловой системы и добавляет ограничения, чтобы все ресурсы находились в одном узле с ресурсом SQL. 

   ```bash
   sudo pcs cluster cib cfg
   sudo pcs -f cfg resource create mssqlha ocf:mssql:fci
   sudo pcs -f cfg resource create virtualip ocf:heartbeat:IPaddr2 ip=10.0.0.99
   sudo pcs -f cfg resource create fs Filesystem device="10.8.8.0:/mnt/nfs" directory="/var/opt/mssql/data" fstype="nfs"
   sudo pcs -f cfg constraint colocation add virtualip mssqlha
   sudo pcs -f cfg constraint colocation add fs mssqlha
   sudo pcs cluster cib-push cfg
   ```

   После отправки конфигурации SQL Server запустится в одном узле. 

3. Убедитесь в том, что SQL Server запущен. 

   ```bash
   sudo pcs status 
   ```

   В приведенных ниже примерах показаны результаты успешного запуска кластеризованного экземпляра SQL Server с помощью Pacemaker. 

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

* Руководство [Кластер с нуля](https://clusterlabs.org/doc/Cluster_from_Scratch.pdf) от Pacemaker

## <a name="next-steps"></a>Следующие шаги

[Использование SQL Server в кластере общих дисков Red Hat Enterprise Linux](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
