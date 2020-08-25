---
title: Настройка энергонезависимой памяти (PMEM)
description: Сведения о том, как настроить энергонезависимую память (PMEM) для SQL Server в Linux, а также о том, как создать пространства имен для устройств PMEM.
ms.custom: seo-lt-2019
author: briancarrig
ms.author: brcarrig
ms.date: 10/31/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 146ab5788e29045a55e6251be01e061f52d7bbb8
ms.sourcegitcommit: 3ea082c778f6771b17d90fb597680ed334d3e0ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/11/2020
ms.locfileid: "88088941"
---
# <a name="configure-persistent-memory-pmem-for-sql-server-on-linux"></a>Настройка энергонезависимой памяти (PMEM) для SQL Server на Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

В этой статье описывается настройка энергонезависимой памяти (PMEM) для [!INCLUDE[sqlv15](../includes/sssqlv15-md.md)] на Linux.

## <a name="overview"></a>Обзор

[!INCLUDE[sqlv15](../includes/sssqlv15-md.md)] имеет ряд функций в памяти, использующих энергонезависимую память. В этом документе рассматриваются шаги, необходимые для настройки энергонезависимой памяти для SQL Server на Linux.

> [!NOTE]
> Термин _просвещение_ был введен для того, чтобы описать понятие работы с файловой системой, поддерживающей энергонезависимую память. Прямой доступ к файловой системе из приложений в пользовательском пространстве упрощается с помощью сопоставления памяти (`mmap()`). При создании сопоставления памяти для файла приложение может выдавать инструкции по загрузке или хранению, полностью обходя стек ввода-вывода. Это "просвещенный" метод доступа к файлам с точки зрения приложения расширения узла (оно является "черным ящиком", который позволяет SQLPAL взаимодействовать с ОС Windows или Linux).

## <a name="create-namespaces-for-pmem-devices"></a>Создание пространств имен для устройств PMEM

### <a name="configure-the-devices"></a>Настройка устройств

В Linux используйте служебную программу `ndctl`.

- Установите `ndctl`, чтобы настроить устройство PMEM. Его можно найти [здесь](https://docs.pmem.io/getting-started-guide/installing-ndctl).
- Используйте `ndctl` для создания пространства имен. Пространства имен чередуются между микросхемами NVDIMM в PMEM и могут предоставлять различные типы доступа пользовательского пространства к областям памяти на устройстве. `fsdax` используется для SQL Server по умолчанию и в качестве предпочтительного режима.

```bash 
ndctl create-namespace -f -e namespace0.0 --mode=fsdax* --map=dev
```

Обратите внимание, что мы выбрали режим `fsdax` и используем системную память для хранения метаданных страниц. Мы рекомендуем использовать `--map=dev`. Так метаданные хранятся непосредственно в пространстве имен. Возможность хранения метаданных в памяти с помощью `--map=mem` пока считается экспериментальной.

Проверьте пространство имен с помощью `ndctl`. 
  
Пример выходных данных:

```bash
# ndctl list -N
{
  "dev":"namespace0.0",
  "mode":"fsdax",
  "map":"dev",
  "size":4294967296,
  "sector_size":512,
  "blockdev":"pmem0",
  "numa_node":0
}
```

### <a name="create-and-mount-pmem-device"></a>Создание и подключение устройства PMEM

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

## <a name="technical-considerations"></a>Технические вопросы

- Выделение блоков по 2 МБ для XFS и EXT4, как описано выше.
- Неправильное выравнивание между выделением блоков и `mmap` приводит к автоматическому переходу на 4 КБ.
- Размер файлов должен быть кратен 2 МБ (по модулю 2 МБ).
- Не отключайте прозрачные огромные страницы (THP) (включены по умолчанию для большинства дистрибутивов).

После настройки устройства с помощью `ndctl`, его создания и подключения можно поместить в него файлы базы данных или создать новую базу данных.

Так как устройства PMEM поддерживают безопасный O_DIRECT, можно включить флаг трассировки 3979, чтобы отключить механизм принудительной записи на диск. Дополнительные сведения см. на странице [Поддержка FUA](https://support.microsoft.com/help/4131496/enable-forced-flush-mechanism-in-sql-server-2017-on-linux). Внутренние методы принудительного доступа к модулям рассматриваются здесь: [Внутренности FUA](https://blogs.msdn.microsoft.com/bobsql/2018/12/18/sql-server-on-linux-forced-unit-access-fua-internals/).

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения об SQL Server на Linux см. в статье [SQL Server на Linux](sql-server-linux-overview.md).
Рекомендации по оптимизации производительности SQL Server в Linux см. в статье [Рекомендации по производительности](sql-server-linux-performance-best-practices.md).
