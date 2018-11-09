---
title: Настройка постоянной памяти (PMEM) для SQL Server в Linux | Документация Майкрософт
description: В этой статье приведены пошаговые инструкции для настройки PMEM на Linux.
author: DBArgenis
ms.author: argenisf
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 07f068a24c60fe82c299387fe859f07296f21df8
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269438"
---
# <a name="how-to-configure-persistent-memory-pmem-for-sql-server-on-linux"></a>Настройка постоянной памяти (PMEM) для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается настройка постоянной памяти (PMEM) для SQL Server в Linux. В предварительной версии SQL Server 2019 появилась поддержка PMEM в Linux.

## <a name="overview"></a>Обзор

SQL Server 2016 добавлена поддержка для долговременного DIMM и оптимизации называется [заключительного фрагмента журнала, кэширование на NVDIMM]( https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/). Эти оптимизации уменьшенное количество операций, необходимых для усиления защиты буфера журнала в постоянное хранилище. Этот вариант использует Windows Server прямой доступ к постоянной памяти устройства в режим DAX.

Предварительная версия SQL Server 2019 расширяет поддержку для постоянной памяти устройства (PMEM) для Linux, предоставляя полный просвещения из данных и файлы журнала транзакций на PMEM. Просвещение ссылается на метод доступа к запоминающему устройству с помощью эффективного пространства пользователя `memcpy()` операций. Вместо того, чтобы переход через стек системы и хранилища файлов SQL Server использует возможности DAX в Linux, чтобы напрямую помещения данных в устройства, что позволяет снизить задержку.

## <a name="enable-enlightenment-of-database-files"></a>Включить просвещения файлов базы данных
Чтобы включить просвещения файлов базы данных в SQL Server в Linux, выполните следующие действия.

1. Настройка устройств.

  В Linux, используйте `ndctl` служебной программы.

  - Установка `ndctl` для настройки устройства PMEM. Его можно найти [здесь](https://docs.pmem.io/getting-started-guide/installing-ndctl).
  - Используйте [ndctl], создание пространства имен.

  ```bash 
  ndctl create-namespace -f -e namespace0.0 --mode=fsdax* -–map=mem
  ```

  >[!NOTE]
  >Если вы используете `ndctl` версии ниже, чем 59, используйте `--mode=memory`.

  Используйте `ndctl` проверяемое пространство имен. Пример выходных данных следующим образом:

```bash
ndctl list
[
  {
    "dev":"namespace0.0",
    "mode":"memory",
    "size":1099511627776,
    "blockdev":"pmem0",
    "numa_node":0
  }
]
```

  - Создание и подключение устройства PMEM

    Например для файловой системы XFS

    ```bash
    mkfs.xfs -f /dev/pmem0
    mount –o dax,noatime /dev/pmem0 /mnt/dax
    xfs_io -c "extsize 2m" /mnt/dax
    ```

    Например с помощью EXT4

    ```bash
    mkfs.ext4 -b 4096 -E stride=512 -F /dev/pmem0
    mount –o dax,noatime /dev/pmem0 /mnt/dax
    ```

  Когда устройство будет настроено ndctl, отформатирован и подключен, файлы базы данных можно разместить в нем. Можно также создать новую базу данных 

1. Включите просвещения файл базы данных SQL Server с помощью флага трассировки 3979. Этот флаг трассировки — это флаг трассировки при запуске и таким образом, необходимо включить с помощью служебной программы mssql-conf.

1. Перезапуск SQL Server.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о SQL Server в Linux, см. в разделе [SQL Server в Linux](sql-server-linux-overview.md).
