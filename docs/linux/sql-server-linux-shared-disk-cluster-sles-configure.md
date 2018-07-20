---
title: Настройка общего диска кластера SLES для SQL Server | Документация Майкрософт
description: Реализации высокого уровня доступности, настроив кластер общих дисков SUSE Linux Enterprise Server (SLES) для SQL Server.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: e5ad1bdd-c054-4999-a5aa-00e74770b481
ms.openlocfilehash: f9608d4a36d8fb29185a9da949caf561f5fb1734
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084247"
---
# <a name="configure-sles-shared-disk-cluster-for-sql-server"></a>Настройка общего диска кластера SLES для SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Это руководство содержит инструкции для создания общего диска кластера 2 узла для SQL Server в SUSE Linux Enterprise Server (SLES). Кластеризации уровень основан на SUSE [высокий уровень доступности расширения (для которых Имеется)](https://www.suse.com/products/highavailability) создаются на основе [Pacemaker](http://clusterlabs.org/). 

Дополнительные сведения о конфигурации кластера, параметры агента ресурсов, управления, рекомендации и рекомендации, см. в разделе [SUSE Linux Enterprise высокого уровня доступности расширения 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html).

## <a name="prerequisites"></a>предварительные требования

Чтобы выполнить следующий сценарий end-to-end, вам понадобятся две машины, чтобы развернуть два узла кластера и другого сервера, чтобы настроить в общий ресурс NFS. Следующие действия описывают настройку этих серверов.

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>Установка и настройка операционной системы на каждом узле кластера

Первым шагом является настройка операционной системы на узлах кластера. Для в этом пошаговом руководстве используйте SLES с действительной подпиской для надстройки высокого уровня ДОСТУПНОСТИ.

## <a name="install-and-configure-sql-server-on-each-cluster-node"></a>Установка и настройка SQL Server на каждом узле кластера

1. Установка и настройка SQL Server на обоих узлах. Подробные инструкции см. в разделе [Установка SQL Server в Linux](sql-server-linux-setup.md).
2. Назначить один узел в качестве основного, а другой — как дополнительный для целей конфигурации. Использовать эти термины для следующих в этом руководстве. 
3. На вторичном узле остановка и отключение SQL Server. В следующем примере останавливается и отключает SQL Server:

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
    ```

    > [!NOTE]
    > Во время установки экземпляра SQL Server и поместить в главный ключ сервера `/var/opt/mssql/secrets/machine-key`. В Linux SQL Server всегда выполняется как локальная учетная запись называется mssql. Так как это локальной учетной записи удостоверения нет общего доступа между узлами. Таким образом необходимо скопировать ключ шифрования из основного узла на каждый дополнительный узел, поэтому каждая учетная запись локального mssql можно получить доступ к его для расшифровки главного ключа сервера.
4. На основном узле, создайте имя входа SQL server для Pacemaker и предоставить имени входа разрешение на запуск `sp_server_diagnostics`. Pacemaker использует эту учетную запись, чтобы проверить, какой узел работает под управлением SQL Server.

    ```bash
    sudo systemctl start mssql-server
    ```
    Подключение к базе данных master SQL Server с учетной записью «sa» и выполните следующую команду:

    ```tsql
    USE [master]
    GO
    CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'
    GRANT VIEW SERVER STATE TO <loginName>
    ```
5. На основном узле остановка и отключение SQL Server.
6. Следуйте указаниям, приведенным [в документации по SUSE](https://www.suse.com/documentation/sles11/book_sle_admin/data/sec_basicnet_yast.html) Чтобы настроить и обновить файл hosts для каждого узла кластера. Файл «hosts» должна содержать IP-адрес и имя каждого узла кластера.

    Чтобы проверить IP-адрес текущего узла выполнения:

    ```bash
    sudo ip addr show
    ```

    Задайте имя компьютера, на каждом узле. Присвойте каждому узлу уникальное имя, которое не более 15 символов или меньше. Задайте имя компьютера, добавив его `/etc/hostname` с помощью [yast](https://www.suse.com/documentation/sles11/book_sle_admin/data/sec_basicnet_yast.html) или [вручную](https://www.suse.com/documentation/sled11/book_sle_admin/data/sec_basicnet_manconf.html).

    В следующем примере показан `/etc/hosts` с дополнениями для двух узлов с именем `SLES1` и `SLES2`.

    ```
    127.0.0.1   localhost
    10.128.18.128 SLES1
    10.128.16.77 SLES2
    ```

    > [!NOTE]
    > Все узлы кластера должны иметь возможность обращаться друг к другу через SSH. Таким средствам, как hb_report или crm_report (для устранения неполадок) и обозреватель журнала Hawk, не нужен пароль для доступа SSH между узлами. В противном случае они могут только собирать данные из текущего узла. Если вы используете нестандартный порт SSH, используйте параметр -X ([см. страницу](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_requirements_other.html)). Например если SSH-порт 3479, вызовите crm_report с:
    >
    >```bash
    >crm_report -X "-p 3479" [...]
    >```
    >Дополнительные сведения см. в статье [руководство по администрированию]. (https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.misc)

В следующем разделе будет настройки общего хранилища и перемещение файлов базы данных в хранилище.  

## <a name="configure-shared-storage-and-move-database-files"></a>Настройка общего хранилища и перемещение файлов базы данных

Существует множество решений для предоставления общего хранилища. В этом пошаговом руководстве демонстрируется настройка общего хранилища с помощью NFS. Мы рекомендуем следовать рекомендации и использовать Kerberos для защиты NFS: 

- [Общий доступ к файловым системам с NFS](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#cha.nfs)

Если при несоблюдении этой рекомендации, всем, кто может получить доступ к сети и подмены IP-адрес узла SQL будет иметь возможность доступа к файлам данных. Как всегда убедитесь, что вы угроз модели системы перед его использованием в рабочей среде. 

Другим вариантом хранения является использование общей папки SMB:

- [Samba разделе документации по SUSE](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#cha.samba)

### <a name="configure-an-nfs-server"></a>Настройка NFS-сервера

Чтобы настроить NFS-сервер, см. в разделе инструкциям ниже, в документации по SUSE: [Настройка NFS-сервер](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#sec.nfs.configuring-nfs-server).

### <a name="configure-all-cluster-nodes-to-connect-to-the-nfs-shared-storage"></a>Настройки всех узлов кластера для подключения к хранилищу общих NFS

Прежде чем настроить клиент NFS для подключения пути к файлам базы данных SQL Server, чтобы указать расположение общего хранилища, убедитесь, что сохранить файлы базы данных во временное расположение, чтобы иметь возможность скопировать их позже общей папки:

1. **На основном узле только**, сохранить во временное расположение файлов базы данных. Следующий скрипт создает новый временный каталог и копирует файлы базы данных в новый каталог удаляет старые файлы базы данных. Как SQL Server выполняется как mssql локального пользователя, необходимо убедиться, что после передачи данных в подключенный общий ресурс, локальный пользователь имеет доступ для чтения и записи к общей папке. 

    ```bash
    su mssql
    mkdir /var/opt/mssql/tmp
    cp /var/opt/mssql/data/* /var/opt/mssql/tmp
    rm /var/opt/mssql/data/*
    exit
    ```

    Настройка NFS-клиента на всех узлах кластера:

    - [Настройка клиентов](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#sec.nfs.configuring-nfs-clients)

    > [!NOTE]
    > Мы рекомендуем следовать рекомендации и рекомендаций по использованию хранилища высокой доступных NFS SUSE: [высокодоступное хранилище NFS с DRBD и Pacemaker](https://www.suse.com/documentation/sle-ha-12/book_sleha_techguides/data/art_ha_quick_nfs.html).

2. Проверьте, что SQL Server успешно начинается новый путь к файлу. Для этого на каждом узле. На этом этапе только один узел должен запустить SQL Server за раз. Они оба невозможна, в то же время, так как они оба попытается получить доступ к файлам данных одновременно (Чтобы избежать случайного запуск SQL Server на обоих узлах, убедитесь, что ресурс не подключен дважды с различными узлами с помощью ресурса кластера файловой системы). Следующие команды запуска SQL Server, проверьте состояние и затем остановить SQL Server.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    sudo systemctl stop mssql-server
    ```

На этом этапе оба экземпляра SQL Server настроены для запуска с файлами базы данных в общем хранилище. Следующим шагом является настройка SQL Server для Pacemaker. 

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

## <a name="configure-the-cluster-resources-for-sql-server"></a>Настройте кластерные ресурсы для SQL Server

Ниже объясняется, как настроить ресурс кластера для SQL Server. Существует два параметра, которые нужно настроить.

- **Имя ресурса SQL Server**: имя кластеризованного ресурса SQL Server. 
- **Значение времени ожидания**: значение времени ожидания — это количество времени, которое кластера ожидает, пока ресурс будет подключен к сети. Для SQL Server, это время, когда предполагается, что SQL Server, чтобы перевести `master` базы данных в сети. 

Обновите значения из следующий сценарий для вашей среды. Запустите на одном узле, настройки и запуска кластерной службы.

```bash
sudo crm configure
primitive <sqlServerResourceName> ocf:mssql:fci op start timeout=<timeout_in_seconds>
colocation <constraintName> inf: <virtualIPResourceName> <sqlServerResourceName>
show
commit
exit
```

Например следующий скрипт создает ресурс кластеризованный SQL Server с именем mssqlha. 

```bash
sudo crm configure
primitive mssqlha ocf:mssql:fci op start timeout=60s
colocation admin_addr_mssqlha inf: admin_addr mssqlha
show
commit
exit
```

После подтверждения конфигурации SQL Server запускается на том же узле, виртуальный IP-адрес. 

Дополнительные сведения см. в разделе [Настройка и управление ресурсами кластера (командной строки)](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.manual_config). 

### <a name="verify-that-sql-server-is-started"></a>Убедитесь, что SQL Server запущена. 

Чтобы проверить, что SQL Server запущена, запустите **состояние crm** команды:

```bash
crm status
```

Приведенных ниже примерах показаны результаты, когда Pacemaker успешно запущена как кластеризованный ресурс. 
```
2 nodes configured
2 resources configured

Online: [ SLES1 SLES2 ]

Full list of resources:

 admin_addr     (ocf::heartbeat:IPaddr2):       Started SLES1
 mssqlha        (ocf::mssql:fci):       Started SLES1
```

## <a name="managing-cluster-resources"></a>Управление кластерными ресурсами

Управление ресурсами кластера, см. в следующем разделе SUSE: [управление ресурсами кластера](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.config.crm )

### <a name="manual-failover"></a>Отработка отказа вручную

Несмотря на то, что ресурсы настроены автоматически отработки отказа (или миграция) на другие узлы кластера в случае сбоя оборудования или программного обеспечения, можно также вручную переместить ресурс в другой узел в кластере, с помощью Pacemaker графического пользовательского интерфейса или командной строки . 

Используйте команду migrate для выполнения этой задачи. Например для переноса ресурса SQL имена узлов кластера SLES2 выполните: 

```bash
crm resource
migrate mssqlha SLES2
```

## <a name="additional-resources"></a>Дополнительные ресурсы

[Расширение высокого уровня доступности в Linux Enterprise SUSE — руководство по администрированию](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html) 
