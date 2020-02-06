---
title: Настройка экземпляра отказоустойчивого кластера хранилища NFS — SQL Server на Linux
description: Узнайте, как настроить экземпляр отказоустойчивого кластера с помощью хранилища NFS для SQL Server для Linux.
ms.custom: seo-lt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 35f6dc79756c192419dbe3a8962d5dcdfeea8aef
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75558339"
---
# <a name="configure-failover-cluster-instance---nfs---sql-server-on-linux"></a>Настройка экземпляра отказоустойчивого кластера (NFS) — SQL Server на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается, как настроить хранилище NFS для экземпляра отказоустойчивого кластера в Linux. 

NFS (Network File System, сетевая файловая система) — это распространенный способ предоставления общего доступа к дискам в Linux, но не в Windows. Так же как и iSCSI, NFS можно настроить на сервере, устройстве или в единице хранения, если они отвечают требованиям к хранилищу для SQL Server.

## <a name="important-nfs-server-information"></a>Важные сведения о сервере NFS

Источник размещения NFS (сервер Linux или другое устройство) должен использовать версию 4.2 или более позднюю либо быть совместимым с ней. Более ранние версии не работают с SQL Server на Linux.

При настройке общего доступа к папкам на сервере NFS необходимо использовать следующие рекомендованные параметры:
- `rw` для обеспечения возможности считывания из папки и записи в нее;
- `sync` для обеспечения гарантированной записи в папку;
- не используйте параметр `no_root_squash`, он считается небезопасным;
- к папке необходимо применить полные права (777).

Примените стандарты безопасного доступа. При настройке папки NFS доступ к ней должны иметь только серверы, относящиеся к экземпляру отказоустойчивого кластера. Ниже приведен пример папки /etc/exports в решении NFS на базе Linux, доступ к которой имеют только серверы FCIN1 и FCIN2.

![05-nfsacl][1]

## <a name="instructions"></a>Instructions

1. Выберите один из серверов, которые будут включены в конфигурацию экземпляра отказоустойчивого кластера. Какой именно — не имеет значения. 

2. Проверьте, доступны ли серверу подключенные ресурсы на сервере NFS.

    ```bash
    sudo showmount -e <IPAddressOfNFSServer>
    ```

    \<IPAddressOfNFSServer> — это IP-адрес NFS-сервера, который будет использоваться.

3. Для системных баз данных или других объектов, хранящихся в расположении данных по умолчанию, выполните указанные ниже действия. В противном случае перейдите к шагу 4.
 
   * Убедитесь в том, что SQL Server остановлен на сервере, на котором вы работаете.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
   * Перейдите в режим суперпользователя. В случае успешного действия подтверждение не выводится.

    ```bash
    sudo -i
    ```

   * Переключитесь на пользователя mssql. В случае успешного действия подтверждение не выводится.

    ```bash
    su mssql
    ```

   * Создайте временный каталог для хранения данных и файлов журналов SQL Server. В случае успешного действия подтверждение не выводится.

    ```bash
    mkdir <TempDir>
    ```

    \<TempDir> — это имя папки. В приведенном ниже примере создается папка /var/opt/mssql/tmp.

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   * Скопируйте данные и файлы журналов SQL Server во временный каталог. В случае успешного действия подтверждение не выводится.
    
    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir> — это имя папки из предыдущего шага.

   * Проверьте наличие файлов в папке.

    ```bash
    ls TempDir
    ```

    \<TempDir> — это имя папки из шага d.

   * Удалите файлы из существующего каталога данных SQL Server. В случае успешного действия подтверждение не выводится.

    ```bash
    rm - f /var/opt/mssql/data/*
    ```

   * Проверьте, были ли файлы удалены. 

    ```bash
    ls /var/opt/mssql/data
    ```
    
   * Введите exit, чтобы переключиться на привилегированного пользователя.

   * Подключите общую папку NFS в папке данных SQL Server. В случае успешного действия подтверждение не выводится.

    ```bash
    mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer> — это IP-адрес NFS-сервера, который будет использоваться. 

    \<FolderOnNFSServer> — это имя общей папки NFS. Приведенный ниже пример синтаксиса соответствует сведениям об NFS из шага 2.

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

   * Проверьте, было ли подключение выполнено успешно, с помощью команды mount без параметров.

    ```bash
    mount
    ```

    ![10-mountnoswitches][2]

   * Переключитесь на пользователя mssql. В случае успешного действия подтверждение не выводится.

    ```bash
    su mssql
    ```

   * Скопируйте файлы из временного каталога /var/opt/mssql/data. В случае успешного действия подтверждение не выводится.

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssqldata
    ```

   * Проверьте наличие файлов.

    ```bash
    ls /var/opt/mssql/data
    ```

   * Введите exit, чтобы выйти из учетной записи mssql. 
    
   * Введите exit, чтобы выйти из учетной записи привилегированного пользователя.

   * Запустите SQL Server. Если все данные были скопированы и параметры безопасности применены правильно, сервер SQL Server должен отобразиться как запущенный.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
    
   * Создайте базу данных, чтобы проверить правильность настройки безопасности. В приведенном ниже примере это делается с помощью Transact-SQL, но можно использовать и SSMS.
 
    ![CreateTestdatabase][3]

   * Остановите сервер SQL Server и убедитесь в том, что его работа прекращена.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   * Если вы не будете создавать другие подключенные ресурсы NFS, отключите общую папку. В противном случае не отключайте ее.

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer> — это IP-адрес NFS-сервера, который будет использоваться.

    \<FolderOnNFSServer> — это имя общей папки NFS.

    \<FolderMountedIn> — это папка, созданная в предыдущем шаге. 

4. Для объектов, отличных от системных баз данных, например пользовательских баз данных или резервных копий, выполните указанные ниже действия. Если используется только расположение по умолчанию, перейдите к шагу 5.

   * Перейдите в режим суперпользователя. В случае успешного действия подтверждение не выводится.

    ```bash
    sudo -i
    ```

   * Создайте папку, которая будет использоваться сервером SQL Server. 

    ```bash
    mkdir <FolderName>
    ```

    \<FolderName> — это имя папки. Если папка находится в другом месте, необходимо указать полный путь к ней. В приведенном ниже примере создается папка /var/opt/mssql/userdata.

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   * Подключите общую папку NFS в папке, созданной в предыдущем шаге. В случае успешного действия подтверждение не выводится.

    ```bash
    Mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn> -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer> — это IP-адрес NFS-сервера, который будет использоваться.

    \<FolderOnNFSServer> — это имя общей папки NFS.

    \<FolderToMountIn> — это папка, созданная в предыдущем шаге. Ниже приведен пример. 

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci2 /var/opt/mssql/userdata -o nfsvers=4.2,timeo=14,intr
    ```

   * Проверьте, было ли подключение выполнено успешно, с помощью команды mount без параметров.
  
   * Введите exit, чтобы выйти из режима суперпользователя.

   * Создайте в этой папке базу данных для тестирования. В приведенном ниже примере создается база данных с помощью sqlcmd, переключается контекст, проверяется наличие файлов на уровне ОС, а затем временная папка удаляется. Можно также использовать SSMS.

    ![15-createtestdatabase][4]
 
   * Отключение общей папки 

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer> — это IP-адрес NFS-сервера, который будет использоваться.
    
    \<FolderOnNFSServer> — это имя общей папки NFS.

    \<FolderMountedIn> — это папка, созданная в предыдущем шаге. Ниже приведен пример. 
 
5. Повторите эти действия на других узлах.


## <a name="next-steps"></a>Дальнейшие действия

[Настройка экземпляра отказоустойчивого кластера — SQL Server на Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/05-nfsacl.png
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/10-mountnoswitches.png
[3]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/20-createtestdatabase.png
[4]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/15-createtestdatabase.png
