---
title: 'Урок 1 изучение и визуализация данных с помощью Python и T-SQL: машинного обучения SQL Server'
description: Руководства, показывающий, как внедрить Python в SQL Server хранимых процедур и функций T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e9dd0a0884c96a8f5b17948c21b7f891a2e997ab
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860495"
---
# <a name="explore-and-visualize-the-data"></a>Анализ и визуализация данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья входит учебник по, [Python в базе данных аналитики для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md). 

На этом шаге вы изучите образец данных и создадите ряд диаграмм. Позже вы узнаете, как сериализовать графических объектов на языке Python и затем десериализовать эти объекты и сделать графики.

## <a name="review-the-data"></a>Просмотрите данные

Во-первых внимательно выполнять обзор схемы данных, как мы внесли некоторые изменения, чтобы упростить использование данных о такси Нью-ЙОРКА

+ Исходный набор данных используется отдельные файлы для идентификаторы такси и записи поездок. Мы объединены исходные наборы данных по столбцам _medallion_, _hack_license_, и _pickup_datetime_.  
+ Исходный набор данных составные большое количество файлов и был довольно большим. Мы улучшили понижаться до получить 1% от исходного количества записей. Текущая таблица данных содержит 1,703,957 строк и 23 столбца.

**Идентификаторы такси**

_Medallion_ столбец представляет уникальный идентификатор такси.

_Hack_license_ столбец содержит драйвера такси номера лицензий (таксистов).

**Записи о поездках и оплате**

Каждая запись о поездке включает сведения о местах посадки и высадки, а также о расстоянии поездки.

Каждая запись об оплате включает такие сведения, как тип оплаты, общий размер платежа и размер чаевых.

Последние три столбца можно использовать для различных задач машинного обучения.  Столбец _tip_amount_ содержит непрерывный ряд числовых значений и может использоваться в качестве столбца **меток** для регрессионного анализа. Столбец _tipped_ содержит значения "Да" или "Нет" и используется для двоичной классификации. Столбец _tip_class_ содержит несколько **меток классов** и поэтому может использоваться в качестве метки для задач многоклассовой классификации.

Все значения, используемые для столбцов меток основаны на `tip_amount` столбца, с помощью этих бизнес-правила:

+ Столбец метки `tipped` принимать значения 0 и 1

    Если `tip_amount` > 0, `tipped` = 1; в противном случае `tipped` = 0

+ Столбец метки `tip_class` классов значения от 0 до 4

    Класс 0: `tip_amount` = 0 долл. США

    Класс 1: `tip_amount` > $0 и `tip_amount` < = $5
    
    Класс 2: `tip_amount` > $5 и `tip_amount` < = $10
    
    Класс 3: `tip_amount` > $10 и `tip_amount` < = $20
    
    Класс 4: `tip_amount` > $20

## <a name="create-plots-using-python-in-t-sql"></a>Создание диаграмм с помощью Python в T-SQL

Разработка решения для обработки и анализа данных обычно связана с большим числом операций по анализу и визуализации данных. Так как визуализация является эффективным средством для представления распределения данных и выбросов, Python имеется много пакетов для визуализации данных. **Matplotlib** модуль является одним из наиболее популярных библиотек для визуализации и включает в себя множество функций для создания гистограмм, точечных диаграмм, блочных диаграмм и других диаграммах исследования данных.

В этом разделе вы узнаете, как работать с графиков с помощью хранимых процедур. А чем открыть изображение на сервере, сохраните объект Python `plot` как **varbinary** данных, а затем написать, что в файл, можно совместно или просмотреть в другом месте.

### <a name="create-a-plot-as-varbinary-data"></a>Создать диаграмму как данные типа varbinary

Хранимая процедура возвращает сериализованный Python `figure` объект как поток **varbinary** данных. Двоичные данные нельзя просмотреть напрямую, но можно использовать код Python на клиенте для десериализации и просматривать данные, а затем сохраните файл изображения на клиентском компьютере.

1. Создайте хранимую процедуру **PyPlotMatplotlib**, если сценарий PowerShell оно уже не было.

    - Переменная `@query` определяет текст запроса `SELECT tipped FROM nyctaxi_sample`, передаваемый в блоке кода Python, указывается в качестве аргумента входной переменной, `@input_data_1`.
    - Скрипт Python довольно проста: **matplotlib** `figure` объекты используются, чтобы гистограмме и точечной диаграммы, и эти объекты затем сериализуются с помощью `pickle` библиотеки.
    - Python графический объект сериализуется в **pandas** таблицы данных для выходных данных.
  
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

2. Теперь запустите хранимую процедуру для создания диаграммы на основе данных, жестко задать в качестве входного запроса без аргументов.

    ```sql
    EXEC [dbo].[PyPlotMatplotlib]
    ```

3. Результаты должны выглядеть следующим образом:
  
    ```sql
    plot
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    ```

  
4. Из [клиента Python](../python/setup-python-client-tools-sql.md), теперь можно подключиться к экземпляру SQL Server, вызвавшего построения двоичных объектов и просматривать графики. 

    Чтобы сделать это, выполните следующий код Python, заменив имя сервера, имя базы данных и учетные данные соответствующим образом. Убедитесь, что установлена версия Python, так же, на клиенте и сервере. Кроме того, убедитесь, что библиотек Python на клиенте (например, matplotlib) используются тем же или более поздней версии относительно библиотеки, установленные на сервере.
  
    **С помощью проверки подлинности SQL Server:**
    
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

    **С помощью проверки подлинности Windows:**

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

5.  Если подключение установлено успешно, вы увидите примерно следующее сообщение:
  
    *Графики сохраняются в каталоге: xxxx*
  
6.  Выходной файл создается в рабочем каталоге Python. Чтобы просмотреть диаграмму, найдите рабочий каталог Python и откройте файл. На следующем рисунке показана построения, сохраненные на клиентском компьютере.
  
    ![Сумма Fare vs сумма чаевых](media/sqldev-python-sample-plot.png "Fare vs сумма чаевых") 

## <a name="next-step"></a>Следующий шаг

[Создание функций данных с помощью T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Предыдущий шаг

[Скачать набор данных о такси Нью-ЙОРКА](demo-data-nyctaxi-in-sql.md)

