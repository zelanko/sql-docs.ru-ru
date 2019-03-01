---
title: Использовать sparklyr из RStudio
titleSuffix: SQL Server 2019 big data clusters
description: Подключитесь к кластеру больших данных с помощью sparklyr из RStudio.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 83980f9d08a3894b0fbf7871cf899483e06702c4
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018360"
---
# <a name="use-sparklyr-in-sql-server-2019-big-data-cluster"></a>Использовать Sparklyr в кластере SQL Server 2019 больших данных

Sparklyr интерфейс R для Apache Spark. Sparklyr — предпочтительный способ разработчикам R использовать Spark. В этой статье описывается использование sparklyr в кластере большие данные SQL Server 2019 (Предварительная версия), с помощью RStudio.

## <a name="prerequisites"></a>предварительные требования

- [Развертывание кластера больших данных SQL Server 2019](quickstart-big-data-cluster-deploy.md).
- [Установка RStudio](https://www.rstudio.com/)

## <a name="connect-to-spark-in-ss19-big-data-cluster"></a>Подключение к spark в кластере SS19 больших данных

В RStudio Создание RScript и подключение к Spark, следующим образом. Кластер Spark больших данных подключается через Livy, который может быть достигнут с [HDFS/Spark шлюза](connect-to-big-data-cluster.md#hdfs). Для проверки подлинности используйте имя пользователя и пароль, указанные во время развертывания.

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