---
title: Настройка кластера общих дисков SLES для SQL Server
description: Реализуйте высокий уровень доступности, настроив кластер общих дисков SUSE Linux Enterprise Server (SLES) для SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: e5ad1bdd-c054-4999-a5aa-00e74770b481
ms.openlocfilehash: 70701d5c0103da089444177db1143066d0c862cd
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68032220"
---
# <a name="configure-sles-shared-disk-cluster-for-sql-server"></a>Настройка кластера общих дисков SLES для SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Это краткое описание содержит инструкции по созданию кластера общих дисков с двумя узлами для SQL Server на основе SUSE Linux Enterprise Server (SLES). Уровень кластеризации основан на [расширении высокого уровня доступности (HAE)](https://www.suse.com/products/highavailability), построенном на основе [Pacemaker](https://clusterlabs.org/). 

Дополнительные сведения о конфигурации кластера, параметрах агента ресурсов, управлении и рекомендациях см. в статье [Расширение высокого уровня доступности для SUSE Linux Enterprise 12 с пакетом обновления 2 (SP2)](https://www.suse.com/documentation/sle-ha-12/index.html).

## <a name="prerequisites"></a>предварительные требования

Для выполнения следующего законченного сценария нужны два компьютера для развертывания двухузлового кластера и сервера для настройки общего ресурса NFS. Ниже описаны действия по настройке этих серверов.

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>Установка и настройка операционной системы в каждом узле кластера

Сначала необходимо настроить операционную систему в узлах кластера. Для этого пошагового руководства используйте SLES с допустимой подпиской для надстройки высокой доступности.

## <a name="install-and-configure-sql-server-on-each-cluster-node"></a>Установка и настройка SQL Server в каждом узле кластера

1. Установите и настройте SQL Server в обоих узлах. Подробные инструкции см. в статье [Установка SQL Server в Linux](sql-server-linux-setup.md).
2. В целях настройки назначьте один узел первичным, а другой — вторичным. Используйте приведенные ниже условия для работы с этим руководством. 
3. Остановите и отключите SQL Server на вторичном узле. В следующем примере показаны остановка и отключение SQL Server:

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
    ```

    > [!NOTE]
    > Во время установки главный ключ сервера для экземпляра SQL Server создается и помещается в папку `/var/opt/mssql/secrets/machine-key`. На Linux SQL Server всегда выполняется как локальная учетная запись с именем mssql. Так как это локальная учетная запись, ее удостоверение не является общим на всех узлах. Поэтому необходимо скопировать ключ шифрования с первичного узла на каждый вторичный узел, чтобы каждая локальная учетная запись mssql могла получить к нему доступ для расшифровки главного ключа сервера.
4. В первичном узле создайте имя входа SQL Server для Pacemaker и предоставьте разрешение на выполнение `sp_server_diagnostics`. Pacemaker использует эту учетную запись, чтобы проверить, на каком узле запущен SQL Server.

    ```bash
    sudo systemctl start mssql-server
    ```
    Подключитесь к базе данных master в SQL Server с помощью учетной записи SA и выполните следующую команду:

    ```sql
    USE [master]
    GO
    CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'
    GRANT VIEW SERVER STATE TO <loginName>
    ```
5. Остановите и отключите SQL Server в первичном узле.
6. Следуйте указаниям в [документации](https://www.suse.com/documentation/sles11/book_sle_admin/data/sec_basicnet_yast.html) по SUSE, чтобы настроить и обновить файл hosts для каждого узла кластера. Файл hosts должен содержать IP-адрес и имя каждого узла кластера.

    Чтобы проверить IP-адрес текущего узла, выполните следующие действия.

    ```bash
    sudo ip addr show
    ```

    Задайте имя компьютера на каждом узле. Присвойте каждому узлу уникальное имя длиной не более 15 символов. Задайте имя компьютера, добавив его к `/etc/hostname` с помощью [yast](https://www.suse.com/documentation/sles11/book_sle_admin/data/sec_basicnet_yast.html) или [вручную](https://www.suse.com/documentation/sled11/book_sle_admin/data/sec_basicnet_manconf.html).

    В следующем примере показан файл `/etc/hosts` с дополнениями для двух узлов `SLES1` и `SLES2`.

    ```
    127.0.0.1   localhost
    10.128.18.128 SLES1
    10.128.16.77 SLES2
    ```

    > [!NOTE]
    > У всех узлов кластера должен быть доступ друг к другу через SSH. Таким средствам, как hb_report или crm_report (для устранения неполадок) и обозреватель журнала Hawk, не нужен пароль для доступа SSH между узлами. В противном случае они могут только собирать данные из текущего узла. Если вы используете нестандартный SSH-порт, воспользуйтесь параметром -X (см. страницу [man](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_requirements_other.html)). Например, если вы используете SSH-порт 3479, вызовите средство crm_report с помощью следующей команды:
    >
    >```bash
    >crm_report -X "-p 3479" [...]
    >```
    >Дополнительные сведения см. в [руководстве по администрированию].(https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.misc)

В следующем разделе вы настроите общее хранилище и переместите в него файлы базы данных.  

## <a name="configure-shared-storage-and-move-database-files"></a>Настройка общего хранилища и перемещение файлов базы данных

Существует множество решений для предоставления общего хранилища. В этом пошаговом руководстве демонстрируется настройка общего хранилища с NFS. Мы рекомендуем следовать рекомендациям и использовать Kerberos для защиты NFS: 

- [Совместное использование файловых систем с NFS](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#cha.nfs)

Если вы не будете следовать этому руководству, любой пользователь, который может получить доступ к вашей сети и подменить IP-адрес узла SQL, сможет получить и доступ к файлам данных. Как всегда, проведите моделирование угроз для вашей системы, прежде чем использовать ее в рабочей среде. 

Другой вариант хранения — использовать общую папку SMB:

- [Раздел по Samba в документации по SUSE](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#cha.samba)

### <a name="configure-an-nfs-server"></a>Настройка сервера NFS

Сведения о настройке сервера NFS см. в следующих шагах документации по SUSE: [Настройка сервера NFS](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#sec.nfs.configuring-nfs-server).

### <a name="configure-all-cluster-nodes-to-connect-to-the-nfs-shared-storage"></a>Настройка всех узлов кластера для подключения к общему хранилищу NFS

Перед настройкой NFS на клиенте для подключения пути к файлам базы данных SQL Server с указанием общего хранилища убедитесь, что файлы базы данных сохранены во временном расположении, чтобы их можно было скопировать позже в общую папку:

1. **Только на основном узле** сохраните файлы базы данных во временном расположении. Следующий скрипт создает новый временный каталог, копирует файлы базы данных в него и удаляет старые файлы базы данных. Так как SQL Server выполняется от имени локального пользователя mssql, необходимо убедиться в том, что после передачи данных в подключенный общий ресурс локальный пользователь имеет доступ к общей папке для чтения и записи. 

    ```bash
    su mssql
    mkdir /var/opt/mssql/tmp
    cp /var/opt/mssql/data/* /var/opt/mssql/tmp
    rm /var/opt/mssql/data/*
    exit
    ```

    Настройте клиент NFS на всех узлах кластера:

    - [Настройка клиентов](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#sec.nfs.configuring-nfs-clients)

    > [!NOTE]
    > Мы рекомендуем следовать рекомендациям SUSE в отношении хранилища NFS высокого уровня доступности: [Высокодоступное хранилище NFS с использованием DRBD и Pacemaker](https://www.suse.com/documentation/sle-ha-12/book_sleha_techguides/data/art_ha_quick_nfs.html).

2. Убедитесь в том, что SQL Server успешно запускается с новым путем к файлу. Выполните это действие в каждом узле. На этом этапе SQL Server должен выполняться только в одном узле в каждый момент времени. Они не могут выполняться одновременно из-за того, что пытаются одновременно получить доступ к файлам данных (чтобы избежать случайного запуска SQL Server в обоих узлах, используйте ресурс кластера файловой системы, чтобы убедиться в том, что общий ресурс не подключен дважды в разных узлах). Приведенные ниже команды запускают SQL Server, проверяют его состояние, а затем останавливают SQL Server.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    sudo systemctl stop mssql-server
    ```

На этом этапе оба экземпляра SQL Server настроены для работы с файлами базы данных в общем хранилище. Следующим шагом является настройка SQL Server для Pacemaker. 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Установка и настройка Pacemaker в каждом узле кластера

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
    sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
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

Ниже описаны действия по настройке ресурса кластера для SQL Server. Есть два параметра, которые необходимо настроить.

- **Имя ресурса SQL Server**. Имя кластеризованного ресурса SQL Server. 
- **Значение времени ожидания**. Значение времени ожидания — это период времени, в течение которого кластер ожидает, когда ресурс будет подключен к сети. Для SQL Server это время ожидания перевода базы данных `master` в режим "в сети". 

Замените значения в приведенном ниже скрипте значениями для своей среды. Запустите его в одном узле, чтобы настроить и запустить кластеризованную службу.

```bash
sudo crm configure
primitive <sqlServerResourceName> ocf:mssql:fci op start timeout=<timeout_in_seconds>
colocation <constraintName> inf: <virtualIPResourceName> <sqlServerResourceName>
show
commit
exit
```

Например, следующий скрипт создает кластеризованный ресурс SQL Server с именем mssqlha. 

```bash
sudo crm configure
primitive mssqlha ocf:mssql:fci op start timeout=60s
colocation admin_addr_mssqlha inf: admin_addr mssqlha
show
commit
exit
```

После фиксации конфигурации SQL Server запустится на том же узле, что и ресурс виртуального IP-адреса. 

Дополнительные сведения см. в разделе [Настройка ресурсов кластера и управление ими (командная строка)](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.manual_config). 

### <a name="verify-that-sql-server-is-started"></a>Убедитесь в том, что SQL Server запущен. 

Для этого выполните команду **crm status**.

```bash
crm status
```

В следующих примерах показаны результаты успешного запуска Pacemaker в качестве кластеризованного ресурса. 
```
2 nodes configured
2 resources configured

Online: [ SLES1 SLES2 ]

Full list of resources:

 admin_addr     (ocf::heartbeat:IPaddr2):       Started SLES1
 mssqlha        (ocf::mssql:fci):       Started SLES1
```

## <a name="managing-cluster-resources"></a>Управление ресурсами кластера

Сведения об управлении ресурсами кластера см. в следующем разделе документации по SUSE: [Управление ресурсами кластера](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.config.crm )

### <a name="manual-failover"></a>Отработка отказа вручную

Хотя ресурсы настроены для автоматической отработки отказа (или миграцию) на другие узлы кластера в случае сбоя оборудования или программного обеспечения, можно также вручную переместить ресурс на другой узел в кластере с помощью графического интерфейса Pacemaker или командной строки. 

Используйте команду migrate для этой задачи. Например, чтобы перенести ресурс SQL на узел кластера с именем SLES2, выполните: 

```bash
crm resource
migrate mssqlha SLES2
```

## <a name="additional-resources"></a>Дополнительные ресурсы

[Руководство по администрированию. Расширение для обеспечения высокой доступности SUSE Linux Enterprise](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html) 
