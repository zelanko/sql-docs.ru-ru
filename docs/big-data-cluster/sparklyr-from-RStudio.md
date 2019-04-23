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
ms.openlocfilehash: 148e4942babafb35af2efe33eb427f9462f0a47e
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59969880"
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

   '' "Install.packages RStudio Desktop (репозиториев" DBI"="https://cran.microsoft.com/snapshot/2019-01-01") install.packages (репозиториев" dplyr"="https://cran.microsoft.com/snapshot/2019-01-01") install.packages (репозиториев" sparklyr"="https://cran.microsoft.com/snapshot/2019-01-01")
   ```

## Connect to Spark in a big data cluster

You can use sparklyr to connect from a client to the big data cluster using Livy and the HDFS/Spark gateway. 

In RStudio, create an R script and connect to Spark as in the following example:

> [!TIP]
> For the `<USERNAME>` and `<PASSWORD>` values, use the username (such as root) and password you set during the big data cluster deployment. For the `<IP>` and `<PORT>` values, see the documentation on the [HDFS/Spark gateway](connect-to-big-data-cluster.md#hdfs).

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