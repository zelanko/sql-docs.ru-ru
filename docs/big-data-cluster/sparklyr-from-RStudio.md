---
title: Использовать sparklyr из RStudio
titleSuffix: SQL Server big data clusters
description: Подключитесь к кластеру больших данных с помощью sparklyr из RStudio.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8004146499bd8b17c7705f7558de075dfece5813
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65994181"
---
# <a name="use-sparklyr-in-sql-server-big-data-cluster"></a>Использовать sparklyr в кластере SQL Server больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sparklyr интерфейс R для Apache Spark. Sparklyr — это популярное средство для разработчикам R использовать Spark. В этой статье описывается использование sparklyr в кластере большие данные SQL Server 2019 (Предварительная версия), с помощью RStudio.

## <a name="prerequisites"></a>предварительные требования

- [Развертывание кластера больших данных SQL Server 2019](quickstart-big-data-cluster-deploy.md).

### <a name="install-rstudio-desktop"></a>Установка RStudio Desktop

Установка и настройка **RStudio Desktop** , сделав следующее:

1. При выполнении на клиентском компьютере Windows, [загрузить и установить R 3.4.4](https://cran.rstudio.com/bin/windows/base/old/3.4.4).

1. [Загрузка и установка RStudio Desktop](https://www.rstudio.com/products/rstudio/download/).

1. После завершения установки выполните следующие команды в RStudio Desktop, чтобы установить необходимые пакеты:

   ```RStudioDesktop
   install.packages("DBI", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   install.packages("dplyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   install.packages("sparklyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   ```

## <a name="connect-to-spark-in-a-big-data-cluster"></a>Подключение к Spark в кластере больших данных

Sparklyr можно использовать для подключения от клиента к кластеру больших данных с помощью Livy и шлюзом HDFS или Spark. 

В RStudio создайте скрипт R и подключение к Spark, как показано в следующем примере:

> [!TIP]
> Для `<USERNAME>` и `<PASSWORD>` значения, используйте имя пользователя (например, root) и пароль, указанные во время развертывания кластера больших данных. Для `<IP>` и `<PORT>` значения, см. в документации на [подключении к кластеру больших данных](connect-to-big-data-cluster.md).

```r
library(sparklyr)
library(dplyr)
library(DBI)

#Specify the Knox username and password
config <- livy_config(user = "<username>", password = "<password>")

httr::set_config(httr::config(ssl_verifypeer = 0L, ssl_verifyhost = 0L))

sc <- spark_connect(master = "https://<IP>:<PORT>/gateway/default/livy/v1",
                    method = "livy",
                    config = config)
```

## <a name="run-sparklyr-queries"></a>Выполнение запросов sparklyr

После подключения к Spark, можно запустить sparklyr. В следующем примере выполняется запрос на набор данных iris, с помощью sparklyr:

```r
iris_tbl <- copy_to(sc, iris)

iris_count <- dbGetQuery(sc, "SELECT COUNT(*) FROM iris")

iris_count
```

## <a name="distributed-r-computations"></a>Распределенных вычислений на r.

Одной из особенностей sparklyr является возможность [распределения вычислений R](https://spark.rstudio.com/guides/distributed-r/) с [spark_apply](https://spark.rstudio.com/reference/spark_apply/).

Поскольку кластеры больших данных использовать Livy подключения, необходимо задать `packages = FALSE` в вызове **spark_apply**. Дополнительные сведения см. в разделе [Livy разделе](https://spark.rstudio.com/guides/distributed-r/#livy) sparklyr документации на распределенных вычислений R. Этот параметр можно использовать только пакеты R, которые уже установлены в кластере Spark в коде R, передаваемый **spark_apply**. В следующем примере демонстрируется эта функция:

```r
iris_tbl %>% spark_apply(function(e) nrow(e), names = "nrow", group_by = "Species", packages = FALSE)
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах большие данные см. в разделе [что такое большие данные кластеры SQL Server 2019](big-data-cluster-overview.md).
