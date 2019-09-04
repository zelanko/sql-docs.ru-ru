---
title: Учебник. Развертывание модели кластеризации в Python
description: В четвертой части серии руководств из четырех частей вы развернете модель кластеризации в Python с SQL Server Службы машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/27/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 923fae2a6b215814888b04dc674b67e4c87bc00d
ms.sourcegitcommit: ecb19d0be87c38a283014dbc330adc2f1819a697
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70238689"
---
# <a name="tutorial-deploy-a-clustering-model-in-python-with-sql-server-machine-learning-services"></a>Учебник. Развертывание модели кластеризации в Python с помощью SQL Server Службы машинного обучения

В четвертой части серии руководств из четырех частей вы развернете модель кластеризации, разработанную на языке Python, в базу данных SQL с помощью SQL Server Службы машинного обучения.

Для регулярного создания кластеров при регистрации новых клиентов необходимо иметь возможность вызывать скрипт Python из любого приложения. Для этого можно развернуть скрипт Python в SQL Server, поместив скрипт Python в хранимую процедуру SQL в базе данных. Поскольку модель выполняется в базе данных SQL, ее можно легко обучить с данными, хранящимися в базе данных.

В этом разделе вы перемещаете код Python, который вы только что написали в SQL Server, и развертываете кластеризацию с помощью SQL Server Службы машинного обучения.

Из этой статьи вы узнаете о следующем:

> [!div class="checklist"]
> * Создание хранимой процедуры, которая создает модель
> * Выполнение кластеризации в SQL Server
> * Использование сведений о кластеризации

В [первой части](tutorial-python-clustering-model.md)вы установили необходимые компоненты и импортировали образец базы данных.

В [части 2](tutorial-python-clustering-model-prepare-data.md)вы узнали, как подготавливать данные из базы данных SQL для выполнения кластеризации.

В [третьей части](tutorial-python-clustering-model-build.md)вы узнали, как создать и обучить модель кластеризации K-средних в Python.

## <a name="prerequisites"></a>Предварительные требования

* В четвертой части этой серии руководств предполагается, что вы выполнили предварительные требования к первой части и выполнили [**шаги,** ](tutorial-python-clustering-model.md)описанные в части [**две**](tutorial-python-clustering-model-prepare-data.md) и [**третий**](tutorial-python-clustering-model-build.md).

## <a name="create-a-stored-procedure-that-generates-the-model"></a>Создание хранимой процедуры, которая создает модель

Выполните следующий скрипт T-SQL, чтобы создать хранимую процедуру. Процедура воссоздает шаги, которые вы разработали в одной и той же части серии руководств.

* Классификация клиентов на основе журнала покупок и возврата
* создание четырех кластеров клиентов с помощью алгоритма K-средних

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

## <a name="perform-clustering-in-sql-database"></a>Выполнение кластеризации в базе данных SQL

Теперь, когда вы создали хранимую процедуру, выполните следующий сценарий, чтобы выполнить кластеризацию с помощью процедуры.

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

## <a name="use-the-clustering-information"></a>Использование сведений о кластеризации

Так как хранимая процедура кластеризации сохранена в базе данных, она может эффективно выполнять кластеризацию для данных клиента, хранящихся в той же базе данных. Процедуру можно выполнять при каждом обновлении данных клиента и использовать обновленные сведения о кластеризации.

Предположим, вы хотите отправить рекламное письмо клиентам в кластере 0, неактивной группе (вы можете увидеть, как четыре кластера были описаны в [третьей части](tutorial-python-clustering-model-build.md#analyze-the-results) этого руководства). Следующий код выбирает адреса электронной почты клиентов в кластере 0.

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

Можно изменить значение **c. Cluster** , чтобы получить адреса электронной почты для клиентов в других кластерах.

## <a name="clean-up-resources"></a>Очистка ресурсов

По завершении работы с этим руководством можно удалить базу данных tpcxbb_1gb из SQL Server.

## <a name="next-steps"></a>Следующие шаги

В четвертой части этой серии руководств вы выполнили следующие действия:

* Создание хранимой процедуры, которая создает модель
* Выполнение кластеризации в SQL Server
* Использование сведений о кластеризации

Дополнительные сведения об использовании Python в SQL Server Службы машинного обучения см. в следующих статьях:

* [Краткое руководство Запуск скрипта Python "Hello World" на SQL Server Службы машинного обучения](quickstart-python-run-using-t-sql.md)
* [Другие руководства по Python для SQL Server Службы машинного обучения](sql-server-python-tutorials.md)
* [Установка пакетов Python с помощью склмлутилс](../package-management/install-additional-python-packages-on-sql-server.md)

