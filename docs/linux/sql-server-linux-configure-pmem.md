---
title: Настройка энергонезависимой памяти (PMEM) для SQL Server на Linux
description: В этой статье представлено пошаговое руководство по настройке PMEM в Linux.
ms.custom: seo-lt-2019
author: briancarrig
ms.author: brcarrig
ms.reviewer: vanto
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 0b5f86dac62c371a9e4dda607cbd9ec7533a187a
ms.sourcegitcommit: 035ad9197cb9799852ed705432740ad52e0a256d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/31/2019
ms.locfileid: "75558619"
---
# <a name="how-to-configure-persistent-memory-pmem-for-sql-server-on-linux"></a>Настройка энергонезависимой памяти (PMEM) для SQL Server на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В это статье описывается настройка энергонезависимой памяти (PMEM) для SQL Server на Linux. Поддержка PMEM в Linux появилась в версии SQL Server 2019.

## <a name="overview"></a>Обзор

В SQL Server 2016 появилась поддержка энергонезависимых модулей DIMM, а также оптимизация под названием [Кэширование заключительного фрагмента журнала в NVDIMM]( https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/). Эти оптимизации снижают количество операций, необходимых для фиксации буфера журнала в энергонезависимом хранилище. При этом используется прямой доступ Windows Server к устройству энергонезависимой памяти в режиме DAX.

В версии SQL Server 2019 добавлена поддержка устройств энергонезависимой памяти (PMEM) для Linux и предоставляется полноценный компонент паравиртуализации для файлов данных и журналов транзакций, размещенных в PMEM. Паравиртуализация — это способ доступа к устройству хранения данных с помощью эффективных операций `memcpy()` в пространстве пользователя. Вместо обращения через файловую систему и стек хранилища SQL Server использует поддержку DAX в Linux для передачи данных на устройства напрямую, что приводит к сокращению задержки.

## <a name="enable-enlightenment-of-database-files"></a>Включение компонента паравиртуализации для файлов базы данных
Чтобы включить компонент паравиртуализации для файлов базы данных в SQL Server на Linux, выполните указанные ниже действия.

1. Настройте устройства.

  В Linux используйте служебную программу `ndctl`.

  - Установите `ndctl`, чтобы настроить устройство PMEM. Его можно найти [здесь](https://docs.pmem.io/getting-started-guide/installing-ndctl).
  - Используйте [ndctl], чтобы создать пространство имен.

  ```bash 
  ndctl create-namespace -f -e namespace0.0 --mode=fsdax* --map=mem
  ```

  >[!NOTE]
  >Для версии `ndctl` ниже версии 59 используйте `--mode=memory`.

  Проверьте пространство имен с помощью `ndctl`. Пример выходных данных:

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

    Пример с использованием XFS

    ```bash
    mkfs.xfs -f /dev/pmem0
    mount -o dax,noatime /dev/pmem0 /mnt/dax
    xfs_io -c "extsize 2m" /mnt/dax
    ```

    Пример с использованием EXT4

    ```bash
    mkfs.ext4 -b 4096 -E stride=512 -F /dev/pmem0
    mount -o dax,noatime /dev/pmem0 /mnt/dax
    ```

  После настройки устройства с помощью ndctl, его форматирования и подключения можно поместить в него файлы базы данных. Кроме того, можно создать новую базу данных. 

1. Так как устройства PMEM поддерживают O_DIRECT, включите флаг трассировки 3979, чтобы отключить механизм принудительной записи на диск. Этот флаг трассировки устанавливается при запуске, поэтому его необходимо включить с помощью служебной программы mssql-conf. Обратите внимание, что это изменение конфигурации применяется на уровне сервера и данный флаг трассировки не следует использовать, если имеются несовместимые с O_DIRECT устройства, которым требуется механизм принудительной записи на диск для обеспечения целостности данных. Дополнительные сведения см. в разделе https://support.microsoft.com/help/4131496/enable-forced-flush-mechanism-in-sql-server-2017-on-linux.

1. Перезапуск SQL Server.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения об SQL Server на Linux см. в статье [SQL Server на Linux](sql-server-linux-overview.md).
