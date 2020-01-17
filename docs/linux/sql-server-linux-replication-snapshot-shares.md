---
title: Настройка общих папок моментальных снимков
titleSuffix: SQL Server on Linux
description: Узнайте, как настроить репликацию общих папок моментальных снимков в SQL Server на Linux.
ms.custom: seo-lt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c5deaf7fbe62b30140f476a37ad096d080e00c49
ms.sourcegitcommit: 035ad9197cb9799852ed705432740ad52e0a256d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/31/2019
ms.locfileid: "75558359"
---
# <a name="configure-replication-snapshot-folder-with-shares"></a>Настройка папки моментальных снимков репликации с общими папками

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Папка моментальных снимков — это каталог, назначенный для совместного использования; агенты, считывающие и записывающие данные в этой папке, должны иметь достаточные разрешения для доступа к ней.

![схема репликации][1]

### <a name="replication-snapshot-folder-share-explained"></a>Описание общей папки для моментальных снимков репликации

Прежде чем обратиться к примерам, давайте рассмотрим, как SQL Server использует общие папки Samba при репликации. Ниже приведен простой пример того, как это работает.

1. Общие папки Samba настроены так, чтобы файлы, записываемые в `/local/path1` агентами репликации на издателе, были видны подписчику.
2. SQL Server настроен для использования путей к общим папкам при настройке издателя на сервере распространения, чтобы все экземпляры обращались к `//share/path`.
3. SQL Server находит локальный путь из `//share/path`, чтобы узнать, где искать файлы.
4. SQL Server осуществляет чтение и запись по локальным путям, поддерживаемым общей папкой Samba.


## <a name="configure-a-samba-share-for-the-snapshot-folder"></a>Настройка общей папки Samba для папки моментальных снимков 

Для доступа к папкам моментальных снимков на других компьютерах агентам репликации потребуется общий каталог между узлами репликации. Например, в репликации транзакций по запросу агент распространения находится на подписчике, в связи с чем требуется доступ к распространителю для получения статей. В этом разделе мы рассмотрим пример настройки общей папки Samba на двух узлах репликации.


## <a name="steps"></a>Шаги

В качестве примера мы настроим папку моментальных снимков на узле 1 (распространителе) для совместного использования с узлом 2 (подписчиком) с помощью Samba. 

### <a name="install-and-start-samba-on-both-machines"></a>Установка и запуск Samba на обоих компьютерах 

В Ubuntu:

```bash
sudo apt-get -y install samba
sudo service smbd restart
```

В RHEL:

```bash
sudo yum install samba
sudo service smb start
sudo service smb status
```

### <a name="on-host-1-distributor-set-up-the-samba-share"></a>На узле 1 (распространитель) — настройка общей папки Samba 

1. Задайте пользователя и пароль для Samba:

  ```bash
  sudo smbpasswd -a mssql 
  ```

1. Измените, `/etc/samba/smb.conf` чтобы включить следующую запись и заполнить поля *share_name* и *path*.
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

### <a name="on-host-2-subscriber--mount-the-samba-share"></a>На узле 2 (подписчик) — подключение общей папки Samba

Измените команду, указав правильные пути, и выполните следующую команду на компьютере 2.

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

### <a name="on-both-hosts--configure-sql-server-on-linux-instances-to-use-snapshot-share"></a>На обоих узлах — настройка экземпляров SQL Server в Linux для использования общей папки моментальных снимков

Добавьте следующий раздел в `mssql.conf` на обоих компьютерах. Используйте общую папку samba для //share/path. В данном примере это будет `//host1/mssql_data`

  ```bash
  [uncmapping]
  //share/path = /local/path/on/hosts/
  ```

  **Пример**

  На узле 1:

  ```bash
  [uncmapping]
  //host1/mssql_data = /local/path/on/hosts/1
  ```

  На узле 2:
  
  ```bash
  [uncmapping]
  //host1/mssql_data = /local/path/on/hosts/2
  ```

### <a name="configuring-publisher-with-shared-paths"></a>Настройка издателя с использованием общих путей

* При настройке репликации используйте путь к общим папкам (например, `//host1/mssql_data`).
* Сопоставьте `//host1/mssql_data` с локальным каталогом и сопоставлением, добавленным в `mssql.conf`.

## <a name="next-steps"></a>Дальнейшие действия

[Основные понятия. Репликация SQL Server в Linux](sql-server-linux-replication.md)

[Хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

[1]: ./media/sql-server-linux-replication-snapshot-shares/image1.png
