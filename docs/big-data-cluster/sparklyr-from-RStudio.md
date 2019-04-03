---
title: Использовать sparklyr из RStudio
titleSuffix: SQL Server big data clusters
description: Подключитесь к кластеру больших данных с помощью sparklyr из RStudio.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 30b8ddccd01c0e8d9a4eac34f2f504b0d8971af6
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860195"
---
# <a name="use-sparklyr-in-sql-server-big-data-cluster"></a>Использовать Sparklyr в кластере SQL Server больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sparklyr интерфейс R для Apache Spark. Sparklyr — предпочтительный способ разработчикам R использовать Spark. В этой статье описывается использование sparklyr в кластере большие данные SQL Server 2019 (Предварительная версия), с помощью RStudio.

## <a name="prerequisites"></a>предварительные требования

- [Развертывание кластера больших данных SQL Server 2019](quickstart-big-data-cluster-deploy.md).
- [Установка RStudio](https://www.rstudio.com/)

## <a name="connect-to-spark-in-ss19-big-data-cluster"></a>Подключение к spark в кластере SS19 больших данных

В RStudio Создание RScript и подключение к Spark, следующим образом. Кластер Spark больших данных подключается через Livy, который можно связаться с [HDFS/Spark шлюза](connect-to-big-data-cluster.md#hdfs). Для проверки подлинности используйте имя пользователя и пароль, указанные во время развертывания.

```r
library(sparklyr)
library(dplyr)
library(DBI)

#Specify the Knox username and password
config <- livy_config(user = "***root***", password = "****")

httr::set_config(httr::config(ssl_verifypeer = 0L))

sc <- spark_connect(master = "https://<IP>:<PORT>/gateway/default/livy/v1",
                    method = "livy",
                    config = config)
```

## <a name="run-sparklyr-queries"></a>Выполнение запросов sparklyr

После подключения к Spark, можно запустить sparklyr. В следующем примере выполняется запрос на набор данных iris, с помощью sparklyr:

``` r
copy_to(sc, iris)

iris_count <- dbGetQuery(sc, "SELECT COUNT(*) FROM iris")

iris_count
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах большие данные см. в разделе [Каковы кластеров SQL Server 2019 больших данных?](big-data-cluster-overview.md).