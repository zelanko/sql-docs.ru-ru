---
title: Разрешения уровней HDFS для кластеров больших данных SQL Server
titleSuffix: Manage HDFS tiering permissions for SQL Server Big Data Clusters
description: Управляйте безопасностью для уровней HDFS в кластерах больших данных SQL Server, такой как разрешения в других системах на основе Linux.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8112c5c6b69b83986bdf10c6b73d72afba4d9cb6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764062"
---
# <a name="manage-hdfs-permissions-for-big-data-clusters-2019"></a>Управление разрешениями HDFS для [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

HDFS как файловая система подобна файловым системам на базе Linux, в которых в качестве модели разрешений для файлов используется POSIX. Помимо традиционной модели разрешений POSIX, HDFS также поддерживает списки управления доступом POSIX (ACL). Дополнительные сведения см. в [статье Apache Hadoop об ACL](https://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-hdfs/HdfsPermissionsGuide.html#ACLs_.28Access_Control_Lists.29).

В следующих разделах приведены примеры использования CLI `azdata` для управления разрешениями HDFS для файлов и каталогов.

## <a name="prerequisites"></a>предварительные требования

- [Развернутый кластер больших данных](deployment-guidance.md)
- [Средства работы с большими данными](deploy-big-data-tools.md)
  
## <a name="hdfs-shell"></a>Оболочка HDFS

Функция оболочки `hdfs` в `azdata` позволяет выдавать команды непосредственно в оболочке для управления разрешениями HDFS для файлов и каталогов. Базовый механизм использует вызовы WebHDFS для выдачи команд.

Следующая команда открывает оболочку.

```bash
azdata bdc hdfs shell
```

Чтобы вызвать справку по оболочке `hdfs` и понять, как выдавать команды, выполните в запущенной оболочке следующую команду.

```bash
[hdfs] ?
```

В следующем примере показано, как создать каталог, получить список каталогов, изменить разрешения для каталога, а также предоставить пользователю с именем `bob` доступ на чтение, запись и выполнение в каталоге `sales`.

```bash
[hdfs] mkdir sales
[hdfs] ls
rwxr-xr-x  hdfs bdcadmins        0 Oct 09 18:02 system/
rwxrwxr-x admin bdcadmins        0 Oct 10 16:47 sales/
--xrwxrwxrwx  hdfs bdcadmins        0 Oct 09 18:03 tmp/
rwxrwxrwx  hdfs bdcadmins        0 Oct 09 17:59 user/

[hdfs] acl modify  '/sales/' 'user:bob:rwx'
acl modify: Change completed.
[hdfs] acl status  '/sales/'
{
  `AclStatus`: {
    `entries`: [
      `user:bob:rwx`,
      `group::r-x`
    ],
    `group`: `bdcadmins`,
    `owner`: `admin`,
    `permission`: `775`,
    `stickyBit`: false
  }
}
```

## <a name="create-a-directory-in-hdfs-using-azdata"></a>Создание каталога в HDFS с помощью `azdata`

В следующем примере показано создание каталога с именем `data` по пути `/sales`.

```bash
azdata bdc hdfs mkdir --path '/sales/data'
```

## <a name="change-owner-of-a-directory-or-file"></a>Изменение владельца каталога или файла

В следующем примере показано, как изменить пользователя-владельца каталога `data` в HDFS и сделать владельцами пользователя *`alice`* и группу *`salesgroup`* . Чтобы изменить владельца, необходимо быть владельцем.

```bash
azdata bdc hdfs chown --owner alice --group 'salesgroup' --path '/sales/data'
```

## <a name="change-permissions-of-a-file-or-directory-with-chmod"></a>Изменение разрешений для файла или каталога с помощью `chmod`

Используйте `chmod`, чтобы изменить разрешения для файлов и каталогов (для владельца, группы-владельца и других). Дополнительные сведения см. в статье [об изменении разрешений в файловой системе Linux](https://www.lifewire.com/uses-of-command-chmod-2201064). В HDFS используется тот же шаблон. Пример:

```bash
azdata bdc hdfs chmod --permission 750 --path /sales/data
```

```bash
azdata bdc hdfs chmod --permission 775 --path /sales/data/file.txt
```

## <a name="set-sticky-bit-on-directories"></a>Установка бита закрепления в каталогах

Установка бита закрепления в каталогах помогает предотвратить непреднамеренное удаление или перемещение файлов. Бит закрепления разрешает удалять или перемещать файл только суперпользователю, владельцу каталога или владельцу файла. Эта настройка не затрагивает сами файлы. В приведенном ниже примере задается бит закрепления для каталога `users` путем добавления к разрешениям префикса `1`.

```bash
azdata bdc hdfs chmod --path /sales/users --permission 1750
```

## <a name="setting-acls-on-files-and-directories"></a>Настройка списков управления доступом для файлов и каталогов

Чтобы задать списки управления доступом для файлов и каталогов HDFS, используйте команды `azdata`.

В следующем примере показано, как настроить списки управления доступом для каталога и предоставить пользователю с именем *`tom`* доступ на чтение, запись и выполнение в каталоге *`data`* . 

> [!NOTE]
> При использовании команды `set` убедитесь, что вы предоставляете полную спецификацию ACL, включая спецификацию ACL для пользователя-владельца, группы-владельца и других.

```bash
azdata bdc hdfs acl set --path '/sales' --aclspec  'user::rw-,user:tom:rwx,group::rw-,other::rw-'
```

## <a name="default-acl-on-directories"></a>ACL по умолчанию для каталогов

ACL по умолчанию позволяет вложенным каталогам наследовать разрешения от родительского каталога. ACL по умолчанию могут иметь только каталоги. При создании нового файла или вложенного каталога он автоматически наследует ACL по умолчанию своего родительского элемента в качестве собственного списка управления доступом. Таким образом, ACL по умолчанию будет наследоваться все глубже и глубже по мере создания новых вложенных каталогов.

Ниже приведен пример установки ACL по умолчанию с помощью azdata.

```bash
azdata bdc hdfs acl set --path '/sale' --aclspec  'user::rw-,user:tom:rwx,group::rw-,other::rw-,default:group::rw-,default:user::rw-,default:other::rw-'
```

## <a name="next-steps"></a>Дальнейшие действия

- [Справочник `azdata`](reference-azdata.md)

- [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
