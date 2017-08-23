---
title: "Настройка SLES общего диска кластера для SQL Server | Документы Microsoft"
description: "Реализация высокой доступности с помощью конфигурации кластера общего диска SUSE Linux Enterprise Server (SLES) для SQL Server."
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: e5ad1bdd-c054-4999-a5aa-00e74770b481
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 02cf781a1035326ad5073f6a6d3219e8a7d9c070
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---

# <a name="configure-sles-shared-disk-cluster-for-sql-server"></a>Настройка SLES общего диска кластера для SQL Server

Это руководство содержит инструкции для создания общего диска кластера 2 узла для SQL Server в SUSE Linux Enterprise Server (SLES). Кластеризации уровень основан на SUSE [высокий уровень доступности расширения (для которых Имеется)](https://www.suse.com/products/highavailability) построены на основе [Pacemaker](http://clusterlabs.org/). 

Дополнительные сведения о конфигурации кластера, параметры агента ресурсов, управления, советы и рекомендации см. в разделе [SUSE Linux Enterprise высокого уровня доступности расширения 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html).

> [!NOTE]
> На этом этапе интеграции SQL Server с Pacemaker в Linux не, а также как WSFC в Windows. Из в SQL, неизвестно о наличии кластера, все orchestration находится за пределами в и служба управляется как отдельный экземпляр Pacemaker. Кроме того имя виртуальной сети доступен только в WSFC, не имеет эквивалента в одной и той же в Pacemaker. Ожидается, что @@servername и sys.servers для возврата имени узла, а sys.dm_os_cluster_nodes кластера динамических административных представлений и sys.dm_os_cluster_properties нет записей. Чтобы использовать строку подключения, указывающая на строку имя сервера и не используйте IP-адрес, они будут иметь для регистрации в своих DNS-сервера IP-адрес, используемый для создания виртуального IP-ресурс (как описано ниже) с именем выбранного сервера.

## <a name="prerequisites"></a>Предварительные требования

Для выполнения сценария конца в конец ниже необходимы две машины для развертывания двух узлов кластера и другой сервер для настройки общих папок NFS. Шаги, описанные ниже описываются настройки этих серверов.

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>Установка и настройка операционной системы на каждом узле кластера

Первым шагом является настройка операционной системы на узлах кластера. Для этого пошагово используйте SLES с действительной подпиской для надстройки высокого уровня ДОСТУПНОСТИ.

## <a name="install-and-configure-sql-server-on-each-cluster-node"></a>Установка и настройка SQL Server на каждом узле кластера

1. Установить и настроить SQL Server на обоих узлах. Подробные сведения содержатся в разделе [Установка SQL Server в Linux](sql-server-linux-setup.md).
2. Назначить один узел в качестве основной, а другой — как получателя для целей конфигурации. Использовать эти термины для следующих в этом руководстве. 
3. На вторичном узле остановите и отключите SQL Server. В следующем примере останавливается и отключает SQL Server:

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
    ```

    > [!NOTE]
    > Во время установки сервера главный ключ создается для экземпляра SQL Server и размещается в var/opt/mssql/секреты /-ключ компьютера. SQL Server в Linux, всегда выполняется под локальной учетной записью, называется mssql. Так как он является локальной учетной записью, его подлинность, не являющихся общими между узлами. Таким образом необходимо скопировать ключ шифрования от основного узла для каждого дополнительного узла, поэтому каждой учетной записи локального mssql можно получить доступ к его расшифровать главный ключ сервера.
4. На основном узле, создайте имя входа SQL server для Pacemaker и предоставьте имени входа разрешение для запуска `sp_server_diagnostics`. Pacemaker будет использовать эту учетную запись, чтобы проверить, какой узел работает под управлением SQL Server.

    ```bash
    sudo systemctl start mssql-server
    ```
    Подключитесь к базе данных master SQL Server с учетной записью «sa» и выполните следующую команду:

    ```tsql
    USE [master]
    GO
    CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'
    GRANT VIEW SERVER STATE TO <loginName>
    ```
5. На основном узле остановите и отключите SQL Server.
6. Следуйте указаниям, приведенным [в документации по SUSE](https://www.suse.com/documentation/sles11/book_sle_admin/data/sec_basicnet_yast.html) для настройки и обновить файл hosts на всех узлах кластера. Файл «hosts» должен включать IP-адрес и имя каждого узла кластера.

    Чтобы проверить IP-адрес текущего узла запуска:

    ```bash
    sudo ip addr show
    ```

    Задайте имя компьютера, на каждом узле. Присвойте каждому узлу уникальное имя, которое составляет 15 символов или меньше. Задайте имя компьютера, добавив его в `/etc/hostname` с помощью [yast](https://www.suse.com/documentation/sles11/book_sle_admin/data/sec_basicnet_yast.html) или [вручную](https://www.suse.com/documentation/sled11/book_sle_admin/data/sec_basicnet_manconf.html).

    В следующем примере показан `/etc/hosts` дополнений для двух узлов с именем `SLES1` и `SLES2`.

    ```
    127.0.0.1   localhost
    10.128.18.128 SLES1
    10.128.16.77 SLES2
    ```

    > [!NOTE]
    > Все узлы кластера должны иметь доступ к друг с другом через SSH. Таким средствам, как hb_report или crm_report (для устранения неполадок) и обозреватель журнала Hawk, не нужен пароль для доступа SSH между узлами. В противном случае они могут только собирать данные из текущего узла. В случае, если используется нестандартный порт SSH, используйте параметр -X ([см. справочную страницу](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_requirements_other.html)). Например если SSH-порта 3479, вызовите crm_report с:
    >
    >```bash
    >crm_report -X "-p 3479" [...]
    >```
    >Дополнительные сведения см. в разделе [руководство по администрированию]. (https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.misc)

В следующем разделе будет Настройка общего хранилища и перемещение файлов базы данных в этом хранилище.  

## <a name="configure-shared-storage-and-move-database-files"></a>Настройка общего хранилища и перемещение файлов базы данных

Существуют различные решения для обеспечения общего хранилища. Это пошаговое руководство демонстрирует Настройка общего хранилища с помощью NFS. Корпорация Майкрософт рекомендует следовать рекомендациям и использовать Kerberos для защиты NFS: 

- [Совместное использование файловых систем с помощью NFS](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#cha.nfs)

Если не следовать этой рекомендации, любой, кто может получить доступ к сети и подмены IP-адрес узла SQL сможет получить доступ к файлам данных. Как всегда убедитесь, что вы угроз модели системы перед его использованием в рабочей среде. 

Другой вариант хранения данных является использование общей папки SMB:

- [Раздел Samba SUSE документации](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#cha.samba)

### <a name="configure-an-nfs-server"></a>Настройка NFS-сервера

Чтобы настроить NFS-сервера, см. в следующих шагах в документации SUSE: [Настройка сервера для NFS](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#sec.nfs.configuring-nfs-server).

### <a name="configure-all-cluster-nodes-to-connect-to-the-nfs-shared-storage"></a>Настройки всех узлов кластера для подключения к хранилищу общих NFS

Прежде чем настроить клиент NFS, чтобы подключить пути к файлам базы данных SQL Server, чтобы она указывала на расположение общего хранилища, убедитесь, что сохранить файлы базы данных во временную папку, чтобы иметь возможность скопировать их позже на общую папку:

1. **На основном узле только**, сохранить во временное расположение файлов базы данных. Следующий скрипт создает новый временный каталог и копирует файлы базы данных в новый каталог удаляет старые файлы базы данных. Как SQL Server выполняется как mssql локального пользователя, необходимо убедитесь в том, что после передачи данных в общую папку подключенного, локальный пользователь имеет доступ для чтения и записи к общей папке. 

    ```bash
    su mssql
    mkdir /var/opt/mssql/tmp
    cp /var/opt/mssql/data/* /var/opt/mssql/tmp
    rm /var/opt/mssql/data/*
    exit
    ```

    Настройте клиент NFS на всех узлах кластера.

    - [Настройка клиентов](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#sec.nfs.configuring-nfs-clients)

    > [!NOTE]
    > Рекомендуется следовать советы и рекомендации, связанные с хранилищем высокой доступных NFS SUSE: [высокой доступные хранилища NFS с DRBD и Pacemaker](https://www.suse.com/documentation/sle-ha-12/book_sleha_techguides/data/art_ha_quick_nfs.html).

2. Проверьте, что SQL Server успешно начинает новый путь к файлу. Для этого на каждом узле. На этом этапе одновременно только один узел должен запустить SQL Server. Они не работают в то же время, так как они оба попытается получить доступ к файлам данных одновременно (Чтобы избежать случайного запуск SQL Server на обоих узлах, ресурс кластера файловой системы убедитесь, что общий ресурс не подключен дважды на разных узлах). Следующие команды запуска SQL Server, проверьте состояние и затем остановить SQL Server.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    sudo systemctl stop mssql-server
    ```

На этом этапе оба экземпляра SQL Server, настроенных для запуска с файлами базы данных в общем хранилище. Следующим шагом является настройка SQL Server для Pacemaker. 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Установка и настройка Pacemaker на каждом узле кластера

1. **На обоих узлах кластера создайте файлы для хранения имени пользователя и пароля SQL Server для входа Pacemaker**. Следующая команда создает и заполняет такой файл:

    ```bash
    sudo touch /var/opt/mssql/secrets/passwd
    sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
    sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
    sudo chown root:root /var/opt/mssql/secrets/passwd 
    sudo chmod 600 /var/opt/mssql/secrets/passwd
    ```
2. **У всех узлов кластера должен быть доступ друг к другу через SSH.** Таким средствам, как hb_report или crm_report (для устранения неполадок) и обозреватель журнала Hawk, не нужен пароль для доступа SSH между узлами. В противном случае они могут только собирать данные из текущего узла. Если вы используете нестандартный SSH-порт, воспользуйтесь параметром -X (см. страницу man). Например, если вы используете SSH-порт 3479, вызовите средство hb_report с помощью следующей команды:

    ```bash
    crm_report -X "-p 3479" [...]
    ```

    Дополнительные сведения см. в [руководстве по системным требованиям и рекомендациям в документации SUSE](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_requirements_other.html).

3. **Установите расширение высокого уровня доступности.** Чтобы установить это расширение, выполните действия, описанные в руководстве по установке и настройке в документации SUSE.
    
    [Краткое руководство по установке и настройке](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html)

4. **Установите агент ресурсов отказоустойчивого кластера для SQL Server.** Выполните следующие команды на обоих узлах:

    ```bash
    sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server.repo
    sudo zypper --gpg-auto-import-keys refresh
    sudo zypper install mssql-server-ha
    ```

5. **Автоматически настройте первый узел.** Затем настройте запуск кластера с одним узлом. Для этого необходимо настроить первый узел — SLES1. Следуйте инструкциям, описанным в руководстве SUSE по [настройке первого узла](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.1st-node).

    После завершения настройки проверьте состояние кластера с помощью команды `crm status`.
    ```bash
    crm status
    ```

    В результатах должно быть видно, что узел SLES1 настроен.

6. **Добавьте узлы в существующий кластер.** Затем присоедините узел SLES2 к кластеру. Следуйте инструкциям, описанным в руководстве SUSE по [добавлению второго узла](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.2nd-node).
    
    После завершения настройки проверьте состояние кластера с помощью команды **crm status**. Если второй узел добавлен успешно, выходные данные должны быть примерно следующими:
        
    ```
    2 nodes configured
    1 resource configured
    Online: [ SLES1 SLES2 ]
    Full list of resources:
    admin_addr     (ocf::heartbeat:IPaddr2):       Started SLES1
    ```

    > [!NOTE]
    > **admin_addr** — это виртуальный кластерный ресурс IP, который настраивается в процессе первоначальной установки кластера с одним узлом.

7.  **Процедуры удаления.** Если необходимо удалить узел из кластера, используйте скрипт начальной загрузки **ha-cluster-remove**. Дополнительные сведения см. в разделе с [обзором скриптов начальной загрузки](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.bootstrap).  

## <a name="configure-the-cluster-resources-for-sql-server"></a>Настройка ресурсов кластера для SQL Server

Далее описывается, как настроить ресурс кластера для SQL Server. Существует два параметра, которые нужно настроить.

- **Имя ресурса SQL Server**: имя кластеризованного ресурса SQL Server. 
- **Значение времени ожидания**: значение времени ожидания — это объем времени, кластер должен подождать, пока ресурс переводится в оперативный режим. Для SQL Server, это время, которое предполагается, что SQL Server необходимо выполнить, чтобы перевести `master` базы данных в сети. 

Обновление значений из приведенный ниже сценарий для вашей среды. Запустите на одном узле, чтобы настроить и запустить кластеризованной службы.

```bash
sudo crm configure
primitive <sqlServerResourceName> ocf:mssql:fci op start timeout=<timeout_in_seconds>
colocation <constraintName> inf: <virtualIPResourceName> <sqlServerResourceName>
show
commit
exit
```

Например следующий скрипт создает ресурса кластеризованного сервера SQL с именем mssqlha. 

```bash
sudo crm configure
primitive mssqlha ocf:mssql:fci op start timeout=60s
colocation admin_addr_mssqlha inf: admin_addr mssqlha
show
commit
exit
```

После настройки SQL Server запускается на том же узле, виртуальные IP-адреса. 

Дополнительные сведения см. в разделе [Настройка и управление ресурсами кластера (командной строки)](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.manual_config). 

### <a name="verify-that-sql-server-is-started"></a>Убедитесь, что запущен SQL Server. 

Чтобы убедиться, что SQL Server запущена, выполните **состояние crm** команды:

```bash
crm status
```

Ниже приведены результаты при Pacemaker успешно запущен как кластеризованный ресурс. 
```
2 nodes configured
2 resources configured

Online: [ SLES1 SLES2 ]

Full list of resources:

 admin_addr     (ocf::heartbeat:IPaddr2):       Started SLES1
 mssqlha        (ocf::mssql:fci):       Started SLES1
```

## <a name="managing-cluster-resources"></a>Управление ресурсами кластера

Для управления ресурсами кластера, см. в следующем разделе SUSE: [управление ресурсами кластера](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.config.crm )

### <a name="manual-failover"></a>Отработка отказа вручную

Несмотря на то, что ресурсы настраиваются автоматически при сбое (или перенести) на другие узлы кластера в случае сбоя оборудования или программного обеспечения, можно также вручную переместить ресурс на другой узел в кластере, с помощью графического интерфейса пользователя Pacemaker или из командной строки. 

Команда миграции для данной задачи. Например для миграции ресурсов SQL именам узлов кластера SLES2 выполните: 

```bash
crm resource
migrate mssqlha SLES2
```

## <a name="additional-resources"></a>Дополнительные ресурсы

[Расширение высокого уровня доступности Linux Enterprise SUSE - руководство по администрированию](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html) 

