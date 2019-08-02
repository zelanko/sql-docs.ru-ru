---
title: Занятие 1. Просмотр и визуализация данных с помощью Python и T-SQL
description: Учебник, демонстрирующий внедрение Python в SQL Server хранимых процедур и функций T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6ee82de1431a6bc21596505dc4b008b817b35830
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714707"
---
# <a name="explore-and-visualize-the-data"></a>Просмотр и визуализация данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта статья является частью руководства, [в базе данных Python Analytics для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md). 

На этом шаге вы просматриваете образец данных и создаете несколько графиков. Далее вы узнаете, как сериализовать графические объекты в Python, а затем десериализовать эти объекты и создать диаграммы.

## <a name="review-the-data"></a>Проверка данных

Во-первых, просмотрите схему данных, Потратьте несколько минут, так как мы внесли некоторые изменения, чтобы упростить использование данных НЬЮного такси.

+ В исходном наборе данных используются отдельные файлы для идентификаторов такси и записей поездки. Мы присоединили два исходных набора данных к столбцам _Medallion_, _hack_license_и _pickup_datetime_.  
+ Исходный набор данных имеет много файлов и был довольно большим. Мы downsampled на получение всего 1% от исходного количества записей. Текущая таблица данных содержит 1 703 957 строк и 23 столбца.

**Идентификаторы такси**

Столбец _Medallion_ представляет уникальный идентификационный номер такси.

Столбец _hack_license_ содержит номер лицензии для драйвера такси (анонимный).

**Записи о поездках и оплате**

Каждая запись о поездке включает сведения о местах посадки и высадки, а также о расстоянии поездки.

Каждая запись об оплате включает такие сведения, как тип оплаты, общий размер платежа и размер чаевых.

Последние три столбца можно использовать для различных задач машинного обучения.  Столбец _tip_amount_ содержит непрерывный ряд числовых значений и может использоваться в качестве столбца **меток** для регрессионного анализа. Столбец _tipped_ содержит значения "Да" или "Нет" и используется для двоичной классификации. Столбец _tip_class_ содержит несколько **меток классов** и поэтому может использоваться в качестве метки для задач многоклассовой классификации.

Значения, используемые для столбцов меток, основаны на `tip_amount` столбце, используя следующие бизнес-правила:

+ Столбец `tipped` меток может иметь значения 0 и 1

    Если `tip_amount` > 0, `tipped` = 1; в `tipped` противном случае — 0

+ Столбец `tip_class` меток имеет возможные значения класса 0-4

    Класс 0: `tip_amount` = $0

    Класс 1: `tip_amount` > $0 и `tip_amount` < = $5
    
    Класс 2. `tip_amount` > $5 и `tip_amount` < = $10
    
    Класс 3. `tip_amount` > $10 и `tip_amount` < = $20
    
    Класс 4. `tip_amount` > $20

## <a name="create-plots-using-python-in-t-sql"></a>Создание графиков с помощью Python в T-SQL

Разработка решения для обработки и анализа данных обычно связана с большим числом операций по анализу и визуализации данных. Поскольку визуализация — это мощный инструмент для понимания распределения данных и выбросов, Python предоставляет множество пакетов для визуализации данных. Модуль **Matplotlib** является одной из наиболее популярных библиотек для визуализации и включает множество функций для создания гистограмм, точечных диаграмм, блочных диаграмм и других графов просмотра данных.

В этом разделе вы узнаете, как работать с графикой с помощью хранимых процедур. Вместо того чтобы открывать образ на сервере, вы сохраняете объект `plot` Python как данные типа **varbinary** , а затем записываете его в файл, который можно совместно использовать или просматривать в других местах.

### <a name="create-a-plot-as-varbinary-data"></a>Создание графика как данных типа varbinary

Хранимая процедура возвращает сериализованный объект Python `figure` в виде потока данных типа **varbinary** . Двоичные данные нельзя просматривать напрямую, но можно использовать код Python на клиенте для десериализации и просмотра рисунков, а затем сохранить файл изображения на клиентском компьютере.

1. Создайте хранимую процедуру **пиплотматплотлиб**, если сценарий PowerShell еще не сделал этого.

    - Переменная `@query` определяет текст `SELECT tipped FROM nyctaxi_sample`запроса, который передается блоку кода Python в качестве аргумента входной переменной `@input_data_1`скрипта.
    - Сценарий Python довольно прост: объекты **Matplotlib** `figure` используются для создания гистограммы и точечной диаграммы, и эти объекты затем `pickle` сериализуются с помощью библиотеки.
    - Объект Graphics в Python сериализуется в кадр данных **Pandas** для вывода.
  
    ```sql
    DROP PROCEDURE IF EXISTS PyPlotMatplotlib;
    GO

    CREATE PROCEDURE [dbo].[PyPlotMatplotlib]
    AS
    BEGIN
        SET NOCOUNT ON;
        DECLARE @query nvarchar(max) =
        N'SELECT cast(tipped as int) as tipped, tip_amount, fare_amount FROM [dbo].[nyctaxi_sample]'
        EXECUTE sp_execute_external_script
        @language = N'Python',
        @script = N'
    import matplotlib
    matplotlib.use("Agg")
    import matplotlib.pyplot as plt
    import pandas as pd
    import pickle

    fig_handle = plt.figure()
    plt.hist(InputDataSet.tipped)
    plt.xlabel("Tipped")
    plt.ylabel("Counts")
    plt.title("Histogram, Tipped")
    plot0 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.hist(InputDataSet.tip_amount)
    plt.xlabel("Tip amount ($)")
    plt.ylabel("Counts")
    plt.title("Histogram, Tip amount")
    plot1 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.hist(InputDataSet.fare_amount)
    plt.xlabel("Fare amount ($)")
    plt.ylabel("Counts")
    plt.title("Histogram, Fare amount")
    plot2 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.scatter( InputDataSet.fare_amount, InputDataSet.tip_amount)
    plt.xlabel("Fare Amount ($)")
    plt.ylabel("Tip Amount ($)")
    plt.title("Tip amount by Fare amount")
    plot3 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    OutputDataSet = plot0.append(plot1, ignore_index=True).append(plot2, ignore_index=True).append(plot3, ignore_index=True)
    ',
    @input_data_1 = @query
    WITH RESULT SETS ((plot varbinary(max)))
    END
    GO
    ```

2. Теперь запустите хранимую процедуру без аргументов, чтобы создать график на основе данных, жестко запрограммированных в качестве входного запроса.

    ```sql
    EXEC [dbo].[PyPlotMatplotlib]
    ```

3. Результаты должны быть примерно такими:
  
    ```sql
    plot
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    ```

  
4. С помощью [клиента Python](../python/setup-python-client-tools-sql.md)теперь можно подключаться к экземпляру SQL Server, который создал двоичные объекты построения, и просматривать графики. 

    Для этого выполните следующий код Python, заменив имя сервера, имя базы данных и учетные данные соответствующим образом. Убедитесь, что версия Python одинакова на клиенте и на сервере. Также убедитесь, что библиотеки Python на вашем клиенте (например, Matplotlib) имеют ту же или более позднюю версию относительно библиотек, установленных на сервере.
  
    **Использование проверки подлинности SQL Server:**
    
    ```python
    %matplotlib notebook
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER=SQL Server;SERVER={SERVER_NAME};DATABASE={DB_NAME};UID={USER_NAME};PWD={PASSWORD}')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[PyPlotMatplotlib]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

    **Использование проверки подлинности Windows:**

    ```python
    %matplotlib notebook
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER=SQL Server;SERVER={SERVER_NAME};DATABASE={DB_NAME};Trusted_Connection=True;')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[PyPlotMatplotlib]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

5.  Если подключение установлено успешно, должно отобразиться сообщение следующего вида:
  
    *Графики сохраняются в каталоге: XXXX.*
  
6.  Выходной файл создается в рабочем каталоге Python. Чтобы просмотреть график, перейдите к рабочему каталогу Python и откройте файл. На следующем рисунке показана диаграмма, сохраненная на клиентском компьютере.
  
    ![Сумма TIP и сумма FARE](media/sqldev-python-sample-plot.png "Сумма TIP и сумма FARE") 

## <a name="next-step"></a>Следующий шаг

[Создание функций данных с помощью T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Предыдущий шаг

[Скачайте набор данных Нью такси](demo-data-nyctaxi-in-sql.md)

