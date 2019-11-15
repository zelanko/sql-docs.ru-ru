---
title: Учебник по Python. Развертывание кластерной модели
description: В четвертой части этой серии руководств будет выполняться развертывание модели кластеризации в Python с помощью Служб машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/27/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: df0fd7cb27977679a6ca879d7ae01045ed3fa8c8
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727135"
---
# <a name="tutorial-deploy-a-model-in-python-to-categorize-customers-with-sql-server-machine-learning-services"></a>Руководство. Развертывание модели для категоризации клиентов в Python с использованием Служб машинного обучения SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В четвертой части этой серии руководств будет выполняться развертывание модели кластеризации, разработанной в Python, в базе данных SQL с помощью Служб машинного обучения SQL Server.

Для выполнения кластеризации на регулярной основе по мере регистрации новых клиентов необходимо иметь возможность вызывать скрипт Python из любого приложения. Для этого можно развернуть скрипт Python в SQL Server, заключив его в хранимую процедуру SQL в базе данных. Поскольку модель выполняется в базе данных SQL, ее можно легко обучать на данных, хранящихся в базе данных.

В этом разделе вы будете перемещать только что написанный код Python в SQL и развертывать кластеризацию с помощью Служб машинного обучения SQL Server.

В этой статье вы узнаете, как выполнять следующие задачи.

> [!div class="checklist"]
> * Создание хранимой процедуры, которая формирует модель
> * Выполнение кластеризации в SQL Server
> * Использование сведений кластеризации

В [первой части](python-clustering-model.md) были установлены необходимые компоненты и восстановлена демонстрационная база данных.

Во [второй части](python-clustering-model-prepare-data.md) вы узнали, как подготовить данные из базы данных SQL для выполнения кластеризации.

В [третьей части](python-clustering-model-build.md) вы узнали, как создать и обучить модель кластеризации на основе k-средних в Python.

## <a name="prerequisites"></a>предварительные требования

* В четвертой части этого учебника предполагается, что вы уже выполнили предварительные требования из [**первой части**](python-clustering-model.md), а также действия, указанные во [**второй** ](python-clustering-model-prepare-data.md) и [**третьей**](python-clustering-model-build.md) частях.

## <a name="create-a-stored-procedure-that-generates-the-model"></a>Создание хранимой процедуры, которая формирует модель

Чтобы создать хранимую процедуру, выполните следующий скрипт T-SQL. Эта процедура восстанавливает шаги, которые вы разработали в первой и второй частях этой серии руководств:

* классификация клиентов на основе журнала покупок и возвратов;
* создание четырех кластеров клиентов с помощью алгоритма k-средних.

```sql
USE [tpcxbb_1gb]
GO

CREATE procedure [dbo].[py_generate_customer_return_clusters]
AS

BEGIN
    DECLARE

-- Input query to generate the purchase history & return metrics
     @input_query NVARCHAR(MAX) = N'
SELECT
  ss_customer_sk AS customer,
  CAST( (ROUND(COALESCE(returns_count / NULLIF(1.0*orders_count, 0), 0), 7) ) AS FLOAT) AS orderRatio,
  CAST( (ROUND(COALESCE(returns_items / NULLIF(1.0*orders_items, 0), 0), 7) ) AS FLOAT) AS itemsRatio,
  CAST( (ROUND(COALESCE(returns_money / NULLIF(1.0*orders_money, 0), 0), 7) ) AS FLOAT) AS monetaryRatio,
  CAST( (COALESCE(returns_count, 0)) AS FLOAT) AS frequency
FROM
  (
    SELECT
      ss_customer_sk,
      -- return order ratio
      COUNT(distinct(ss_ticket_number)) AS orders_count,
      -- return ss_item_sk ratio
      COUNT(ss_item_sk) AS orders_items,
      -- return monetary amount ratio
      SUM( ss_net_paid ) AS orders_money
    FROM store_sales s
    GROUP BY ss_customer_sk
  ) orders
  LEFT OUTER JOIN
  (
    SELECT
      sr_customer_sk,
      -- return order ratio
      count(distinct(sr_ticket_number)) as returns_count,
      -- return ss_item_sk ratio
      COUNT(sr_item_sk) as returns_items,
      -- return monetary amount ratio
      SUM( sr_return_amt ) AS returns_money
    FROM store_returns
    GROUP BY sr_customer_sk
  ) returned ON ss_customer_sk=sr_customer_sk
 '

EXEC sp_execute_external_script
      @language = N'Python'
    , @script = N'

import pandas as pd
from sklearn.cluster import KMeans

#get data from input query
customer_data = my_input_data

#We concluded in step 2 in the tutorial that 4 would be a good number of clusters
n_clusters = 4

#Perform clustering
est = KMeans(n_clusters=n_clusters, random_state=111).fit(customer_data[["orderRatio","itemsRatio","monetaryRatio","frequency"]])
clusters = est.labels_
customer_data["cluster"] = clusters

OutputDataSet = customer_data
'
    , @input_data_1 = @input_query
    , @input_data_1_name = N'my_input_data'
             with result sets (("Customer" int, "orderRatio" float,"itemsRatio" float,"monetaryRatio" float,"frequency" float,"cluster" float));
END;
GO
```

## <a name="perform-clustering-in-sql-database"></a>Выполнение кластеризации в SQL Server

Теперь, когда хранимая процедура создана, запустите следующий скрипт, чтобы выполнить кластеризацию с помощью этой процедуры.

```sql
--Create a table to store the predictions in

DROP TABLE IF EXISTS [dbo].[py_customer_clusters];
GO

CREATE TABLE [dbo].[py_customer_clusters] (
    [Customer] [bigint] NULL
  , [OrderRatio] [float] NULL
  , [itemsRatio] [float] NULL
  , [monetaryRatio] [float] NULL
  , [frequency] [float] NULL
  , [cluster] [int] NULL
  ,
    ) ON [PRIMARY]
GO

--Execute the clustering and insert results into table
INSERT INTO py_customer_clusters
EXEC [dbo].[py_generate_customer_return_clusters];

-- Select contents of the table to verify it works
SELECT * FROM py_customer_clusters;
```

## <a name="use-the-clustering-information"></a>Использование сведений кластеризации

Так как процедура кластеризации сохранена в базе данных, она может эффективно выполнять кластеризацию для данных клиента, хранящихся в той же базе данных. Эту процедуру можно выполнять при каждом обновлении данных клиента и использовать обновленные сведения кластеризации.

Предположим, требуется отправить рекламное сообщение электронной почты клиентам в кластере 0, неактивной группе (описание четырех кластеров см. в [третьей части](python-clustering-model-build.md#analyze-the-results) этого учебника). Следующий код выбирает адреса электронной почты клиентов в кластере 0.

```sql
USE [tpcxbb_1gb]
--Get email addresses of customers in cluster 0 for a promotion campaign
SELECT customer.[c_email_address], customer.c_customer_sk
  FROM dbo.customer
  JOIN
  [dbo].[py_customer_clusters] as c
  ON c.Customer = customer.c_customer_sk
  WHERE c.cluster = 0
```

Чтобы получить адреса электронной почты клиентов в других кластерах, можно изменить значение **c.cluster**.

## <a name="clean-up-resources"></a>Очистка ресурсов

Если вы не собираетесь продолжать работу с этим учебником, можно удалить базу данных tpcxbb_1gb с SQL Server.

## <a name="next-steps"></a>Дальнейшие действия

В четвертой части этого учебника вы выполнили следующие действия.

* Создание хранимой процедуры, которая формирует модель
* Выполнение кластеризации в SQL Server
* Использование сведений кластеризации

Дополнительные сведения об использовании Python в Службах машинного обучения SQL Server см. в следующих ресурсах.

* [Краткое руководство. Создание и выполнение простых сценариев Python с помощью служб машинного обучения SQL Server](quickstart-python-create-script.md)
* [Другие учебники по Python для Служб машинного обучения SQL Server](sql-server-python-tutorials.md)
* [Установка пакетов Python с помощью sqlmlutils](../package-management/install-additional-python-packages-on-sql-server.md)

