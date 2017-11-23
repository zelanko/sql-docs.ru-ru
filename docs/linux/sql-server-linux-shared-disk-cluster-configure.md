---
title: "Настроить экземпляр отказоустойчивого кластера — SQL Server для Linux (RHEL) | Документы Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.workload: Inactive
ms.openlocfilehash: 66c3fe5f03ab597826c8ba0101aaa1cd0b54d2b7
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="configure-failover-cluster-instance---sql-server-on-linux-rhel"></a>Настроить экземпляр отказоустойчивого кластера — SQL Server для Linux (RHEL)

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Экземпляр отказоустойчивого кластера SQL Server двумя узлами общего диска обеспечивает избыточность уровня сервера для обеспечения высокой доступности. В этом учебнике вы узнаете, как для создания экземпляра двух узлов отказоустойчивого кластера SQL Server в Linux. Перечислены шаги, которые необходимо выполнить.

> [!div class="checklist"]
> * Установка и настройка Linux
> * Установка и настройка SQL Server
> * Настройка файла hosts
> * Настройка общего хранилища и перемещение файлов базы данных
> * Установка и настройка Pacemaker на каждом узле кластера
> * Настройка экземпляра отказоустойчивого кластера

В этой статье описывается создание экземпляра отказоустойчивого кластера общего диска с двумя узлами (FCI) для SQL Server. В статье содержатся инструкции и примеры сценариев для Red Hat Enterprise Linux (RHEL). Ubuntu распределения похожи на RHEL, поэтому обычно будут примеры сценариев работы с Ubuntu. 

Основные сведения см. в разделе [SQL Server экземпляр (Отказоустойчивого кластера) в Linux](sql-server-linux-shared-disk-cluster-concepts.md).

## <a name="prerequisites"></a>Предварительные требования

Для выполнения сценария конца в конец ниже требуется две машины для развертывания двух узлов кластера и другой сервер для хранения. Шаги, описанные ниже описываются настройки этих серверов.

## <a name="set-up-and-configure-linux"></a>Установка и настройка Linux

Первым шагом является настройка операционной системы на узлах кластера. На каждом узле в кластере настройте ОС Linux. Используйте те же распространения и версии на обоих узлах. Используйте одно из них, распределений следующие:
    
* RHEL с действительной подпиской для надстройки высокого уровня ДОСТУПНОСТИ

## <a name="install-and-configure-sql-server"></a>Установка и настройка SQL Server

1. Установка и настройка SQL Server на обоих узлах.  Подробные сведения содержатся в разделе [Установка SQL Server в Linux](sql-server-linux-setup.md).
1. Назначить один узел в качестве основной, а другой — как получателя для целей конфигурации. Использовать эти термины для следующих в этом руководстве.  
1. На вторичном узле остановите и отключите SQL Server.
    В следующем примере останавливается и отключает SQL Server: 
    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
    ```

    > [!NOTE] 
    > Во время установки, созданный для экземпляра SQL Server и помещается в главный ключ сервера `var/opt/mssql/secrets/machine-key`. SQL Server в Linux, всегда выполняется под локальной учетной записью, называется mssql. Так как он является локальной учетной записью, его подлинность, не являющихся общими между узлами. Таким образом необходимо скопировать ключ шифрования от основного узла для каждого дополнительного узла, поэтому каждой учетной записи локального mssql можно получить доступ к его расшифровать главный ключ сервера. 

1.  На основном узле, создайте имя входа SQL server для Pacemaker и предоставьте имени входа разрешение для запуска `sp_server_diagnostics`. Pacemaker будет использовать эту учетную запись, чтобы проверить, какой узел работает под управлением SQL Server. 

    ```bash
    sudo systemctl start mssql-server
    ```
   
   Подключиться к серверу SQL `master` базы данных с помощью учетной записи sa и выполните следующую команду:

   ```sql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```

   Вы также можете задать разрешения на более детальном уровне. Требуется имя входа Pacemaker `VIEW SERVER STATE` запросить состояние работоспособности с sp_server_diagnostics, `setupadmin` и `ALTER ANY LINKED SERVER` Чтобы изменить имя экземпляра отказоустойчивого Кластера с именем ресурса, запустив sp_dropserver и sp_addserver. 

1. На основном узле остановите и отключите SQL Server. 

## <a name="configure-the-hosts-file"></a>Настройка файла hosts

На каждом узле кластера Настройка файла hosts. IP-адрес и имя каждого узла кластера, необходимо включить в файл hosts.

1. Проверьте IP-адрес для каждого узла. Следующий скрипт показывает IP-адрес вашего текущего узла. 

    ```bash
    sudo ip addr show
    ```

1. Задайте имя компьютера, на каждом узле. Присвойте каждому узлу уникальное имя, которое составляет 15 символов или меньше. Задайте имя компьютера, добавив его в `/etc/hosts`. Следующий сценарий позволяет изменить `/etc/hosts` с помощью `vi`. 

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

## <a name="configure-storage--move-database-files"></a>Настройка хранилища и перемещение файлов базы данных  

Необходимо предоставить доступ к обоим узлам хранилища. Можно использовать iSCSI, SMB или NFS. Настройка хранилища, представления хранилища для узлов кластера и затем переместить ее файлы в новое хранилище. Следующие статьи описываются нужные шаги для каждого типа хранилища:

- [Настройка экземпляра отказоустойчивого кластера — iSCSI - SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
- [Настроить экземпляр отказоустойчивого кластера — NFS - SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure-nfs.md)
- [Настройте экземпляр отказоустойчивого кластера — SMB - SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure-smb.md)

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Установка и настройка Pacemaker на каждом узле кластера

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

FCI будут создаваться в группе ресурсов. Это немного проще, так как группа ресурсов устраняет необходимость ограничения. Тем не менее добавьте ресурсы в группе ресурсов, в том порядке, который им следует запустить. — В порядке, в котором они должны запустить: 

1. Ресурс хранилища
2. Сетевой ресурс
3. Ресурс приложения

В этом примере создается экземпляр отказоустойчивого Кластера в группе NewLinFCIGrp. Имя группы ресурсов должно быть уникальным в любой ресурс, созданный в Pacemaker.

1.  Создание ресурса диска. Вы получите ответ обратно в том случае, если не является проблемой. Способ создания дисковый ресурс зависит от типа хранения. Ниже приведен пример для каждого типа хранения. Используйте пример, который применяется для типа хранилища для кластеризованного хранилища.

    **iSCSI**

    ```bash
    sudo pcs resource create <iSCSIDiskResourceName> Filesystem device="/dev/<VolumeGroupName>/<LogicalVolumeName>" directory="<FolderToMountiSCSIDisk>" fstype="<FileSystemType>" --group RGName
    ```

    \<iSCSIDIskResourceName > — имя ресурса, связанного с диском iSCSI

    \<VolumeGroupName > — имя группы томов  

    \<LogicalVolumeName > — имя логического тома, который был создан  

    \<FolderToMountiSCSIDIsk > — Папка для подключения диска (для системных баз данных и расположение по умолчанию, он будет иметь /var/opt/mssql/data)

    \<FileSystemType > будет EXT4 или XFS, в зависимости от форматирование вещей и поддерживает какие распределения. 

    **NFS**

    ```bash
    sudo pcs resource create <NFSDiskResourceName> Filesystem device="<IPAddressOfNFSServer>:<FolderOnNFSServer>" directory="<FolderToMountNFSShare>" fstype=nfs4 options=" nfsvers=4.2,timeo=14,intr" --group RGName
    mount -t nfs4 IPAddressOfNFSServer:FolderOnNFSServer /var/opt/mssql/data -o 
    ```

    \<NFSDIskResourceName > — имя ресурса, связанного с общего ресурса NFS

    \<IPAddressOfNFSServer > — IP-адрес сервера NFS, который будет использоваться

    \<FolderOnNFSServer > — имя общего ресурса NFS

    \<FolderToMountNFSShare > — Папка для подключения диска (для системных баз данных и расположение по умолчанию, он будет иметь /var/opt/mssql/data)

     Ниже показан пример:

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    **SMB**

    ```bash
    sudo pcs resource create SMBDiskResourceName Filesystem device="//<ServerName>/<ShareName>" directory="<FolderName>" fstype=cifs options="vers=3.0,username=<UserName>,password=<Password>,domain=<ADDomain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777" --group <RGName>
    ```

    \<Имя_сервера > — имя сервера с общей папкой SMB

    \<ShareName > — имя общей папки

    \<Имя папки > — имя папки, созданные на предыдущем шаге
    
    \<Имя пользователя > — имя пользователя для доступа к общей папке

    \<Пароль > пароль для пользователя

    \<ADDomain > является доменом AD DS (если применимо, при использовании общей папке SMB на основе Windows Server)

    \<mssqlUID > имеет уникальный идентификатор пользователя mssql

    \<mssqlGID > является GID mssql пользователя

    \<RGName > — имя группы ресурсов
 
2.  Создание IP-адрес, который будет использоваться в FCI. Вы получите ответ обратно в том случае, если не является проблемой.

    ```bash
    sudo pcs resource create <IPResourceName> ocf:heartbeat:IPaddr2 ip=<IPAddress> nic=<NetworkCard> cidr_netmask=<NetMask> --group <RGName>
    ```

    \<IPResourceName > — имя ресурса, связанного с IP-адресом

    \<IP-адрес > — IP-адрес для FCI

    \<NetworkCard > сетевой адаптер, связанный с подсетью (т. е. eth0)

    \<Маска подсети > является маска подсети (т. е. 24)

    \<RGName > — имя группы ресурсов
 
3.  Создание ресурса отказоустойчивого Кластера. Вы получите ответ обратно в том случае, если не является проблемой.

    ```bash
    sudo pcs resource create FCIResourceName ocf:mssql:fci op defaults timeout=60s --group RGName
    ```

    \<FCIResourceName > является не только имя ресурса, но понятное имя, связанный с экземпляром отказоустойчивого Кластера. Это то, что пользователи и приложения будут использовать для подключения. 

    \<RGName > — имя группы ресурсов.
 
4.  Выполните команду `sudo pcs resource`. FCI должно быть в сети.
 
5.  Подключиться к FCI с SSMS или sqlcmd, используя имя DNS или ресурса отказоустойчивого Кластера.

6.  Выполните инструкцию `SELECT @@SERVERNAME`. Он должен возвращать имя отказоустойчивого Кластера.

7.  Выполните инструкцию `SELECT SERVERPROPERTY('ComputerNamePhysicalNetBIOS')`. Она возвращает имя узла, который запущен на FCI.

8.  Переход на другой вручную FCI на другие узлы. См. инструкции в разделе [экземпляр отказоустойчивого кластера выполнить — SQL Server в Linux](sql-server-linux-shared-disk-cluster-operate.md).

9.  Наконец ошибкой FCI обратно в исходный узел и удалите ограничение совместного размещения.

<!---
|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)
-->
## <a name="summary"></a>Сводка

В этом учебнике вы выполнили следующие задачи.

> [!div class="checklist"]
> * Установка и настройка Linux
> * Установка и настройка SQL Server
> * Настройка файла hosts
> * Настройка общего хранилища и перемещение файлов базы данных
> * Установка и настройка Pacemaker на каждом узле кластера
> * Настройка экземпляра отказоустойчивого кластера

## <a name="next-steps"></a>Следующие шаги

- [Работать экземпляр отказоустойчивого кластера — SQL Server в Linux](sql-server-linux-shared-disk-cluster-operate.md)

<!--Image references-->
