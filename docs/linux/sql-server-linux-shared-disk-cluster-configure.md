---
title: Настроить экземпляр отказоустойчивого кластера — SQL Server на Linux (RHEL) | Документация Майкрософт
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.openlocfilehash: 2550c2d53f50f2c5647ed0ab61d4d73e586495e2
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38001816"
---
# <a name="configure-failover-cluster-instance---sql-server-on-linux-rhel"></a>Настроить экземпляр отказоустойчивого кластера — SQL Server на Linux (RHEL)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Экземпляра общего диска с двумя узлами отказоустойчивого кластера SQL Server обеспечивает избыточность на уровне сервера для обеспечения высокой доступности. В этом руководстве вы узнаете, как создать экземпляр двух узлов отказоустойчивого кластера SQL Server в Linux. Конкретные действия, которые выполняются включают:

> [!div class="checklist"]
> * Установка и настройка Linux
> * Установка и настройка SQL Server
> * Настройка файла hosts
> * Настройка общего хранилища и перемещение файлов базы данных
> * Установка и настройка Pacemaker на каждом узле кластера
> * Настройка экземпляра отказоустойчивого кластера

В этой статье объясняется, как создать экземпляр общего диска для двух узлов отказоустойчивого кластера (FCI) для SQL Server. В этой статье содержатся инструкции и примеры сценариев для Red Hat Enterprise Linux (RHEL). Дистрибутивов Ubuntu похожи на RHEL, поэтому примеры сценариев будут обычно также работают под управлением Ubuntu. 

Общие сведения см. в разделе [SQL Server экземпляра (Отказоустойчивого кластера) в Linux](sql-server-linux-shared-disk-cluster-concepts.md).

## <a name="prerequisites"></a>предварительные требования

Для работы в следующем сценарии end-to-end, требуется две машины для развертывания кластера двумя узлами и другой сервер для хранения. Следующие действия описывают настройку этих серверов.

## <a name="set-up-and-configure-linux"></a>Установка и настройка Linux

Первым шагом является настройка операционной системы на узлах кластера. На каждом узле в кластере настройте дистрибутив linux. Используйте те же распространения и версии на обоих узлах. Используйте один из этих следующих дистрибутивов:
    
* RHEL с действительной подпиской для надстройки высокого уровня ДОСТУПНОСТИ

## <a name="install-and-configure-sql-server"></a>Установка и настройка SQL Server

1. Установка и настройка SQL Server на обоих узлах.  Подробные инструкции см. в разделе [Установка SQL Server в Linux](sql-server-linux-setup.md).
1. Назначить один узел в качестве основного, а другой — как дополнительный для целей конфигурации. Использовать эти термины для следующих в этом руководстве.  
1. На вторичном узле остановка и отключение SQL Server.
    В следующем примере останавливается и отключает SQL Server: 
    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
    ```

    > [!NOTE] 
    > Во время установки, сервер главный ключ создается для экземпляра SQL Server и помещается в `var/opt/mssql/secrets/machine-key`. В Linux SQL Server всегда выполняется как локальная учетная запись называется mssql. Так как это локальной учетной записи удостоверения нет общего доступа между узлами. Таким образом необходимо скопировать ключ шифрования из основного узла на каждый дополнительный узел, поэтому каждая учетная запись локального mssql можно получить доступ к его для расшифровки главного ключа сервера. 

1.  На основном узле, создайте имя входа SQL server для Pacemaker и предоставить имени входа разрешение на запуск `sp_server_diagnostics`. Pacemaker использует эту учетную запись, чтобы проверить, какой узел работает под управлением SQL Server. 

    ```bash
    sudo systemctl start mssql-server
    ```
   
   Подключение к SQL Server `master` базы данных с помощью учетной записи sa и выполните следующую команду:

   ```sql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```

   Вы также можете задать разрешения на более детальном уровне. Требует входа с помощью Pacemaker `VIEW SERVER STATE` запросить состояние работоспособности с sp_server_diagnostics, `setupadmin` и `ALTER ANY LINKED SERVER` обновить имя экземпляра отказоустойчивого Кластера с именем ресурса, запустив sp_dropserver и sp_addserver. 

1. На основном узле остановка и отключение SQL Server. 

## <a name="configure-the-hosts-file"></a>Настройка файла hosts

На каждом узле кластера Настройка файла hosts. Файл hosts должна содержать IP-адрес и имя каждого узла кластера.

1. Проверьте IP-адрес для каждого узла. Следующий скрипт показывает IP-адрес вашего текущего узла. 

    ```bash
    sudo ip addr show
    ```

1. Задайте имя компьютера, на каждом узле. Присвойте каждому узлу уникальное имя, которое не более 15 символов или меньше. Задайте имя компьютера, добавив его `/etc/hosts`. Следующий сценарий позволяет изменить `/etc/hosts` с помощью `vi`. 

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

## <a name="configure-storage--move-database-files"></a>Настройка хранилища и перемещение файлов базы данных  

Необходимо указать хранилище с доступом к оба узла. Можно использовать iSCSI, SMB или NFS. Настройка хранилища, предоставление хранилища для узлов кластера и затем переместить ее файлы в новое хранилище. В следующих статьях описаны шаги для каждого типа хранилища:

- [Настройка экземпляра отказоустойчивого кластера — iSCSI — SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
- [Настроить экземпляр отказоустойчивого кластера — NFS - сервера SQL в Linux](sql-server-linux-shared-disk-cluster-configure-nfs.md)
- [Настроить экземпляр отказоустойчивого кластера — SMB — SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure-smb.md)

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

Будет создан FCI в группе ресурсов. Это немного более удобочитаемым, так как группа ресурсов частично устраняют необходимость ограничения. Тем не менее добавьте ресурсы в группе ресурсов, в порядке, в котором им следует запустить. — В порядке, в котором они должны запустить: 

1. Ресурс хранилища
2. Сетевой ресурс
3. Ресурс приложения

В этом примере создаст экземпляр отказоустойчивого Кластера в группе NewLinFCIGrp. Имя группы ресурсов должно быть уникальным с любым ресурсом в Pacemaker.

1.  Создайте дисковый ресурс. Вы получите ответ обратно в том случае, если не имеется проблема. Способ создания дисковый ресурс зависит от типа хранилища. Ниже приведен пример для каждого типа хранилища. Используйте приведенный пример, которое применяется к типу хранилища для кластеризованного хранилища.

    **iSCSI**

    ```bash
    sudo pcs resource create <iSCSIDiskResourceName> Filesystem device="/dev/<VolumeGroupName>/<LogicalVolumeName>" directory="<FolderToMountiSCSIDisk>" fstype="<FileSystemType>" --group RGName
    ```

    \<iSCSIDIskResourceName > — имя ресурса, связанного с диском iSCSI

    \<VolumeGroupName > — имя группы томов  

    \<LogicalVolumeName > — это имя логического тома, который был создан  

    \<FolderToMountiSCSIDIsk > — это папка, для подключения диска (для системных баз данных и расположение по умолчанию, он будет иметь /var/opt/mssql/data)

    \<FileSystemType > будет EXT4 или XFS, в зависимости от форматирование вещей и поддерживает какие распределение. 

    **NFS**

    ```bash
    sudo pcs resource create <NFSDiskResourceName> Filesystem device="<IPAddressOfNFSServer>:<FolderOnNFSServer>" directory="<FolderToMountNFSShare>" fstype=nfs4 options=" nfsvers=4.2,timeo=14,intr" --group RGName
    mount -t nfs4 IPAddressOfNFSServer:FolderOnNFSServer /var/opt/mssql/data -o 
    ```

    \<NFSDIskResourceName > — имя ресурса, связанного с общего ресурса NFS

    \<IPAddressOfNFSServer > является IP-адрес NFS-сервер, который вы собираетесь использовать

    \<FolderOnNFSServer > — это имя общего ресурса NFS

    \<FolderToMountNFSShare > — это папка, для подключения диска (для системных баз данных и расположение по умолчанию, он будет иметь /var/opt/mssql/data)

    Пример показан далее:

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    **SMB**

    ```bash
    sudo pcs resource create SMBDiskResourceName Filesystem device="//<ServerName>/<ShareName>" directory="<FolderName>" fstype=cifs options="vers=3.0,username=<UserName>,password=<Password>,domain=<ADDomain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777" --group <RGName>
    ```

    \<Имя_сервера > — имя сервера с общей папкой SMB

    \<ShareName > — имя общей папки

    \<Имя папки > — имя папки, созданной на предыдущем шаге
    
    \<Имя пользователя > — имя пользователя для доступа к общей папке

    \<Пароль > пароль для пользователя

    \<ADDomain > — это домен AD DS (если применимо, при использовании общей папке SMB на основе Windows Server)

    \<mssqlUID > — это уникальный идентификатор пользователя mssql

    \<mssqlGID > является GID пользователя mssql

    \<RGName > — имя группы ресурсов
 
2.  Создайте IP-адрес, который будет использоваться экземпляром отказоустойчивого Кластера. Вы получите ответ обратно в том случае, если не имеется проблема.

    ```bash
    sudo pcs resource create <IPResourceName> ocf:heartbeat:IPaddr2 ip=<IPAddress> nic=<NetworkCard> cidr_netmask=<NetMask> --group <RGName>
    ```

    \<IPResourceName > — имя ресурса, связанного с IP-адрес

    \<IP-адрес > является IP-адреса для FCI

    \<NetworkCard > сетевой адаптер, связанный с подсетью (т. е. eth0)

    \<Маска подсети > — это маска подсети (т. е. 24)

    \<RGName > — имя группы ресурсов
 
3.  Создание ресурса отказоустойчивого Кластера. Вы получите ответ обратно в том случае, если не имеется проблема.

    ```bash
    sudo pcs resource create FCIResourceName ocf:mssql:fci op defaults timeout=60s --group RGName
    ```

    \<FCIResourceName > является не только имя ресурса, но понятное имя, который связан с отказоустойчивого Кластера. Это, что пользователи и приложения будут использовать для подключения. 

    \<RGName > — имя группы ресурсов.
 
4.  Выполните команду `sudo pcs resource`. Экземпляр отказоустойчивого Кластера должно быть в сети.
 
5.  Подключиться к FCI с помощью SSMS или sqlcmd, используя имя DNS и ресурсов экземпляра отказоустойчивого Кластера.

6.  Выполните инструкцию `SELECT @@SERVERNAME`. Она возвращает имя экземпляра отказоустойчивого Кластера.

7.  Выполните инструкцию `SELECT SERVERPROPERTY('ComputerNamePhysicalNetBIOS')`. Она должна возвращать имя узла, под управлением отказоустойчивого Кластера.

8.  Другой отказоустойчивого Кластера, чтобы другие узлы вручную. См. инструкции в разделе [экземпляр отказоустойчивого кластера выполнить — SQL Server в Linux](sql-server-linux-shared-disk-cluster-operate.md).

9.  Наконец сбой FCI обратно на исходный узел и удалить ограничение совместного размещения.

<!---
|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)
-->
## <a name="summary"></a>Сводка

В этом руководстве вы выполнили следующие задачи.

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
