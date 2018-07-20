---
title: Настройка отказоустойчивого кластера хранилища экземпляра NFS - SQL Server в Linux | Документация Майкрософт
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: da4499433e89161c6204082d43d1e2c65bbd0503
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084316"
---
# <a name="configure-failover-cluster-instance---nfs---sql-server-on-linux"></a>Настроить экземпляр отказоустойчивого кластера — NFS - сервера SQL в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье объясняется, как настроить хранилище NFS для экземпляра отказоустойчивого кластера (FCI) в Linux. 

NFS или сетевой файловой системы, — это общий метод для совместного использования дисков в мире Linux, но не Windows, один. Как и для iSCSI, NFS можно настроить на сервере или какую-либо устройство или устройство хранения до тех пор, пока он соответствует требованиям хранилища для SQL Server.

## <a name="important-nfs-server-information"></a>Важные сведения о сервере NFS

Размещение NFS (сервер Linux или что-то еще) источника должно соответствовать с помощью/4.2 и более поздних версиях. Более ранние версии не будут работать с SQL Server в Linux.

При настройке папки для совместного использования на NFS-сервер, убедитесь, что они соответствуют эти рекомендации Общие параметры:
- `rw` Чтобы убедиться, что папку можно считать данные и записи
- `sync` Чтобы обеспечить гарантированную запись в папку
- Не используйте `no_root_squash` свободен; он считается угрозу безопасности
- Убедитесь, что она содержит полные права (777) применения

Убедитесь, что вашим стандартам безопасности применяются для доступа к. При настройке папки, убедитесь, что только серверы, участвующие в FCI увидите папке NFS. Ниже где папке ограничен FCIN1 и FCIN2 приведен пример измененного /etc/exports на решение для NFS под управлением Linux.

![05-nfsacl][1]

## <a name="instructions"></a>Instructions

1. Выберите один из серверов, которые будут участвовать в конфигурации отказоустойчивого Кластера. Неважно, какой из них. 

2. Проверьте, что сервер можно увидеть mount(s) NFS-сервера.

    ```bash
    sudo showmount -e <IPAddressOfNFSServer>
    ```

    \<IPAddressOfNFSServer > является IP-адрес NFS-сервер, который вы собираетесь использовать.

3. Для системных баз данных или все данные, хранящиеся в расположении данных по умолчанию выполните следующие действия. В противном случае перейдите к шагу 4.
 
   * Убедитесь, что SQL Server остановлена на сервере, которым вы работаете.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
   * Переключиться в режим полностью стать суперпользователем. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    sudo -i
    ```

   * Ключ пользователя mssql. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    su mssql
    ```

   * Создайте временный каталог для хранения данных SQL Server и файлов журнала. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    mkdir <TempDir>
    ```

    \<TempDir > — это имя папки. В следующем примере создается папка с именем /var/opt/mssql/tmp.

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   * Скопируйте файлы данных и журналов SQL Server во временный каталог. Вы не получите любое подтверждение при успешном выполнении.
    
    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > — это имя папки, из предыдущего шага.

   * Убедитесь, что файлы находятся в каталоге.

    ```bash
    ls TempDir
    ```

    \<TempDir > — это имя папки из шагу d.

   * Удалите файлы из существующего каталога данных SQL Server. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    rm – f /var/opt/mssql/data/*
    ```

   * Убедитесь, что файлы были удалены. 

    ```bash
    ls /var/opt/mssql/data
    ```
    
   * Наберите exit, чтобы вернуться к привилегированного пользователя.

   * Подключите общий ресурс NFS в папке данных SQL Server. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > является IP-адрес NFS-сервер, который вы собираетесь использовать 

    \<FolderOnNFSServer > — это имя общего ресурса NFS. Следующий пример синтаксиса соответствуют сведениям NFS из шага 2.

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

   * Проверьте, что подключение успешно, выполнив подключения без ключей.

    ```bash
    mount
    ```

    ![10-mountnoswitches][2]

   * Переключитесь на пользователя mssql. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    su mssql
    ```

   * Скопируйте файлы из /var/opt/mssql/data во временный каталог. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssqldata
    ```

   * Убедитесь, что файлы существуют.

    ```bash
    ls /var/opt/mssql/data
    ```

   * Вход и выход, не является mssql 
    
   * Вход и выход, не является корневой

   * Запустите SQL Server. Если все, что был скопирован правильно, и обеспечения безопасности, SQL Server должна отобразиться как к работе.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
    
   * Создание базы данных для проверки правильности настройки безопасности. В следующем примере показано, что необходимо сделать с помощью Transact-SQL; Это можно сделать с помощью SSMS.
 
    ![CreateTestdatabase][3]

   * Остановка SQL Server и убедитесь, что завершение работы.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   * Если вы не создаете любые другие NFS подключается, отключите общую папку. Если вы являетесь, не отключайте.

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > является IP-адрес NFS-сервер, который вы собираетесь использовать

    \<FolderOnNFSServer > — это имя общего ресурса NFS

    \<FolderMountedIn > — это папки, созданной на предыдущем шаге. 

4. Для таких вещей, кроме системных баз данных, таких как пользовательских баз данных или резервных копий выполните следующие действия. Если только с использованием расположения по умолчанию, переходите к шагу 5.

   * Переключатель, чтобы стать суперпользователем. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    sudo -i
    ```

   * Создайте папку, которая будет использоваться SQL Server. 

    ```bash
    mkdir <FolderName>
    ```

    \<Имя папки > — это имя папки. Полный путь к папке должен быть указан не в надлежащем расположении if. В следующем примере создается папка с именем /var/opt/mssql/userdata.

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   * Подключите общий ресурс NFS в папке, который был создан на предыдущем шаге. Вы не получите любое подтверждение при успешном выполнении.

    ```bash
    Mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn> -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > является IP-адрес NFS-сервер, который вы собираетесь использовать

    \<FolderOnNFSServer > — это имя общего ресурса NFS

    \<FolderToMountIn > — это папки, созданной на предыдущем шаге. Ниже приведен пример. 

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci2 /var/opt/mssql/userdata -o nfsvers=4.2,timeo=14,intr
    ```

   * Проверьте, что подключение успешно, выполнив подключения без ключей.
  
   * Наберите exit больше не суперпользователь.

   * Чтобы проверить, создайте базу данных в этой папке. В следующем примере использует sqlcmd для создания базы данных, переключить контекст на него, проверьте файлы существуют на уровне операционной системы, а затем удаляет во временную папку. Можно использовать SSMS.

    ![15-createtestdatabase][4]
 
   * Отключить общую папку 

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > является IP-адрес NFS-сервер, который вы собираетесь использовать
    
    \<FolderOnNFSServer > — это имя общего ресурса NFS

    \<FolderMountedIn > — это папки, созданной на предыдущем шаге. Ниже приведен пример. 
 
5. Повторите эти действия на другие узлы.


## <a name="next-steps"></a>Следующие шаги

[Настроить экземпляр отказоустойчивого кластера — SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/05-nfsacl.png
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/10-mountnoswitches.png
[3]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/20-createtestdatabase.png
[4]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/15-createtestdatabase.png
