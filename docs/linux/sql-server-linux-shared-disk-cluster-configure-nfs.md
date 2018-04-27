---
title: Настройка отказоустойчивого кластера экземпляра хранилища NFS - SQL Server для Linux | Документы Microsoft
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: 3c17fc54cf181bbac1fee61ddc52cef034c91f02
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="configure-failover-cluster-instance---nfs---sql-server-on-linux"></a>Настроить экземпляр отказоустойчивого кластера — NFS - SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается настройка хранилища NFS для экземпляра отказоустойчивого кластера (FCI) в Linux. 

NFS или сетевой файловой системы является распространенным методом совместное использование дисков в системе Linux, но не один Windows. Аналогично iSCSI NFS можно настроить на сервере или какой-то устройство или устройство хранения при условии, что он удовлетворяет требованиям для SQL Server хранилища.

## <a name="important-nfs-server-information"></a>Важные сведения о сервере NFS

Источник размещение NFS (сервера под управлением Linux или что-нибудь другое) должен соответствовать с помощью/4.2 или более поздней версии. Более ранних версий не будет работать с SQL Server в Linux.

При настройке папки для совместного использования на NFS-сервер, убедитесь, что они следуют эти рекомендации Общие параметры:
- `rw` Чтобы убедиться, что папка может быть считываются и записываются в
- `sync` Чтобы обеспечить гарантированную запись в папку
- Не используйте `no_root_squash` в качестве альтернативы; она считается угрозу безопасности
- Убедитесь, что папка имеет полные права (777) применения

Убедитесь, что стандартов безопасности применяются для доступа к. При настройке папки, убедитесь, что только серверы, участвующие в отказоустойчивом кластере должны увидеть папки NFS. Пример измененного /etc/exports на решение на основе Linux NFS, показано ниже где ограничиваются FCIN1 и FCIN2 папке.

![05 nfsacl][1]

## <a name="instructions"></a>Instructions

1. Выберите один из серверов, которые будут участвовать в конфигурации отказоустойчивого Кластера. Неважно, какой из них. 

2. Проверьте, что сервер может просматривать mount(s) NFS-сервера.

    ```bash
    sudo showmount -e <IPAddressOfNFSServer>
    ```

    \<IPAddressOfNFSServer > — IP-адрес сервера NFS, который планируется использовать.

3. Для системных баз данных или все данные, хранящиеся в расположении данных по умолчанию выполните следующие действия. В противном случае перейдите к шагу 4.
 
   * Убедитесь, что SQL Server остановлена на сервере, вы работаете.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
   * Переключитесь в полностью быть суперпользователем. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    sudo -i
    ```

   * Переключатель — mssql пользователя. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    su mssql
    ```

   * Создайте временный каталог для хранения данных SQL Server и файлы журнала. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    mkdir <TempDir>
    ```

    \<TempDir > — имя папки. В следующем примере создается папка с именем /var/opt/mssql/tmp.

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   * Скопируйте файлы данных и журналов SQL Server во временный каталог. Вы не получите любое подтверждение в случае успешного выполнения.
    
    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > — имя папки из предыдущего шага.

   * Убедитесь, что файлы находятся в каталоге.

    ```bash
    ls TempDir
    ```

    \<TempDir > — имя каталога, от шагу d.

   * Удалите файлы из существующего каталога данных SQL Server. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    rm – f /var/opt/mssql/data/*
    ```

   * Убедитесь, что файлы были удалены. 

    ```bash
    ls /var/opt/mssql/data
    ```
    
   * Наберите exit, чтобы вернуться к привилегированного пользователя.

   * Подключите общего ресурса NFS в папке данных SQL Server. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > — IP-адрес сервера NFS, который будет использоваться 

    \<FolderOnNFSServer > — имя общего ресурса NFS. Следующий пример синтаксиса соответствует сведениям NFS из шага 2.

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

   * Проверьте подключения прошла успешно, выполнив подключения без ключей.

    ```bash
    mount
    ```

    ![10 mountnoswitches][2]

   * Переключитесь в mssql пользователя. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    su mssql
    ```

   * Скопируйте файлы из /var/opt/mssql/data временный каталог. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssqldata
    ```

   * Убедитесь, что файлы существуют.

    ```bash
    ls /var/opt/mssql/data
    ```

   * Введите exit не является mssql 
    
   * Введите exit не является корневой

   * Запустите SQL Server. Если все, что был правильно скопирован и обеспечения безопасности, SQL Server должен показывать начала работы.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
    
   * Создайте базу данных для проверки правильности настройки безопасности. В следующем примере показано, выполняется через Transact-SQL; Это можно сделать через среду SSMS.
 
    ![CreateTestdatabase][3]

   * Остановка SQL Server и убедитесь, что завершение работы.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   * При создании не любые другие подключение NFS, отключите общую папку. Если вы являетесь, не отключить.

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > — IP-адрес сервера NFS, который будет использоваться

    \<FolderOnNFSServer > — имя общего ресурса NFS

    \<FolderMountedIn > — Папка, созданные на предыдущем шаге. 

4. Для выполнения задач, кроме системных баз данных пользовательских баз данных или создание резервных копий выполните следующие действия. Если только расположение по умолчанию, перейдите к шагу 5.

   * Параметр, добавляемый суперпользователя. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    sudo -i
    ```

   * Создайте папку, которая будет использоваться SQL Server. 

    ```bash
    mkdir <FolderName>
    ```

    \<Имя папки > — имя папки. Полный путь к папке должен быть указан не в надлежащем расположении if. В следующем примере создается папка с именем /var/opt/mssql/userdata.

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   * Подключите общего ресурса NFS в папку, созданную на предыдущем шаге. Вы не получите любое подтверждение в случае успешного выполнения.

    ```bash
    Mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn> -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > — IP-адрес сервера NFS, который будет использоваться

    \<FolderOnNFSServer > — имя общего ресурса NFS

    \<FolderToMountIn > — Папка, созданные на предыдущем шаге. Ниже приведен пример. 

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci2 /var/opt/mssql/userdata -o nfsvers=4.2,timeo=14,intr
    ```

   * Проверьте подключения прошла успешно, выполнив подключения без ключей.
  
   * Введите exit для перестанет быть суперпользователем.

   * Чтобы проверить, создайте базу данных в этой папке. В следующем примере программы sqlcmd для создания базы данных, переходить в контекст, проверьте файлы существуют на уровне операционной системы, а затем удаляет временное расположение. Можно использовать среду SSMS.

    ![15 createtestdatabase][4]
 
   * Отключение общего ресурса 

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > — IP-адрес сервера NFS, который будет использоваться
    
    \<FolderOnNFSServer > — имя общего ресурса NFS

    \<FolderMountedIn > — Папка, созданные на предыдущем шаге. Ниже приведен пример. 
 
5. Повторите шаги на другие узлы.


## <a name="next-steps"></a>Следующие шаги

[Настроить экземпляр отказоустойчивого кластера — SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/05-nfsacl.png
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/10-mountnoswitches.png
[3]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/20-createtestdatabase.png
[4]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/15-createtestdatabase.png
