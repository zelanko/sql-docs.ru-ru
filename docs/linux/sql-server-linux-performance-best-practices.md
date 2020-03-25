---
title: Рекомендации по обеспечению производительности SQL Server на Linux
description: В этой статье приводятся рекомендации по обеспечению производительности SQL Server на Linux.
author: tejasaks
ms.author: tejasaks
ms.reviewer: vanto
ms.date: 09/14/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 548ab73e97b9bccb6a64a95b7294d3d5ca63493d
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79286848"
---
# <a name="performance-best-practices-and-configuration-guidelines-for-sql-server-on-linux"></a>Рекомендации по производительности и конфигурации для SQL Server на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье приводятся рекомендации по повышению производительности приложений баз данных, подключающихся к SQL Server на Linux. Эти рекомендации относятся именно к платформе Linux. При этом действуют все стандартные рекомендации в отношении SQL Server, например касающиеся проектирования индекса.

Ниже приводятся рекомендации по настройке SQL Server и операционной системы Linux.

## <a name="sql-server-configuration"></a>Конфигурация SQL Server

Чтобы обеспечить максимальную производительность, рекомендуется выполнить описанные ниже задачи по настройке после установки SQL Server на Linux.

### <a name="best-practices"></a>Рекомендации

- **Использование PROCESS AFFINITY для узла и ЦП**

   Рекомендуется использовать инструкцию `ALTER SERVER CONFIGURATION`, чтобы задать `PROCESS AFFINITY` для всех узлов **NUMANODE** или ЦП, используемых для SQL Server в операционной системе Linux (то есть обычно для всех узлов и ЦП). Соответствие процессоров помогает эффективно планировать работу Linux и SQL. Использование параметра **NUMANODE** — простейший метод. Имейте в виду, что **PROCESS AFFINITY** следует использовать, даже если на вашем компьютере всего один узел NUMA.  Дополнительные сведения о задании **PROCESS AFFINITY** см. в документации по [ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md).

- **Настройка нескольких файлов данных tempdb**

   Так как установленный экземпляр SQL Server на Linux не дает возможности настроить несколько файлов tempdb, мы рекомендуем создать несколько файлов данных tempdb после установки. Дополнительные сведения см. в статье [Рекомендации по сокращению состязания за выделяемые ресурсы в базе данных tempdb SQL Server](https://support.microsoft.com/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d).

### <a name="advanced-configuration"></a>Расширенная настройка

Ниже приведены рекомендации по дополнительным параметрам конфигурации, которые можно настроить после установки SQL Server на Linux. Их выбор зависит от требований рабочей нагрузки и конфигурации операционной системы Linux.

- **Настройка предельного объема памяти с помощью mssql-conf**

   Чтобы обеспечить достаточный объем свободной физической памяти для операционной системы Linux, процесс SQL Server по умолчанию использует только 80 % физического ОЗУ. В некоторых системах с большим размером ОЗУ 20 % может быть очень много. Например, в системе с 1 ТБ ОЗУ при настройке по умолчанию неиспользуемыми остаются приблизительно 200 ГБ ОЗУ. В таком случае может быть желательно установить более высокий предел памяти. См. документацию по средству **mssql-conf** и параметру [memory.memorylimitmb](sql-server-linux-configure-mssql-conf.md#memorylimit), который определяет объем памяти, доступный SQL Server (в МБ).

   При изменении этого параметра будьте осторожны. Не задавайте слишком большое значение. Если памяти будет недостаточно, могут возникнуть проблемы в работе операционной системы Linux и других приложений Linux.

## <a name="linux-os-configuration"></a>Конфигурация ОС Linux

Чтобы обеспечить максимальную производительность системы SQL Server, рекомендуется использовать приведенные ниже параметры конфигурации операционной системы Linux.

### <a name="kernel-settings-for-high-performance"></a>Параметры ядра для высокой производительности
В этом разделе приводятся рекомендованные параметры операционной системы Linux для обеспечения как высокой производительности, так и пропускной способности системы SQL Server. Сведения о настройке этих параметров см. в документации по операционной системе Linux.



> [!Note]
> В Red Hat Enterprise Linux (RHEL) при использовании [настраиваемого](https://tuned-project.org) профиля пропускной способности эти параметры задаются автоматически (за исключением режима C-States). Начиная с RHEL 8.0 используется встроенный профиль mssql /usr/lib/tuned, разработанный совместно с Red Hat и предоставляющий возможность более детальной настройки производительности для рабочих нагрузок SQL Server. Этот профиль включает профиль пропускной способности RHEL. Определения этого профиля представлены ниже для сравнения с другими дистрибутивами Linux и выпусками RHEL, не содержащими этого профиля.

В приведенной ниже таблице представлены рекомендации по параметрам ЦП.

| Параметр | Значение | Дополнительные сведения |
|---|---|---|
| Регулятор частоты ЦП | производительность | См. описание команды **cpupower** |
| ENERGY_PERF_BIAS | производительность | См. описание команды **x86_energy_perf_policy** |
| min_perf_pct | 100 | См. документацию по режиму Intel p-state |
| C-States | Только C1 | Сведения о том, как включить только режим C1 C-States, см. в документации по Linux или вашей системе |

В приведенной ниже таблице представлены рекомендации по параметрам дисков.

| Параметр | Значение | Дополнительные сведения |
|---|---|---|
| Упреждающее чтение с диска | 4096 | См. описание команды **blockdev** |
| Параметры sysctl | kernel.sched_min_granularity_ns = 10000000<br/>kernel.sched_wakeup_granularity_ns = 15000000<br/>vm.dirty_ratio = 40<br/>vm.dirty_background_ratio = 10<br/>vm.swappiness = 10 | См. описание команды **sysctl** |

### <a name="kernel-setting-auto-numa-balancing-for-multi-node-numa-systems"></a>Автоматическая балансировка между узлами NUMA в системах с несколькими узлами NUMA

Если сервер SQL Server устанавливается в системах с несколькими узлами **NUMA**, указанный ниже параметр ядра **kernel.numa_balancing** включается по умолчанию. Чтобы обеспечить максимально эффективную работу SQL Server в системе **NUMA**, отключите автоматическую балансировку NUMA в системе с несколькими узлами NUMA.

```bash
sysctl -w kernel.numa_balancing=0
```

### <a name="kernel-settings-for-virtual-address-space"></a>Параметры ядра для виртуального адресного пространства

Значение параметра **vm.max_map_count** по умолчанию (65 536) может быть недостаточно большим для системы SQL Server. Измените это значение до верхнего предела (256 000).

```bash
sysctl -w vm.max_map_count=262144
```

### <a name="proposed-linux-settings-using-a-tuned-mssql-profile"></a>Рекомендуемые параметры Linux при использовании настраиваемого профиля mssql

```bash
#
# A tuned configuration for SQL Server on Linux
#
    
[main]
summary=Optimize for Microsoft SQL Server
include=throughput-performance
    
[cpu]
force_latency=5

[sysctl]
vm.swappiness = 1
vm.dirty_background_ratio = 3
vm.dirty_ratio = 80
vm.dirty_expire_centisecs = 500
vm.dirty_writeback_centisecs = 100
vm.transparent_hugepages=always
# For , use
# vm.transparent_hugepages=madvice
vm.max_map_count=1600000
net.core.rmem_default = 262144
net.core.rmem_max = 4194304
net.core.wmem_default = 262144
net.core.wmem_max = 1048576
kernel.numa_balancing=0
kernel.sched_latency_ns = 60000000
kernel.sched_migration_cost_ns = 500000
kernel.sched_min_granularity_ns = 15000000
kernel.sched_wakeup_granularity_ns = 2000000
```

Чтобы включить этот настраиваемый профиль, сохраните эти определения в файле **tuned.conf** в папке /usr/lib/tuned/mssql и включите профиль, выполнив следующую команду

```bash
chmod +x /usr/lib/tuned/mssql/tuned.conf
tuned-adm profile mssql
```

Убедитесь, что профиль включен, выполнив команду

```bash
tuned-adm active
```
или диспетчер конфигурации служб
```bash
tuned-adm list
```

### <a name="disable-last-accessed-datetime-on-file-systems-for-sql-server-data-and-log-files"></a>Отключение даты и времени последнего доступа к файлам данных и журналов SQL Server в файловых системах

Используйте атрибут **noatime** с любой файловой системой, которая используется для хранения файлов данных и журналов SQL Server. Сведения о задании этого атрибута см. в документации по Linux.

### <a name="leave-transparent-huge-pages-thp-enabled"></a>Сохранение параметра Transparent Huge Pages (THP) во включенном состоянии

В большинстве систем Linux этот параметр конфигурации включен по умолчанию. Чтобы обеспечить максимально единообразную производительность, мы рекомендуем не отключать его. Однако в случае высокой активности страничной памяти в развертываниях SQL Server с несколькими экземплярами или при выполнении SQL Server с другими ресурсоемкими приложениями на сервере рекомендуется проверить производительность приложений после выполнения следующей команды 

```bash
echo madvice > /sys/kernel/mm/transparent_hugepage/enabled
```
или после изменения настраиваемого профиля mssql путем установки параметра

```bash
vm.transparent_hugepages=madvice
```
и активации профиля mssql после изменения параметра
```bash
tuned-adm off
tuned-amd profile mssql
```

### <a name="swapfile"></a>Файл подкачки

Во избежание проблем с нехваткой памяти правильно настройте файл подкачки. Сведения о создании файла подкачки и его правильном размере см. в документации по вашей системе Linux.

### <a name="virtual-machines-and-dynamic-memory"></a>Виртуальные машины и динамическая память

Если SQL Server на Linux выполняется в виртуальной машине, настройте фиксированный размер памяти, резервируемой для виртуальной машины. Не используйте такие функции, как динамическая память Hyper-V.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о функциях SQL Server, повышающих производительность, см. в статье о [начале работы с функциями производительности](sql-server-linux-performance-get-started.md).

Дополнительные сведения об SQL Server на Linux см. в статье [Обзор SQL Server на Linux](sql-server-linux-overview.md).
