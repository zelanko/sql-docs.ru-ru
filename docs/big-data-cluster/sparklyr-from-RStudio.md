---
title: Использование sparklyr из RStudio
titleSuffix: SQL Server big data clusters
description: Подключитесь к кластеру больших данных с помощью sparklyr из RStudio.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f346fed17e4c79214a7eba43f70767fc80b98a07
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67728373"
---
# <a name="use-sparklyr-in-sql-server-big-data-cluster"></a>Использование sparklyr в кластере больших данных SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sparklyr предоставляет интерфейс R для Apache Spark. Sparklyr является популярным способом для разработчиков R, использующих Spark. В этой статье описывается, как использовать sparklyr в кластере больших данных SQL Server 2019 (Предварительная версия) с помощью RStudio.

## <a name="prerequisites"></a>Предварительные требования

- [Развертывание кластера больших данных SQL Server 2019](quickstart-big-data-cluster-deploy.md).

### <a name="install-rstudio-desktop"></a>Установка RStudio Desktop

Установите и настройте **RStudio Desktop** , выполнив следующие действия.

1. Если вы используете клиент Windows, [скачайте и установите R 3.4.4](https://cran.rstudio.com/bin/windows/base/old/3.4.4).

1. [Скачайте и установите RStudio Desktop](https://www.rstudio.com/products/rstudio/download/).

1. После завершения установки выполните следующие команды в RStudio Desktop, чтобы установить необходимые пакеты:

   ```RStudioDesktop
   install.packages("DBI", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   install.packages("dplyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   install.packages("sparklyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   ```

## <a name="connect-to-spark-in-a-big-data-cluster"></a>Подключение к Spark в кластере больших данных

Sparklyr можно использовать для подключения клиента к кластеру больших данных с помощью Livy и шлюза HDFS/Spark. 

В RStudio создайте скрипт R и подключитесь к Spark, как показано в следующем примере:

> [!TIP]
> Для значений `<PASSWORD>` и используйте имя пользователя (например, root) и пароль, заданные при развертывании кластера больших данных. `<USERNAME>` `<IP>` Значения и `<PORT>` см. в документации по подключению [к кластеру больших данных](connect-to-big-data-cluster.md).

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

После подключения к Spark можно запустить sparklyr. В следующем примере выполняется запрос к набору данных IRI с помощью sparklyr:

```r
iris_tbl <- copy_to(sc, iris)

iris_count <- dbGetQuery(sc, "SELECT COUNT(*) FROM iris")

iris_count
```

## <a name="distributed-r-computations"></a>Распределенные вычисления R

Одной из функций sparklyr является возможность [распределять вычисления R](https://spark.rstudio.com/guides/distributed-r/) с помощью [spark_apply](https://spark.rstudio.com/reference/spark_apply/).

Так как кластеры больших данных используют подключения Livy, необходимо `packages = FALSE` задать в вызове **spark_apply**. Дополнительные сведения см. в [разделе Livy](https://spark.rstudio.com/guides/distributed-r/#livy) документации sparklyr по распределенным вычислениям R. С помощью этого параметра можно использовать только те пакеты R, которые уже установлены в кластере Spark в коде R, переданном в **spark_apply**. В следующем примере демонстрируется эта функция:

```r
iris_tbl %>% spark_apply(function(e) nrow(e), names = "nrow", group_by = "Species", packages = FALSE)
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в разделе [что такое кластеры больших данных SQL Server 2019](big-data-cluster-overview.md).
