---
title: "Шаг 3. Анализ и визуализация данных | Документация Майкрософт"
ms.custom: 
ms.date: 05/25/2017
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
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dfb80fcd3241b22f0ac72c2cf4cd8a18d1add857
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="step-3-explore-and-visualize-the-data"></a>Шаг 3. Анализ и визуализация данных

Разработка решения для обработки и анализа данных обычно связана с большим числом операций по анализу и визуализации данных. На этом шаге будет Просмотр образцов данных и создать некоторые графики. Более поздней версии вы узнаете, как сериализации графических объектов в Python и затем выполнить десериализацию данных объектов и производить графики.

> [!NOTE]
> В этом пошаговом руководстве показано только задачи двоичной классификации; Мы приглашаем вас построении отдельных моделей для задачи двух машинного обучения, регрессии и других мультиклассовой классификации.

## <a name="review-the-data"></a>Изучение данных

В исходном наборе данных идентификаторы такси и записи о поездках были предоставлены в отдельных файлах. Однако, чтобы образец данных было удобнее использовать, исходные наборы данных были объединены по столбцам _medallion_, _hack_license_и _pickup_datetime_.  Кроме того, была произведена выборка записей с целью получить 1 % от их общего числа. Полученный набор данных содержит 1 703 957 строк и 23 столбца.

**Идентификаторы такси**

- В столбце _medallion_ представлены уникальные идентификационные номера такси.
- В столбце _hack_license_ содержатся номера лицензий таксистов (без указания имен).

**Записи о поездках и оплате**

- Каждая запись о поездке включает сведения о местах посадки и высадки, а также о расстоянии поездки.
- Каждая запись об оплате включает такие сведения, как тип оплаты, общий размер платежа и размер чаевых.
- Последние три столбца можно использовать для различных задач машинного обучения.  Столбец _tip_amount_ содержит непрерывный ряд числовых значений и может использоваться в качестве столбца **меток** для регрессионного анализа. Столбец _tipped_ содержит значения "Да" или "Нет" и используется для двоичной классификации. Столбец _tip_class_ содержит несколько **меток классов** и поэтому может использоваться в качестве метки для задач многоклассовой классификации.
- Все значения, используемые для столбцов меток, основаны на столбце _tip_amount_ с применением следующих бизнес-правил:
  
    |Имя производного столбца|Правило|
    |-|-|
     |tipped|If tip_amount > 0, tipped = 1, otherwise tipped = 0|
    |tip_class|Class 0: tip_amount = $0<br /><br />Class 1: tip_amount > $0 and tip_amount <= $5<br /><br />Class 2: tip_amount > $5 and tip_amount <= $10<br /><br />Class 3: tip_amount > $10 and tip_amount <= $20<br /><br />Class 4: tip_amount > $20|

## <a name="create-plots-using-python-in-t-sql"></a>Создание диаграммы с помощью Python в T-SQL

Поскольку визуализация таких мощное средство для понимания распределения данных и выбросов, Python предоставляет многие пакеты для визуализации данных. **Matplotlib** модуль — это популярный библиотека, которая включает в себя множество функций для создания гистограммы, точечных диаграмм, графиков поле и других диаграммах исследования данных.

В этом разделе вы узнаете, как работать с графики с помощью хранимых процедур. Будут храниться `plot` Python объекта в виде **varbinary** данных введите и сохраните графики, созданный на сервере.

### <a name="storing-plots-as-varbinary-data-type"></a>Сохранение диаграмм с типом данных varbinary

**Revoscalepy** модуля, входящий в состав служб SQL Server 2017 г машины обучения содержит библиотеки аналогом библиотеки R в пакета RevoScaleR. В этом примере будет использоваться эквивалент Python `rxHistogram` строится Гистограмма, на основе данных из [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса. Чтобы упростить, будет поместить его в хранимой процедуре, _PlotHistogram_.

Хранимая процедура возвращает сериализованный Python `figure` объект как поток **varbinary** данных. Двоичные данные нельзя просматривать непосредственно, но можно использовать код Python на стороне клиента для десериализации и просматривать данные и затем сохраните файл изображения на клиентском компьютере.

### <a name="create-the-stored-procedure-plotspython"></a>Создайте хранимую процедуру Plots_Python

1.  В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], откройте новый **запроса** окна.

2.  Выберите базу данных, предназначенную для пошагового руководства, и создайте процедуру с помощью приведенной ниже инструкции. При необходимости замените имя таблицы в коде на нужное.
  
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
**Примечания.**

- Переменная `@query` определяет текст запроса (`'SELECT tipped FROM nyctaxi_sample'`), который передается блоку кода Python в качестве аргумента для входной переменной сценария `@input_data_1`.
- Сценарий Python очень прост: **matplotlib** `figure` объектов используются для создания гистограмме и точечной диаграмме, и эти объекты сериализуются с помощью `pickle` библиотеки.
- Python графический объект сериализуется в Python **pandas** кадр данных для вывода.

### <a name="output-varbinary-data-to-viewable-graphics-file"></a>Выходные данные varbinary файл можно просматривать графики

1.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]выполните следующую инструкцию:
  
    ```
    EXEC [dbo].[SerializePlots]
    ```
  
    **Результаты**
  
    *построения*
    *0xFFD8FFE000104A4649... * 
     *0xFFD8FFE000104A4649... * 
     *0xFFD8FFE000104A4649... * 
     *0xFFD8FFE000104A4649...*

  
2.  На клиентском компьютере запустите следующий код Python, заменив имя сервера, имя базы данных и учетные данные, соответствующие.
  
    **Для проверки подлинности SQL server:**
    
        ```python
        import pyodbc
        import pickle
        import os
        cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER={SERVER_NAME};DATABASE={DB_NAME};UID={USER_NAME};PWD={PASSOWRD}')
        cursor = cnxn.cursor()
        cursor.execute("EXECUTE [dbo].[SerializePlots]")
        tables = cursor.fetchall()
        for i in range(0, len(tables)):
            fig = pickle.loads(tables[i][0])
            fig.savefig(str(i)+'.png')
        print("The plots are saved in directory: ",os.getcwd())
        ```  
    **Для проверки подлинности Windows:**

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

    > [!NOTE]
    > Убедитесь, что версия Python является одинаковым на клиент и сервер. Кроме того убедитесь, что библиотеки Python, которую вы используете на клиентском компьютере (например, matplotlib) относятся к одной или более поздняя версия относительно библиотеки, установленные на сервере.


3.  Если соединение установлено успешно, вы увидите результаты ниже
  
    *Графики сохраняются в каталоге: xxxx*
  
4.  Выходной файл будет создан в рабочем каталоге Python. Чтобы просмотреть график, просто откройте рабочий каталог Python. Ниже приведен пример построения сохраняются на клиентском компьютере.
  
    ![Совет тариф авиакомпании vs сумма сумма](media/sqldev-python-sample-plot.png "vs тариф авиакомпании совет сумма сумма") 

## <a name="next-step"></a>Следующий шаг

[Шаг 4. Создание характеристик данных с помощью T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Предыдущий шаг

[Шаг 2. Импорт данных в SQL Server с помощью PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="see-also"></a>См. также:

[Машинного обучения служб с Python](../python/sql-server-python-services.md)

