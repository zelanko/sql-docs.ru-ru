---
title: Построение гистограммы для изучения данных с помощью Python
titleSuffix: SQL machine learning
description: Узнайте, как создать гистограмму для визуализации данных с помощью Python.
author: cawrites
ms.author: chadam
ms.date: 07/14/2020
ms.topic: how-to
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=azuresqldb-current||=sqlallproducts-allversions'
ms.openlocfilehash: 1a946efdd8da5a64d2475164a1b8057c7b41554f
ms.sourcegitcommit: 8f062015c2a033f5a0d805ee4adabbe15e7c8f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2020
ms.locfileid: "91226851"
---
# <a name="plot-histograms-in-python"></a>Построение гистограмм в Python 
[!INCLUDE[SQL Server SQL DB SQL MI](../../includes/applies-to-version/sql-asdb-asdbmi.md)]

В этой статье описывается построение графиков данных с помощью пакета Python [pandas'.hist()](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.hist.html). База данных SQL — это источник, используемый для визуализации интервалов данных гистограммы, имеющих последовательные, не перекрывающиеся значения.

## <a name="prerequisites"></a>Предварительные требования:

::: moniker range=">=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions"
* SQL Server. Сведения об установке см. в разделе [SQL Server для Windows](../../database-engine/install-windows/install-sql-server.md) или [для Linux](../../linux/sql-server-linux-overview.md).
::: moniker-end

::: moniker range="=azuresqldb-current||=sqlallproducts-allversions"
* База данных SQL Azure. Сведения о регистрации см. в разделе [База данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal).
::: moniker-end

::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
* Управляемый экземпляр SQL Azure. Сведения о регистрации см. в разделе [Управляемый экземпляр SQL Azure](https://docs.microsoft.com/azure/azure-sql/managed-instance/instance-create-quickstart).

* [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) для восстановления образца базы данных в Управляемый экземпляр SQL Azure.
::: moniker-end

* Azure Data Studio. Сведения об установке см. в разделе [Azure Data Studio](../../azure-data-studio/what-is.md).

* [Восстановление образца базы данных DW](../../samples/adventureworks-install-configure.md) для получения демонстрационных данных, используемых в этой статье.

## <a name="verify-restored-database"></a>Проверка восстановленной базы данных

Чтобы убедиться, что восстановленная база данных существует, выполните запрос к таблице **Person.CountryRegion**.
```sql
USE AdventureWorksDW;
SELECT * FROM Person.CountryRegion;
```
  
## <a name="install-python-packages"></a>Установка пакетов Python

[Скачивание и установка Azure Data Studio](../../azure-data-studio/download-azure-data-studio.md).

Установите следующие пакеты Python.
  * pyodbc
  * pandas

  Чтобы установить эти пакеты, выполните приведенные ниже действия.

  1. В записной книжке Azure Data Studio выберите **Управление пакетами**.
  2. В области **Управление пакетами** выберите вкладку **Добавить новые**.
  3. Для каждого из следующих пакетов введите имя пакета, щелкните **Поиск**, а затем **Установить**.

## <a name="plot-histogram"></a>Построение гистограммы

Распределенные данные, отображаемые в гистограмме, основаны на SQL-запросе из AdventureWorksDW. Гистограмма визуализирует данные и частоту значений данных. Измените переменные строки подключения: 'server', 'database', 'username' и 'password' для подключения к базе данных SQL.

Чтобы создать записную книжку:

1. В Azure Data Studio выберите пункт **Файл** и **Новая записная книжка**.
2. В записной книжке выберите ядро **Python3** и нажмите **+ Код**.
3. Вставьте код в записную книжку и нажмите **Запустить все**.

```python
import pyodbc 
import pandas as plt
# Some other example server values are
# server = 'localhost\sqlexpress' # for a named instance
# server = 'myserver,port' # to specify an alternate port
server = 'servername' 
database = 'AdventureWorksDW' 
username = 'yourusername' 
password = 'databasename'  
cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER='+server+';DATABASE='+database+';UID='+username+';PWD='+ password)
cursor = cnxn.cursor()
sql = "SELECT DATEDIFF(year, c.BirthDate, GETDATE()) AS Age FROM [dbo].[FactInternetSales] s INNER JOIN dbo.DimCustomer c ON s.CustomerKey = c.CustomerKey"
df = pd.read_sql(sql, cnxn)
df.hist(bins=10)
```

На экране отобразится распределение возраста клиентов в таблице FactInternetSales.

![Гистограмма Pandas](./media/python-histogram.png)


