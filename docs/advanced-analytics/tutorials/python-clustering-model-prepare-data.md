---
title: Учебник. Подготовка данных для категоризации клиентов в Python
description: В второй части серии руководств из четырех частей вы будете подготавливать данные из SQL Server базы данных для выполнения кластеризации в Python с SQL Server Службы машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/30/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d91f3b9f1e3d1abe53d677d9f9058058d321d985
ms.sourcegitcommit: 26715b4dbef95d99abf2ab7198a00e6e2c550243
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294349"
---
# <a name="tutorial-prepare-data-to-categorize-customers-in-python-with-sql-server-machine-learning-services"></a>Учебник. Подготовка данных для категоризации клиентов в Python с помощью SQL Server Службы машинного обучения

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В второй части серии руководств из четырех частей вы сможете восстановить и подготовить данные из базы данных SQL с помощью Python. Далее в этой серии вы будете использовать эти данные для обучения и развертывания модели кластеризации в Python с помощью SQL Server Службы машинного обучения.

Из этой статьи вы узнаете о следующем:

> [!div class="checklist"]
> * Отделение клиентов по разным измерениям с помощью Python
> * Загрузка данных из базы данных SQL в кадр данных Python

В [первой части](python-clustering-model.md)вы установили необходимые компоненты и восстановили образец базы данных.

В [третьей части](python-clustering-model-build.md)вы узнаете, как создать и обучить модель кластеризации K-средних в Python.

В [части 4](python-clustering-model-deploy.md)вы узнаете, как создать хранимую процедуру в базе данных SQL, которая может выполнять кластеризацию в Python на основе новых данных.

## <a name="prerequisites"></a>Предварительные требования

* В части 2 этого учебника предполагается, что вы выполнили предварительные требования к первой [**части**](python-clustering-model.md).

## <a name="separate-customers"></a>Разделение клиентов

Чтобы подготовиться к кластеризации клиентов, сначала необходимо отделить клиентов по следующим измерениям:

* **ордерратио** = коэффициент возврата (общее количество заказов частично или полностью возвращено, а также общее количество заказов)
* **итемсратио** = коэффициент возвращаемых элементов (общее число возвращенных элементов в сравнении с количеством приобретенных элементов)
* **монетариратио** = коэффициент возврата суммы (всего денежных единиц, возвращенных в сравнении с приобретенным объемом)
* **Частота** = частота возврата

Откройте новую записную книжку в Azure Data Studio и введите следующий скрипт.

В строке подключения при необходимости замените сведения о подключении.

```python
# Load packages.
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import revoscalepy as revoscale
from scipy.spatial import distance as sci_distance
from sklearn import cluster as sk_cluster

################################################################################################

## Connect to DB and select data

################################################################################################

# Connection string to connect to SQL Server named instance.
conn_str = 'Driver=SQL Server;Server=localhost;Database=tpcxbb_1gb;Trusted_Connection=True;'

input_query = '''SELECT
ss_customer_sk AS customer,
ROUND(COALESCE(returns_count / NULLIF(1.0*orders_count, 0), 0), 7) AS orderRatio,
ROUND(COALESCE(returns_items / NULLIF(1.0*orders_items, 0), 0), 7) AS itemsRatio,
ROUND(COALESCE(returns_money / NULLIF(1.0*orders_money, 0), 0), 7) AS monetaryRatio,
COALESCE(returns_count, 0) AS frequency
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
GROUP BY sr_customer_sk ) returned ON ss_customer_sk=sr_customer_sk'''


# Define the columns we wish to import.
column_info = {
    "customer": {"type": "integer"},
    "orderRatio": {"type": "integer"},
    "itemsRatio": {"type": "integer"},
    "frequency": {"type": "integer"}
}
```

## <a name="load-the-data-into-a-data-frame"></a>Загрузка данных в кадр данных

Результаты запроса возвращаются в Python с помощью функции revoscalepy **RxSqlServerData** . В рамках процесса вы будете использовать сведения о столбцах, определенные в предыдущем сценарии.

```python
data_source = revoscale.RxSqlServerData(sql_query=input_query, column_Info=column_info,
                                        connection_string=conn_str)
revoscale.RxInSqlServer(connection_string=conn_str, num_tasks=1, auto_cleanup=False)
# import data source and convert to pandas dataframe.
customer_data = pd.DataFrame(revoscale.rx_import(data_source))
```

Теперь отобразите начало кадра данных, чтобы убедиться, что он выглядит правильно.

```python
print("Data frame:", customer_data.head(n=5))
```

```results
Rows Read: 37336, Total Rows Processed: 37336, Total Chunk Time: 0.172 seconds
Data frame:     customer  orderRatio  itemsRatio  monetaryRatio  frequency
0    29727.0    0.000000    0.000000       0.000000          0
1    97643.0    0.068182    0.078176       0.037034          3
2    57247.0    0.000000    0.000000       0.000000          0
3    32549.0    0.086957    0.068657       0.031281          4
4     2040.0    0.000000    0.000000       0.000000          0
```

## <a name="clean-up-resources"></a>Очистка ресурсов

Если вы не собираетесь продолжать работу с этим руководством, удалите базу данных tpcxbb_1gb из SQL Server.

## <a name="next-steps"></a>Следующие шаги

В второй части этой серии руководств вы выполнили следующие действия:

* Отделение клиентов по разным измерениям с помощью Python
* Загрузка данных из базы данных SQL в кадр данных Python

Чтобы создать модель машинного обучения, которая использует эти данные клиента, следуйте третьей части этой серии руководств:

> [!div class="nextstepaction"]
> [Учебник. Создание прогнозной модели на языке Python с помощью SQL Server Службы машинного обучения](python-clustering-model-build.md)
