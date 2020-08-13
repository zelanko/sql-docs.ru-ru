---
title: Рекомендации по обеспечению производительности кластеров больших данных SQL Server
description: В этой статье приводятся рекомендации по обеспечению производительности кластеров больших данных SQL Server в Kubernetes
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 06/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: abb5a73f472ccefa53517c54a3d403af82d0beb2
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85906242"
---
# <a name="performance-best-practices-and-configuration-guidelines-for-sql-server-big-data-clusters"></a>Рекомендации по производительности и конфигурации для кластеров больших данных SQL Server

[!INCLUDE [sqlserver2019](../includes/applies-to-version/sqlserver2019.md)]

В этой статье приводятся рекомендации по повышению производительности приложений, предназначенных для работы в кластере больших данных.

Следующие рекомендации касаются настройки операционной системы Linux с размещенными в ней рабочими узлами Kubernetes, на которых будет развернут BDC. Рекомендуется перед развертыванием кластера больших данных настроить профиль настройки. Параметры, включенные в рекомендуемый профиль настройки, были проверены в ходе внедрения корпорациями Майкрософт и Intel. Результаты исследования опубликованы для загрузки в этом [техническом документе](https://aka.ms/sql-bdc-spark-perf/).

> [!TIP]
> Сведения о специфичных настройках SQL Server на Linux см. в статье [Рекомендации по производительности и конфигурации для SQL Server на Linux](../linux/sql-server-linux-performance-best-practices.md). Кроме того, по-прежнему применимы и другие рекомендации, такие как проектирование индексов для баз данных SQL Server.

## <a name="proposed-linux-settings-using-a-tuned-mssql-bdc-profile"></a>Рекомендуемые параметры Linux при использовании настраиваемого профиля `mssql-bdc`

Создайте профиль конфигурации **tuned.conf** с представленным ниже содержимым.

```bash
[main]
summary=Optimize for Microsoft SQL Server Big Data Clusters TPC-DS performance
include=throughput-performance
 
[sysctl]
#network tunings
net.ipv4.conf.default.rp_filter=1
net.ipv4.tcp_timestamps=0
net.ipv4.tcp_sack = 1
net.core.netdev_max_backlog = 25000
net.core.rmem_max = 2147483647
net.core.wmem_max = 2147483647
net.core.rmem_default = 33554431
net.core.wmem_default = 33554432
net.core.optmem_max = 33554432
net.ipv4.tcp_rmem =8192 33554432 2147483647
net.ipv4.tcp_wmem =8192 33554432 2147483647
net.ipv4.tcp_low_latency=1
net.ipv4.tcp_adv_win_scale=1
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv4.conf.all.arp_filter=1
net.ipv4.tcp_retries2=5
net.ipv6.conf.lo.disable_ipv6 = 1
net.core.somaxconn = 65535
 
#memory cache settings
vm.swappiness=1
vm.overcommit_memory=0
vm.dirty_background_ratio=1
 
#kernel NUMA
kernel.numa_balancing=0

#filesystem
fs.aio-max-nr=1048576
 
[vm]
#should be revisited for SQL large pages use in master/data/compute pods
transparent_hugepages=never
```

## <a name="install-tuned-utility-on-all-the-kubernetes-worker-nodes"></a>Установка служебной программы **tuned** на всех рабочих узлах Kubernetes

Для установки **tuned** выполните команду:

```bash
apt-get -y install tuned
```

## <a name="apply-tuning-settings-to-all-kubernetes-worker-nodes"></a>Применение параметров настройки ко всем рабочим узлам Kubernetes

Скопируйте созданный выше файл **tuned.conf** на каждый целевой рабочий узел:

```bash
cd /usr/lib/tuned
scp -r <sourcePath> ./mssql-bdc
```

Чтобы включить настраиваемый профиль **mssql-bdc**, сохраните следующие определения в файле **tuned.conf** в папке `/usr/lib/tuned/mssql-bdc` на всех рабочих узлах Kubernetes и включите профиль, выполнив следующие команды:

```bash
chmod +x /usr/lib/tuned/mssql-bdc/tuned.conf
tuned-adm profile mssql-bdc
```

Убедитесь, что он включен, выполнив следующую команду:

```bash
tuned-adm active
```

или диспетчер конфигурации служб

```bash
tuned-adm list
```

Если профиль изменяется динамически, то для вступления в силу новых изменений необходимо перезапустить **tuned** на всех затронутых рабочих узлах.

```bash
systemctl restart tuned
```
 
Журналы службы **tuned** можно найти в файле */var/log/tuned/tuned.log*.

При необходимости можно настроить профиль настройки на одном узле в кластере Kubernetes и использовать приведенный ниже сценарий, чтобы скопировать и настроить его на оставшихся узлах.

```bash
#!/bin/bash -e
# This script takes a list of servers (IPs like `cat ~administrator/workerhosts)) as input
# and update these servers with the local version of mssql-bdc tuned.conf.
 
is_root() {
    local is_root_set=0
    if [ "$EUID" -ne 0 ]; then
        echo "Please run as root"
    else
        is_root_set=1
    fi
    return "${is_root_set}"
}
 
# function main
if is_root -eq 0; then
    exit 0
fi
 
while [ $# -gt 0 ]
do
    # sometimes, people add non-breaking space characters to their *host* files.
    WORKER_IP=$(echo "$1" | sed -e 's/\xC2\xA0//g')
    echo -e "updating mssql-bdc tuned on \e[42m${WORKER_IP}\e[0m"
    # the following commands assume tuned was not set up and active...
    # TODO: add the tuned install and status checks
    ssh "${WORKER_IP}" mkdir -p /usr/lib/tuned/mssql-bdc
    scp ~administrator/tuned.conf "${WORKER_IP}":/usr/lib/tuned/mssql-bdc/tuned.conf
    ssh "${WORKER_IP}" tuned-adm profile mssql-bdc
    ssh "${WORKER_IP}" systemctl restart tuned
    ssh "${WORKER_IP}" tuned-adm active
    shift
done

```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные ресурсы, включая эталонные архитектуры для кластеров больших данных SQL Server, см. в следующих статьях:

* [Анализ примера. Рабочие нагрузки SQL, выполняемые на Apache Spark в кластере больших данных MS SQL Server 2019](https://aka.ms/sql-bdc-spark-perf/)

* [Эталонная архитектура HPE для предоставления аналитики по всем данным с помощью кластеров больших данных Microsoft SQL Server 2019](https://h20195.www2.hpe.com/V2/GetDocument.aspx?docname=a50001963enw)

* [Dell EMC PowerStore. Кластеры больших данных Microsoft SQL Server 2019](https://www.dellemc.com/resources/en-us/asset/white-papers/products/storage/h18231-dell-emc-powerstore-sql-server-big-data-clusters.pdf)

* [Кластеры больших данных Microsoft SQL Server 2019. Решение для обработки больших данных с использованием инфраструктуры EMC Dell](https://infohub.delltechnologies.com/t/microsoft-sql-server-2019-big-data-clusters-a-big-data-solution-using-dell-emc-infrastructure/)

* [Эталонная архитектура кластеров больших данных Microsoft SQL Server 2019 на Cisco UCS](https://www.cisco.com/c/en/us/solutions/collateral/data-center-virtualization/unified-computing/sql-server-on-big-data-cluster-on-ucs.html)