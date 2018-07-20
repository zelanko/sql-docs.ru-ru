---
title: Predict and plot из модели, с помощью языка R в SQL Server машинного обучения и примеры | Документация Майкрософт
description: В этом кратком руководстве Узнайте оценки с использованием готовых моделей данных R и SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 60e152948945f4e86cc1114ae7b20c0e48b403bf
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086656"
---
# <a name="quickstart-predict-and-plot-from-model-using-r-in-sql-server"></a>Краткое руководство: Predict and plot и из модели, с помощью языка R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом кратком руководстве используйте модель, созданную в предыдущем кратком руководстве для оценки прогнозы на основе новых данных. Для выполнения _оценки_ на основе новых данных, получить один из обученной модели из таблицы, а затем вызвать новый набор данных, на которой будет производиться прогнозирование. Оценка — это термин, иногда этот термин используется обработки и анализа данных для обозначения создания прогнозов, вероятности и другие значения, на основе новых данных, поступающих в обученной модели.

## <a name="prerequisites"></a>предварительные требования

В этом кратком руководстве является расширением [Создание модели прогнозирования](rtsql-create-a-predictive-model-r.md).

## <a name="create-the-table-of-new-speeds"></a>Создание таблицы с новыми значениями скорости

Вы заметили, что значение скорости в исходных данных для обучения останавливается на 25 милях в час? Это потому, что эти исходные данные взяты из эксперимента, проведенного в 1920 году.

Вы можете задаться вопросом: сколько же времени потребуется автомобилю 1920-х, чтобы прекратить движение, при условии, что максимальное значение скорости — 60 или даже 100 миль/ч? Чтобы ответить на этот вопрос, необходимо предоставить новые значения скорости.

```sql
CREATE TABLE [dbo].[NewCarSpeed]([speed] [int] NOT NULL,
    [distance] [int]  NULL) ON [PRIMARY]
GO
INSERT [dbo].[NewCarSpeed] (speed)
VALUES (40),  (50),  (60), (70), (80), (90), (100)
```

## <a name="predict-stopping-distance"></a>Прогнозирование тормозного пути

Таблица может содержать несколько моделей R, созданных с помощью различных параметров и алгоритмов или обученных на основе разных подмножеств данных.

![rsql_basictut_listofmodels](media/rsql-basictut-listofmodels.png)

Чтобы получить прогнозы, основанные на одной конкретной модели, необходимо написать скрипт SQL, который выполняет следующие функции:

1. Получение требуемой модели.
2. Получение новых входных данных.
3. Вызов функции прогнозирования R, совместимой с моделью.

В этом примере так, как используемая модель основана на **rxLinMod** алгоритма, предоставляемые как часть **RevoScaleR** пакет, вызовите [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) функции, а не Универсальный R `predict` функции.

```sql
DECLARE @speedmodel varbinary(max) = (SELECT model FROM [dbo].[stopping_distance_models] WHERE model_name = 'latest model');
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(speedmodel));
            new <- data.frame(NewCarData);
            predicted.distance <- rxPredict(current_model, new);
            str(predicted.distance);
            OutputDataSet <- cbind(new, ceiling(predicted.distance));
            '
    , @input_data_1 = N'SELECT speed FROM [dbo].[NewCarSpeed]'
    , @input_data_1_name = N'NewCarData'
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ Используйте инструкцию SELECT для получения одной модели из таблицы и передайте ее в качестве входного параметра.
+ После получения модели из таблицы вызовите функцию `unserialize` для модели.

    > [!TIP] 
    > Также ознакомьтесь с новой [функции сериализации](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) предоставляемые RevoScaleR, который поддерживает [оценки в реальном времени](../real-time-scoring.md).
+  Примените функцию `rxPredict` с соответствующими аргументами к модели, а также укажите новые входные данные.
+  В примере `str` функция будет добавлена на этапе тестирования, чтобы проверить схему данных, возвращаемого из R. Вы можете удалить эту инструкцию позднее.
+ Имена столбцов, используемые в скрипте R, не передаются в выходные данные хранимой процедуры обязательно. Здесь мы использовали предложение WITH RESULTS для определения некоторых новых имен столбцов.

**Результаты**

![rsql_basictut_scoringresults_smalldata](media/rsql-basictut-scoringresults-smalldata.PNG)

## <a name="perform-scoring-in-parallel"></a>Выполнение оценки в параллельном режиме

Прогнозы для этого небольшого набора данных возвратились достаточно быстро. Предположим, что необходимо сделать много прогнозов очень быстро. Существует много способов ускорения операций в SQL Server, если операции могут обрабатываться параллельно. Для оценки в частности, одна простой способ — добавить *@parallel* параметра в sp_execute_external_script и задайте значение **1**.

Предположим, что вы получили более крупную таблицу с сотнями тысяч значений возможных скоростей автомобиля. В сообществе доступно множество примеров скриптов T-SQL, с помощью которых можно получить таблицы с числовыми значениями, поэтому мы не будем приводить их здесь. Давайте просто предположим, что у вас есть столбец с множеством целых чисел, которые требуется использовать в качестве входных данных для параметра `speed` в модели.

Чтобы сделать это, просто запустите же прогнозирующий запрос, но замените большего набора данных и добавьте `@parallel = 1` аргумент.

```sql
DECLARE @speedmodel varbinary(max) = (select model from [dbo].[stopping_distance_models] where model_name = 'default model');
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(speedmodel));
            new <- data.frame(NewCarData);
            predicted.distance <- rxPredict(current_model, new);
            OutputDataSet <- cbind(new, ceiling(predicted.distance));
            '
    , @input_data_1 = N' SELECT [speed] FROM [dbo].[HugeTableofCarSpeeds] '
    , @input_data_1_name = N'NewCarData'
    , @parallel = 1
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ Параллельное выполнение обычно выгодно только при работе с очень большими объемами данных. Ядро базы данных SQL может решить, что параллельное выполнение не требуется. Кроме того, у запроса SQL, получающего данные, должна быть возможность создания плана параллельных запросов.

+ При применении параллельного выполнения вы **должны** заранее указать схему выходных результатов, используя предложение WITH RESULT SETS. За счет этого SQL Server сможет объединить результаты нескольких параллельных наборов данных, схемы которых в противном случае были бы неизвестны.

+ Если вы являетесь *обучения* модели вместо *оценки*, этот параметр часто не будет действовать. В зависимости от типа модели для ее создания может потребоваться считывание всех строк перед созданием сводки.

+ Чтобы получить преимущества параллельной обработки, при обучении модели, мы рекомендуем использовать один из **RevoScaleR** алгоритмы. Эти алгоритмы предназначены для автоматического распределения обработки, даже если вы не укажете <code>@parallel =1</code> в вызове `sp_execute_external_script`. Рекомендации о том, как обеспечить максимальную производительность с RevoScaleR алгоритмами, см. в разделе [распределенные и параллельные вычисления с помощью ScaleR в Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).

## <a name="create-an-r-plot-of-the-model"></a>Создание диаграммы R модели

Множество клиентов, включая SQL Server Management Studio, не могут напрямую отображать диаграммы, созданные с помощью [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Вместо этого общий процесс для создания графиков R — создать диаграмму как часть кода R и запишите изображение в файл.

Кроме того можно вернуть сериализованный двоичный объект диаграммы в любое приложение, которое может отображать изображения.

В следующем примере показано, как создать простой график с помощью функции построения диаграммы, включенной в R по умолчанию. Хранимая процедура выводит изображение в указанный файл, а также в переменную SQL.

```sql
 EXECUTE sp_execute_external_script
 @language = N'R'
 , @script = N'
     imageDir <- ''C:\\temp\\plots'';
     image_filename = tempfile(pattern = "plot_", tmpdir = imageDir, fileext = ".jpg")
     print(image_filename);
     jpeg(filename=image_filename,  width=600, height = 800);
     print(plot(distance~speed, data=InputDataSet, xlab="Speed", ylab="Stopping distance", main = "1920 Car Safety"));
     abline(lm(distance~speed, data = InputDataSet));
     dev.off();
     OutputDataSet <- data.frame(data=readBin(file(image_filename, "rb"), what=raw(), n=1e6));
     '
  , @input_data_1 = N'SELECT speed, distance from [dbo].[CarSpeed]'
  WITH RESULT SETS ((plot varbinary(max)));
```

+ `tempfile` Функция возвращает строку, которая может использоваться в качестве имени файла, но еще не был создан файл.
+ Для аргументов `tempfile`, можно указать префикс и расширение файла, а также каталог. Чтобы проверить, полное имя файла и путь, печать сообщения с помощью `str()`.
+ Функция `jpeg` создает устройство R с указанными параметрами.
+ После создания графика, можно добавить дополнительные визуальные компоненты, к нему. В этом случае создается линия регрессии добавляется с помощью `abline`.
+ Завершив добавление компонентов диаграммы, закройте графическое устройство с помощью функции `dev.off()`.
+ Функция `readBin` принимает файл для чтения, спецификацию формата и число записей. `rb`** "Ключевое слово указывает, что файл является двоичным, а не текст.

**Результаты**

![rsql_basictut_plotresult_small](media/rsql-basictut-plotresult-small.png)

Если вы хотите создать более сложные диаграммы с помощью отличных пакетов графики для R, мы рекомендуем ознакомиться с этими статьями. В обоих случаях потребуется популярный пакет **ggplot2**.

+ [Классификация займов с помощью служб R SQL Server 2016](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/09/27/loan-classification-using-sql-server-2016-r-services/): универсальный сценарий на основе страховых данных. Требуется **изменить форму** пакета.
+ [Создание диаграмм и графиков с помощью языка R](walkthrough-create-graphs-and-plots-using-r.md)

## <a name="next-steps"></a>Следующие шаги

Интеграция R с SQL Server упрощает развертывание решений R в масштабе, а также позволяет использовать лучшие функции R и реляционные базы данных, повышающие производительность обработки данных и скорость анализа с использованием R. 

Продолжайте изучение решений с помощью языка R с SQL Server через end-to-end сценарии, созданные группами разработки обработки и анализа данных Майкрософт и R Services.

> [!div class="nextstepaction"]
> [Учебники по SQL Server R](sql-server-r-tutorials.md)
