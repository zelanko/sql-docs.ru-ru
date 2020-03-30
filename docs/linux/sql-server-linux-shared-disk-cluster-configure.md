---
title: Настройка экземпляра отказоустойчивого кластера— SQL Server на Linux (RHEL)
description: Узнайте, как настроить экземпляр отказоустойчивого кластера на Red Hat Enterprise Linux (RHEL) для SQL Server.
ms.custom: seo-lt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.openlocfilehash: 61fe5d7ffb5dfc6ec98f6d5350eff396deaa0312
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "75558329"
---
# <a name="configure-failover-cluster-instance---sql-server-on-linux-rhel"></a>Настройка экземпляра отказоустойчивого кластера — SQL Server на Linux (RHEL)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Экземпляр отказоустойчивого кластера SQL Server с двумя узлами и общим диском обеспечивает избыточность на уровне сервера для поддержки высокой доступности. В этом руководстве приводятся инструкции по созданию экземпляра отказоустойчивого кластера SQL Server с двумя узлами в Linux. Ниже перечислены конкретные действия, которые нужно выполнить.

> [!div class="checklist"]
> * Установка и настройка Linux
> * Установка и настройка SQL Server
> * Настройка файла hosts
> * Настройка общего хранилища и перемещение файлов базы данных
> * Установка и настройка Pacemaker в каждом узле кластера
> * Настройка экземпляра отказоустойчивого кластера

В этой статье объясняется, как создать экземпляр отказоустойчивого кластера (FCI) SQL Server с двумя узлами и общим диском. Здесь содержатся инструкции и примеры сценариев для Red Hat Enterprise Linux (RHEL). Дистрибутивы Ubuntu аналогичны RHEL, поэтому примеры сценариев также будут работать в Ubuntu. 

Концептуальные сведения см. в статье [Экземпляр отказоустойчивого кластера (FCI) SQL Server в Linux](sql-server-linux-shared-disk-cluster-concepts.md).

## <a name="prerequisites"></a>предварительные требования

Для выполнения следующего законченного сценария нужны два компьютера для развертывания двухузлового кластера и сервера для хранения. Ниже описаны действия по настройке этих серверов.

## <a name="set-up-and-configure-linux"></a>Установка и настройка Linux

Сначала необходимо настроить операционную систему в узлах кластера. На каждом узле в кластере настройте дистрибутив Linux. На обоих узлах следует использовать один и тот же дистрибутив и одну и ту же версию. Воспользуйтесь одним из указанных далее дистрибутивов:
    
* RHEL с допустимой подпиской для надстройки высокой доступности

## <a name="install-and-configure-sql-server"></a>Установка и настройка SQL Server

1. Установите и настройте SQL Server на обоих узлах.  Подробные инструкции см. в статье [Установка SQL Server в Linux](sql-server-linux-setup.md).
1. В целях настройки назначьте один узел первичным, а другой — вторичным. Используйте приведенные ниже условия для работы с этим руководством.  
1. Остановите и отключите SQL Server во вторичном узле.
    В следующем примере показаны остановка и отключение SQL Server: 
    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
    ```

    > [!NOTE] 
    > Во время установки создается главный ключ сервера для экземпляра SQL Server и помещается в папку `var/opt/mssql/secrets/machine-key`. На Linux SQL Server всегда выполняется как локальная учетная запись с именем mssql. Так как это локальная учетная запись, ее удостоверение не является общим во всех узлах. Поэтому необходимо скопировать ключ шифрования из первичного узла в каждый вторичный узел, чтобы каждая локальная учетная запись mssql могла получить к нему доступ для расшифровки главного ключа сервера. 

1.  В первичном узле создайте имя входа SQL Server для Pacemaker и предоставьте разрешение на выполнение `sp_server_diagnostics`. Pacemaker использует эту учетную запись, чтобы проверить, в каком узле запущен SQL Server. 

    ```bash
    sudo systemctl start mssql-server
    ```
   
   Подключитесь к базе данных `master` SQL Server с помощью учетной записи SA и выполните следующую команду:

   ```sql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```

   Вы также можете задать разрешения на более детальном уровне. Имени входа Pacemaker требуется разрешение `VIEW SERVER STATE` для запроса состояния работоспособности с помощью sp_server_diagnostics, а также `setupadmin` и `ALTER ANY LINKED SERVER` для изменения имени экземпляра FCI на имя ресурса с помощью sp_dropserver и sp_addserver. 

1. Остановите и отключите SQL Server в первичном узле. 

## <a name="configure-the-hosts-file"></a>Настройка файла hosts

На каждом узле кластера настройте файл hosts. Файл hosts должен содержать IP-адрес и имя каждого узла кластера.

1. Проверьте IP-адрес для каждого узла. Для отображения IP-адреса текущего узла выполните следующий сценарий. 

    ```bash
    sudo ip addr show
    ```

1. Задайте имя компьютера в каждом узле. Присвойте каждому узлу уникальное имя длиной не более 15 символов. Задайте имя компьютера, добавив его к `/etc/hosts`. Следующий сценарий позволяет изменить `/etc/hosts` с помощью `vi`. 

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

## <a name="configure-storage--move-database-files"></a>Настройка хранилища и перемещение файлов базы данных  

Необходимо предоставить хранилище, доступное для обоих узлов. Можно использовать iSCSI, NFS или SMB. Настройте хранилище, представьте его узлам кластера, а затем переместите в него файлы базы данных. Действия, выполняемые для каждого типа хранилища, описаны в следующих статьях:

- [Настройка экземпляра отказоустойчивого кластера (iSCSI) — SQL Server на Linux](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
- [Настройка экземпляра отказоустойчивого кластера (NFS) — SQL Server на Linux](sql-server-linux-shared-disk-cluster-configure-nfs.md)
- [Настройка экземпляра отказоустойчивого кластера (SMB) — SQL Server на Linux](sql-server-linux-shared-disk-cluster-configure-smb.md)

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Установка и настройка Pacemaker в каждом узле кластера

1. На обоих узлах кластера создайте файлы для хранения имени пользователя и пароля SQL Server для входа с помощью Pacemaker. 

    Следующая команда создает и заполняет такой файл:

    ```bash
    sudo touch /var/opt/mssql/secrets/passwd
    sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
    sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
    sudo chown root:root /var/opt/mssql/secrets/passwd 
    sudo chmod 600 /var/opt/mssql/secrets/passwd    
    ```

1. В брандмауэрах на обоих узлах кластера откройте порты для Pacemaker. Чтобы открыть эти порты с помощью `firewalld`, выполните следующую команду:

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
1. Задайте пароль для пользователя по умолчанию, который создается при установке пакетов Pacemaker и Corosync. Используйте одинаковый пароль на обоих узлах. 

   ```bash
   sudo passwd hacluster
   ```
1. Включите и запустите службу `pcsd` и Pacemaker. Это позволит узлам повторно подключаться к кластеру после перезагрузки. Выполните следующую команду на обоих узлах:

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

1. Установите агент ресурсов отказоустойчивого кластера для SQL Server. Выполните следующие команды на обоих узлах: 

   ```bash
   sudo yum install mssql-server-ha
   ```

## <a name="configure-the-failover-cluster-instance"></a>Настройка экземпляра отказоустойчивого кластера

Экземпляр FCI создается в группе ресурсов. Эта процедура несколько проще, так как в группе ресурсов отсутствуют ограничения. Тем не менее, добавьте ресурсы в группу ресурсов в том порядке, в котором они должны запускаться. Порядок запуска должен быть следующим: 

1. ресурс хранилища;
2. сетевой ресурс;
3. ресурс приложения.

В этом примере показано создание FCI в группе NewLinFCIGrp. Имя группы ресурсов должно быть уникальным для любого ресурса, созданного в Pacemaker.

1.  Создайте дисковый ресурс. При отсутствии проблем ответ не возвращается. Способ создания дискового ресурса зависит от типа хранилища. Ниже приведен пример для каждого типа хранилища. Используйте пример, который подходит для типа вашего кластерного хранилища.

    **iSCSI**

    ```bash
    sudo pcs resource create <iSCSIDiskResourceName> Filesystem device="/dev/<VolumeGroupName>/<LogicalVolumeName>" directory="<FolderToMountiSCSIDisk>" fstype="<FileSystemType>" --group RGName
    ```

    \<iSCSIDIskResourceName> — имя ресурса, связанного с диском iSCSI.

    \<VolumeGroupName> — имя группы томов.  

    \<LogicalVolumeName> — имя созданного логического тома.  

    \<FolderToMountiSCSIDIsk> — папка для подключения диска (для системных баз данных и расположения по умолчанию используется /var/opt/mssql/data).

    \<FileSystemType> — EXT4 или XFS в зависимости от того, как были отформатированы данные и какой тип поддерживается дистрибутивом. 

    **NFS**

    ```bash
    sudo pcs resource create <NFSDiskResourceName> Filesystem device="<IPAddressOfNFSServer>:<FolderOnNFSServer>" directory="<FolderToMountNFSShare>" fstype=nfs4 options=" nfsvers=4.2,timeo=14,intr" --group RGName
    mount -t nfs4 IPAddressOfNFSServer:FolderOnNFSServer /var/opt/mssql/data -o 
    ```

    \<NFSDIskResourceName> — имя ресурса, связанного с общей папкой NFS.

    \<IPAddressOfNFSServer> — это IP-адрес NFS-сервера, который будет использоваться.

    \<FolderOnNFSServer> — это имя общей папки NFS.

    \<FolderToMountNFSShare> — папка для подключения диска (для системных баз данных и расположения по умолчанию используется /var/opt/mssql/data).

    Пример показан далее:

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    **SMB**

    ```bash
    sudo pcs resource create SMBDiskResourceName Filesystem device="//<ServerName>/<ShareName>" directory="<FolderName>" fstype=cifs options="vers=3.0,username=<UserName>,password=<Password>,domain=<ADDomain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777" --group <RGName>
    ```

    \<ServerName> — это имя сервера с общим ресурсом SMB.

    \<ShareName> — это имя общей папки.

    \<FolderName> — имя папки, созданной на последнем шаге.
    
    \<UserName> — это имя пользователя для доступа к общей папке.

    \<Password> — это пароль пользователя.

    \<ADDomain> — домен AD DS (если это применимо при использовании общей папки SMB на основе Windows Server).

    \<mssqlUID> — это идентификатор UID пользователя mssql.

    \<mssqlGID> — это идентификатор GID пользователя mssql.

    \<RGName> — имя группы ресурсов.
 
2.  Создайте IP-адрес, который будет использоваться экземпляром FCI. При отсутствии проблем ответ не возвращается.

    ```bash
    sudo pcs resource create <IPResourceName> ocf:heartbeat:IPaddr2 ip=<IPAddress> nic=<NetworkCard> cidr_netmask=<NetMask> --group <RGName>
    ```

    \<IPResourceName> — имя ресурса, связанного с IP-адресом.

    \<IPAddress> — IP-адрес экземпляра FCI.

    \<NetworkCard> — сетевая карта, связанная с подсетью (т. е., eth0).

    \<NetMask> — маска подсети (т. е., 24).

    \<RGName> — имя группы ресурсов.
 
3.  Создание ресурса экземпляра FCI При отсутствии проблем ответ не возвращается.

    ```bash
    sudo pcs resource create FCIResourceName ocf:mssql:fci op defaults timeout=60s --group RGName
    ```

    \<FCIResourceName> — не только имя ресурса, но и понятное имя, связанное с экземпляром FCI. Пользователи и приложения будут использовать его для подключения. 

    \<RGName> — имя группы ресурсов.
 
4.  Выполните команду `sudo pcs resource`. Экземпляр FCI должен быть в сети.
 
5.  Подключитесь к экземпляру FCI с помощью SSMS или sqlcmd, используя DNS-имя или имя ресурса экземпляра FCI.

6.  Выполните инструкцию `SELECT @@SERVERNAME`. Она должна вернуть имя экземпляра FCI.

7.  Выполните инструкцию `SELECT SERVERPROPERTY('ComputerNamePhysicalNetBIOS')`. Она должна вернуть имя узла, на котором запущен экземпляр FCI.

8.  Вручную переведите экземпляр FCI на другой узел. См. инструкции в статье [Работа экземпляра отказоустойчивого кластера — SQL Server на Linux](sql-server-linux-shared-disk-cluster-operate.md).

9.  И, наконец, переведите экземпляр FCI обратно на исходный узел и удалите ограничение на совместное размещение.

<!---

|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)

-->
## <a name="summary"></a>Сводка

В этом руководстве были выполнены следующие задачи:

> [!div class="checklist"]
> * Установка и настройка Linux
> * Установка и настройка SQL Server
> * Настройка файла hosts
> * Настройка общего хранилища и перемещение файлов базы данных
> * Установка и настройка Pacemaker в каждом узле кластера
> * Настройка экземпляра отказоустойчивого кластера

## <a name="next-steps"></a>Дальнейшие действия

- [Работа экземпляра отказоустойчивого кластера — SQL Server на Linux](sql-server-linux-shared-disk-cluster-operate.md)

<!--Image references-->
