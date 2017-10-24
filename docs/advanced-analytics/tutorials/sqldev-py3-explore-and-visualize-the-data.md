---
title: "Шаг 3: Анализ и визуализация данных | Документы Microsoft"
ms.custom: 
ms.date: 10/17/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-python
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2f28400200105e8e63f787cbcda58c183ba00da5
ms.openlocfilehash: 31fa666c98948dc18f7aad988de795809594d2dd
ms.contentlocale: ru-ru
ms.lasthandoff: 10/18/2017

---
# <a name="step-3-explore-and-visualize-the-data"></a>Шаг 3: Анализ и визуализация данных

В этой статье является частью учебника [analytics Python в базе данных для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md). 

На этом шаге Просмотр образцов данных и создать некоторые графики. Позже вы узнаете, как сериализовать объекты графики в Python и затем десериализации этих объектов и производить графики.

## <a name="review-the-data"></a>Проверка данных

Во-первых прежде всего Обзор схеме данных, как мы внесли некоторые изменения, чтобы упростить использование данных такси NYC

+ Исходный набор данных использовать отдельные файлы для обработки записей и идентификаторов такси. Мы объединенные два исходного набора данных по столбцам _medallion_, _hack_license_, и _pickup_datetime_.  
+ Исходный набор данных охваченных много файлов и довольно велик. У нас понижаться до получения только 1% от первоначального количества записей. Текущая таблица данных содержит 1,703,957 строки и столбцы, 23.

**Идентификаторы такси**

_Medallion_ столбец представляет такси уникальный Идентификационный номер.

_Hack_license_ столбец содержит номер соглашения драйвер такси (анонимизированы).

**Записи о поездках и оплате**

Каждая запись о поездке включает сведения о местах посадки и высадки, а также о расстоянии поездки.

Каждая запись об оплате включает такие сведения, как тип оплаты, общий размер платежа и размер чаевых.

Последние три столбца можно использовать для различных задач машинного обучения.  Столбец _tip_amount_ содержит непрерывный ряд числовых значений и может использоваться в качестве столбца **меток** для регрессионного анализа. Столбец _tipped_ содержит значения "Да" или "Нет" и используется для двоичной классификации. Столбец _tip_class_ содержит несколько **меток классов** и поэтому может использоваться в качестве метки для задач многоклассовой классификации.

Значения, используемые для меток столбцов основаны на `tip_amount` столбца, с помощью этих бизнес-правила:

+ Столбец метки `tipped` может принимать значения 0 и 1

    Если `tip_amount` > 0, `tipped` = 1; в противном случае `tipped` = 0

+ Столбец метки `tip_class` имеет классов значений от 0 до 4

    Класс 0: `tip_amount` = $0

    Класс 1: `tip_amount` > $0 и `tip_amount` < = $5
    
    Класс 2: `tip_amount` > $5 и `tip_amount` < = 10
    
    Класс 3: `tip_amount` > 10 долларов и `tip_amount` < = 20
    
    Класс 4: `tip_amount` > 20

## <a name="create-plots-using-python-in-t-sql"></a>Создание диаграммы с помощью Python в T-SQL

Разработка решения для обработки и анализа данных обычно связана с большим числом операций по анализу и визуализации данных. Поскольку визуализация таких мощное средство для понимания распределения данных и выбросов, Python предоставляет многие пакеты для визуализации данных. **Matplotlib** модуль является одним из более популярных библиотек для визуализации и имеется множество функций для создания гистограммы, точечных диаграмм, графиков поле и других диаграммах исследования данных.

В этом разделе вы узнаете, как работать с графики с помощью хранимых процедур. А чем открыть изображение на сервере, сохранения объекта Python `plot` как **varbinary** данных, а затем написать, что в файле, можно будет совместно или просмотреть в другом месте.

### <a name="create-a-plot-as-varbinary-data"></a>Создать диаграмму как данные типа varbinary

**Revoscalepy** модуля, входящий в состав служб SQL Server 2017 г машины обучения поддерживает функции, аналогичные доступным в **RevoScaleR** пакета для R.  В этом примере используется эквивалент Python `rxHistogram` строится Гистограмма, на основе данных из [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса. 

Хранимая процедура возвращает сериализованный Python `figure` объект как поток **varbinary** данных. Двоичные данные нельзя просматривать непосредственно, но можно использовать код Python на стороне клиента для десериализации и просматривать данные и затем сохраните файл изображения на клиентском компьютере.

1. Создайте хранимую процедуру _SerializePlots_, если сценарий PowerShell это уже не сделано.

    - Переменная `@query` определяет текст запроса `SELECT tipped FROM nyctaxi_sample`, который передается блоку кода Python в качестве аргумента для входной переменной сценария `@input_data_1`.
    - Сценарий Python очень прост: **matplotlib** `figure` объектов используются для создания гистограмме и точечной диаграмме, и эти объекты сериализуются с помощью `pickle` библиотеки.
    - Python графический объект сериализуется в **pandas** кадр данных для вывода.
  
    ```SQL
    CREATE PROCEDURE [dbo].[SerializePlots]
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

2. Теперь запустите хранимую процедуру без аргументов для создания диаграммы из данных, жестко задать в качестве входного запроса.

    ```
    EXEC [dbo].[SerializePlots]
    ```

3. Результаты должны выглядеть следующим образом:
  
    ```
    plot
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    ```

  
4. От клиента Python можно теперь подключитесь к экземпляру SQL Server, вызвавшего построения двоичных объектов и просматривать графики. 

    Чтобы сделать это, выполните следующий код Python, заменив имя сервера, имя базы данных и учетные данные, соответствующие. Убедитесь, что версия Python является одинаковым на клиент и сервер. Убедитесь, что библиотеки Python на клиентском компьютере (например, matplotlib) используются одной или более поздней версии относительно библиотеки, установленные на сервере.
  
    **С помощью проверки подлинности SQL Server:**
    
    ```python
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER={SERVER_NAME};DATABASE={DB_NAME};UID={USER_NAME};PWD={PASSWORD}')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[SerializePlots]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

    **Использование проверки подлинности Windows.**

    ```python
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER={SERVER_NAME};DATABASE={DB_NAME};Trusted_Connection=yes;')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[SerializePlots]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

5.  Если соединение установлено успешно, появится сообщение, подобное следующему:
  
    *Графики сохраняются в каталоге: xxxx*
  
6.  Выходной файл создается в рабочем каталоге Python. Чтобы просмотреть график, найдите рабочий каталог Python и откройте файл. На следующем рисунке показана построения, сохраняются на клиентском компьютере.
  
    ![Совет тариф авиакомпании vs сумма сумма](media/sqldev-python-sample-plot.png "vs тариф авиакомпании совет сумма сумма") 

## <a name="next-step"></a>Следующий шаг

[Шаг 4. Создание функций данных с помощью T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Предыдущий шаг

[Шаг 2. Импорт данных в SQL Server с помощью PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)


