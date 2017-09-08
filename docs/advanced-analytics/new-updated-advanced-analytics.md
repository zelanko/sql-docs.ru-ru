---
title: "Обновить - Advanced Analytics для документации по SQL Server | Документы Microsoft"
description: "Отображение фрагментов обновленное содержимое для последних измененных в документации, Advanced Analytics в Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 07/17/2017
ms.author: genemi
ms.workload: advanced-analytics
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 79f979ecda1ff0851978d19ef28fa3cf909f9a43
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Новые и недавно обновленные: Advanced Analytics для SQL Server



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат для обновлений:* &nbsp; **23.05.2017** &nbsp;—&nbsp; **17.07.2017**
- *Предметной области:* &nbsp; **Advanced Analytics для SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые были добавлены недавно.


1. [Распространенные проблемы с выполнением внешних скриптов](common-issues-external-script-execution.md)
2. [Сбор данных для устранения неполадок машинного обучения](data-collection-ml-troubleshooting-process.md)
3. [Учебники по SQL Server Python](tutorials/sql-server-python-tutorials.md)
4. [Учебники по SQL Server R](tutorials/sql-server-r-tutorials.md)




&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно были внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-introducing-revoscalepypythonwhat-is-revoscalepymd"></a>1. &nbsp;[Знакомство с revoscalepy](python/what-is-revoscalepy.md)

*Обновление: 23.06.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Далее](#TitleNum_2))

<!-- Source markdown line 112.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 cab7330ac9944508aaa360e00cbc2e866455776d 33f4e0e2421fa79fc11931dc7f29bff4432c6f5a  (PR=2171  ,  Filename=what-is-revoscalepy.md  ,  Dirpath=docs\advanced-analytics\python\  ,  MergeCommitSha40=7d2dbe0bdc4cbd05f11eacf938b35a9c35ace2e7) -->



**Использование revoscalepy с MicrosoftML**


Функции Python для MicrosoftML интегрированы с контекстов вычислений и источники данных, которые содержатся в revoscalepy. Таким образом можно использовать алгоритм MicrosoftML для определения и обучения модели на Python и использовать функции revoscalepy для выполнения кода Python, локально или в контексте вычислений SQl Server.

Импортировать модули в коде Python и затем ссылаться на отдельные функции, что нужно.

```
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

**Требования**


Для выполнения кода Python в SQL Server, необходимо установить 2017 г. SQL Server вместе с функцию **службы обучения машины**и включен языка Python. SQL Server более ранних версий не поддерживают интеграции Python.

> [!NOTE]
> Контексты вычислений SQL Server не поддерживают дистрибутивов открытым исходным кодом Python. Тем не менее если требуется для публикации и использования приложений Python из Windows, можно установить Microsoft Server обучения машины без установки SQL Server. Дополнительные сведения см. раздел [создание автономного R Server--... /r/Create-a-standalone-r-Server.MD)

**Дополнительная справка**





&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-step-5-train-and-save-a-model-using-t-sqltutorialssqldev-py5-train-and-save-a-model-using-t-sqlmd"></a>2. &nbsp;[Шаг 5: обучение и сохранить модель с помощью T-SQL](tutorials/sqldev-py5-train-and-save-a-model-using-t-sql.md)

*Обновлено: 2017 г-06-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 121.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5c1cbe92282b96105ffdb69efa803f58dc0ac7e2 e4077a2154a90de468c435efa5b2225125d5b0e7  (PR=1904  ,  Filename=sqldev-py5-train-and-save-a-model-using-t-sql.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=dbf91e0d6f8257227cfe8ac6d13c484d0a566f57) -->



1. В [! ВКЛЮЧИТЬ [ssManStudio--... /../includes/ssManStudio-MD.MD)], откройте новое окно запроса и выполните следующую инструкцию, чтобы создать хранимую процедуру _TrainTipPredictionModelRxPy_.  Эта модель будет основана на подготовленном просто обучающих данных. Так как хранимая процедура уже содержит определение входных данных, не требуется для предоставления входного запроса.

    ```SQL
    DROP PROCEDURE IF EXISTS TrainTipPredictionModelRxPy;
    GO

    CREATE PROCEDURE [dbo].[TrainTipPredictionModelRxPy] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script 
      @language = N'Python',
      @script = N'
    import numpy
    import pickle
    import pandas
    from revoscalepy.functions.RxLogit import rx_logit_ex
    
    ## Create a logistic regression model using rx_logit_ex function from revoscalepy package
    logitObj = rx_logit_ex("tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance", data = InputDataSet);
    
    ## Serialize model
    trained_model = pickle.dumps(logitObj)
    ',
    @input_data_1 = N'
    select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
    from nyctaxi_sample_training
    ',
    @input_data_1_name = N'InputDataSet',
    @params = N'@trained_model varbinary(max) OUTPUT',
    @trained_model = @trained_model OUTPUT;
    ;
    END;
    ```



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-step-6-operationalize-the-modeltutorialssqldev-py6-operationalize-the-modelmd"></a>3. &nbsp;[Шаг 6: модели ввода в эксплуатацию](tutorials/sqldev-py6-operationalize-the-model.md)

*Обновлено: 2017 г-06-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_2) | [Далее](#TitleNum_4))

<!-- Source markdown line 236.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1eb50ac902d4e80bafb1dd7fdf8f607dcdf0d33f 57d5abdc6119db1ecd81587d625054a5bbfb5fc8  (PR=1904  ,  Filename=sqldev-py6-operationalize-the-model.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=dbf91e0d6f8257227cfe8ac6d13c484d0a566f57) -->



Вот определение хранимой процедуры, которая выполняет вычисления с помощью **revoscalepy** модели.

```
CREATE PROCEDURE [dbo].[PredictTipSingleModeRxPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
  DECLARE @inquery nvarchar(max) = N'
    SELECT * FROM [dbo].[fnEngineerFeatures-- 
      @passenger_count,
      @trip_distance,
      @trip_time_in_secs,
      @pickup_latitude,
      @pickup_longitude,
      @dropoff_latitude,
      @dropoff_longitude)
    '
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      from revoscalepy.functions.RxPredict import rx_predict_ex;
```




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-use-python-with-revoscalepy-to-create-a-modeltutorialsuse-python-revoscalepy-to-create-modelmd"></a>4. &nbsp;[Использование Python с revoscalepy для создания модели](tutorials/use-python-revoscalepy-to-create-model.md)

*Обновлено: 2017 г-06-21* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_3))

<!-- Source markdown line 119.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0886939f86fe12d7ff7b339689a02c7fc75e0786 23dd469349a05d535063aab3c14aec152ed2cd7b  (PR=2141  ,  Filename=use-python-revoscalepy-to-create-model.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=76839e39427e24688609353b8708d59fee772d28) -->



**Просмотрите код**


Позволяет просмотреть код и выделите некоторых ключевых шагов.

**Определение данных источника и контекста вычислений**


Это является важной частью использования **revoscalepy** и его связанный пакет R **RevoScaleR**. Источник данных отличается от контекст вычислений. _Источника данных_ определяет данные, используемые в коде. _Контекста вычислений_ определяет, где будет выполняться код.

> [!NOTE]
> Поддержка для некоторых типов источников данных, поддерживаемые в RevoScaleR могут быть ограничены в предварительной версии. Дополнительные сведения о функциях, включенных в последнем выпуске см. в разделе [новые возможности revoscalepy--... /Python/What-is-revoscalepy.MD).

Всего процессов для создания и использования источника данных и вычислений контекста таков:

1. Создание переменных Python, таких как _SQL-запрос_ и _connectionString_, определяющие источник и данные, которые вы хотите использовать. Передавать эти переменные для **RxSqlServerData** конструктор, чтобы реализовать **объекта источника данных** с именем _dataSource_.
2. Создать объект контекста вычислений с помощью **RxInSqlServer** конструктор. В этом примере передать та же строка подключения, созданного ранее, предполагается, что данные находятся на одном экземпляре SQL Server, на котором будет выполняться в контексте. Тем не менее источник данных и контекст вычислений может находиться на разных серверах. Итоговый **объект контекста вычислений** называется _computeContext_.
3. Выберите активный контекст. По умолчанию операции выполняются локально, это значит, что если не указать контекст различных вычислений, данные будут получены из источника данных и модели Подгонка будет работать в текущей среды Python.

    В RevoScaleR, можно также использовать функцию `rxSetComputeContext` для переключения между контекстов вычислений. Функция еще не реализован в предварительной версии **revoscalepy**, но можно указать контекст вычислений в качестве аргумента для **rx_lin_mod_ex**.





<a name="similars2"/>

&nbsp;

## <a name="similar-articles"></a>Похожие статьи

Этот раздел содержит похожие статьи, аналогичные недавно измененным, для других предметных областей в том же репозитории GitHub.com: [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/).

<!--  20170717-1101  -->

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новые + обновленные (4+4): **Расширенная аналитика для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (2+0): **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (1+2): **Подключение к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (6+0): **Ядро СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (13+2): **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (1+0): **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (1+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (8+4): **Реляционные базы данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (2+2): **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (0+1): **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (1+0): **Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Новые + обновленные (1+0): **Инструменты для SQL**](../tools/new-updated-tools.md)


#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (0+0): **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (0+0): **помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)


&nbsp;


