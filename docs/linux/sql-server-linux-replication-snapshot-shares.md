---
title: Настройка общих папок моментального снимка репликации SQL Server в Linux
description: В этой статье описывается, как настроить репликацию моментальных снимков папки общих ресурсов SQL Server в Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4091bd6f1a3afcf32431af78ad47089ffc9a1620
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834782"
---
# <a name="configure-replication-snapshot-folder-with-shares"></a>Настройка папки моментальных снимков репликации с помощью общих папок

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Папка моментальных снимков является каталогом, назначенный для совместного использования; агенты, чтение и запись к этой папке должен иметь достаточных разрешений на доступ к нему.

![схема репликации][1]

### <a name="replication-snapshot-folder-share-explained"></a>Общего ресурса папки моментальных снимков репликации описано

Прежде чем примеры давайте подробно рассмотрим как SQL Server использует общие ресурсы samba в репликации. Ниже приведен простой пример того, как это работает.

1. Общие ресурсы Samba настроены, файлы в записываемый `/local/path1` репликации можно увидеть агентов на издателе, подписчике
2. SQL Server настроен для использования путей общей папки, при настройке издателя на сервере распространения таким образом, чтобы рассмотреть все экземпляры `//share/path`
3. SQL Server находит локальный путь из `//share/path` знать, где искать файлы
4. SQL Server операций чтения и записи к локальным путям, поддерживаемый общую папку samba


## <a name="configure-a-samba-share-for-the-snapshot-folder"></a>Настройте общий ресурс samba для папки моментальных снимков 

Агенты репликации, потребуется общий каталог между узлами репликации для доступа к папкам моментальных снимков на других компьютерах. Например в репликации транзакций по запросу, агент распространителя находится на подписчике, что требует доступа к распространителю для статей. В этом разделе мы разберем пример того, как настроить общую папку samba на двух узлах репликации.


## <a name="steps"></a>Шаги

В качестве примера мы настроим папку моментальных снимков на узле 1 (распространитель) совместно с узлом 2 (подписчик) с помощью Samba. 

### <a name="install-and-start-samba-on-both-machines"></a>Установите и запустите Samba на обоих компьютерах 

В Ubuntu:

```bash
sudo apt-get -y install samba
sudo service smbd restart
```

На RHEL:

```bash
sudo yum install samba
sudo service smb start
sudo service smb status
```

### <a name="on-host-1-distributor-set-up-the-samba-share"></a>На узле 1 (распространитель) настройка Samba общую папку 

1. Настройки пользователя и пароль для samba:

  ```bash
  sudo smbpasswd -a mssql 
  ```

1. Изменить `/etc/samba/smb.conf` следующую запись и заполнить *имя_общего_ресурса* и *путь* поля
 ```bash
  <[share_name]>
  path = </local/path/on/host/1>
  writable = yes
  create mask = 770
  directory mask 
  valid users = mssql 
  ```

  **Пример**

  ```bash
  [mssql_data]    <- Name of the shared directory
  path = /var/opt/mssql/repldata <- location of directory we wish to share
  writable = yes  <- determines if the share is writable from other hosts
  create mask = 770  <- Linux permissions for files created 
  directory mask = 770 <- Linux permissions for directories created
  valid users = mssql   <- list of users who can login to this share
  ```

### <a name="on-host-2-subscriber--mount-the-samba-share"></a>На узле 2 (подписчик) подключите общий ресурс Samba

Изменить команду с правильные пути и выполните следующую команду на компьютере 2:

  ```bash
  sudo mount //<name_of_host_1>/<share_name> </local/path/on/host/2> -o user=mssql,uid=mssql,gid=mssql
  ```

  **Пример**

  ```bash
  mount //host1/mssql_data /var/opt/mssql/repldata_shared -o user=mssql,uid=mssql,gid=mssql

  user=mssql <- sets the login name for samba
  uid=mssql   <- makes the mssql user as the owner of the mounted directory
  gid=mssql   <- sets the mssql group as the owner of the mounted directory
  ```

### <a name="on-both-hosts--configure-sql-server-on-linux-instances-to-use-snapshot-share"></a>Как узлы настроить SQL Server на Linux экземпляров для использования моментальных снимков

Добавьте следующий раздел, чтобы `mssql.conf` на обоих компьютерах. Использовать везде, где samba общего ресурса для / / / путь к общей папке. В этом примере будет `//host1/mssql_data`

  ```bash
  [uncmapping]
  //share/path = /local/path/on/hosts/
  ```

  **Пример**

  На узле1:

  ```bash
  [uncmapping]
  //host1/mssql_data = /local/path/on/hosts/1
  ```

  На узле2:
  
  ```bash
  [uncmapping]
  //host1/mssql_data = /local/path/on/hosts/2
  ```

### <a name="configuring-publisher-with-shared-paths"></a>Настройка издателя с путями Shared

* При настройке репликации, используйте путь (например, общие папки `//host1/mssql_data`
* Карта `//host1/mssql_data` локальный каталог и добавить сопоставление `mssql.conf`.

## <a name="next-steps"></a>Следующие шаги

[Основные понятия: Репликация SQL Server в Linux](sql-server-linux-replication.md)

[Хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

[1]: ./media/sql-server-linux-replication-snapshot-shares/image1.png
