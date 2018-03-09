---
title: "Прогнозировать и построения из модели (R в быстрый запуск SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 08/20/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
dev_langs:
- R
- SQL
ms.assetid: 46babd8a-a331-44fc-bbd6-24daf58865e1
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 835e7d4901fc3d58edfedaea4474e9b523b71620
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="predict-and-plot-from-model-r-in-sql-quickstart"></a>Прогнозировать и построения из модели (R в быстрый запуск SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Для выполнения _оценки_ с помощью новых данных, получении одного из обученных моделей из таблицы и затем вызвать новый набор данных, на которой будет производиться прогнозирование. Оценка — это термин, иногда используются в обработки и анализа данных означает создания прогнозов, вероятности и другие значения на основе новых данных, которые передавались в обученной модели.

## <a name="create-the-table-of-new-speeds"></a>Создание таблицы с новыми значениями скорости

Вы заметили, что значение скорости в исходных данных для обучения останавливается на 25 милях в час? Это потому, что эти исходные данные взяты из эксперимента, проведенного в 1920 году.

Вы можете задаться вопросом: сколько же времени потребуется автомобилю 1920-х, чтобы прекратить движение, при условии, что максимальное значение скорости — 60 или даже 100 миль/ч? Чтобы ответить на этот вопрос, необходимо предоставить некоторые новые значения скорости.

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

Чтобы получить прогнозы, основанные на одну конкретную модель, необходимо написать скрипт SQL, который выполняет следующие задачи:

1. Получение требуемой модели.
2. Получение новых входных данных.
3. Вызов функции прогнозирования R, совместимой с моделью.

В этом примере, так как модель основана на **rxLinMod** предоставляется как часть алгоритма **RevoScaleR** пакет, вызовите [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) функции, а не Универсальный R `predict` функции.

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
    , @input_data_1 = N' SELECT speed FROM [dbo].[NewCarSpeed] '
    , @input_data_1_name = N'NewCarData'
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ Используйте инструкцию SELECT для получения одной модели из таблицы и передайте ее в качестве входного параметра.
+  После получения модели из таблицы вызовите функцию `unserialize` для модели.

    > [!TIP] 
    > Также ознакомьтесь с новой [функции сериализации](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) , предоставляемые RevoScaleR, которая поддерживает [оценки в реальном времени](../../advanced-analytics/real-time-scoring.md).
+  Примените функцию `rxPredict` с соответствующими аргументами к модели, а также укажите новые входные данные.
+  В примере `str` функция будет добавлена на этапе тестирования, чтобы проверить схему данных, возвращаемых из кода R. Можно удалить эту инструкцию позднее.
+ Имена столбцов, используемых в R-скрипта не обязательно передаются в выходные данные хранимой процедуры. Здесь мы использовали РЕЗУЛЬТАТЫ с помощью предложения для определения некоторых новых имен столбцов.

**Результаты**

![rsql_basictut_scoringresults_smalldata](media/rsql-basictut-scoringresults-smalldata.PNG)

## <a name="perform-scoring-in-parallel"></a>Выполнение оценки в параллельном режиме

Прогнозы для этого небольшого набора данных возвратились достаточно быстро. Предположим, что необходимо сделать много прогнозов очень быстро. Существует множество способов для ускорения операции в SQL Server, если операции могут обрабатываться параллельно. Для оценки в частности проще всего добавить параметр *@parallel* в `sp_execute_external_script` и установить значение **1**.

Предположим, что вы получили более крупную таблицу с сотнями тысяч значений возможных скоростей автомобиля. В сообществе доступно множество примеров скриптов T-SQL, с помощью которых можно получить таблицы с числовыми значениями, поэтому мы не будем приводить их здесь. Давайте просто предположим, что у вас есть столбец с множеством целых чисел, которые требуется использовать в качестве входных данных для параметра `speed` в модели.

Чтобы сделать это, просто запустите прогнозирующий запрос, но заменить большего набора данных и добавьте `@parallel = 1` аргумент.

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

+ Параллельное выполнение, как правило, обеспечивает преимущества только при работе с очень больших объемов данных. Ядро базы данных SQL решить, что параллельное выполнение не нужен. Кроме того, у запроса SQL, получающего данные, должна быть возможность создания плана параллельных запросов.

+ При применении параллельного выполнения вы **должны** заранее указать схему выходных результатов, используя предложение WITH RESULT SETS. За счет этого SQL Server сможет объединить результаты нескольких параллельных наборов данных, схемы которых в противном случае были бы неизвестны.

+ Если вы являетесь *обучения* модель, а не *оценки*, этот параметр часто не будет оказывать влияние. В зависимости от типа модели для ее создания может потребоваться считывание всех строк перед созданием сводки.

+ Чтобы получить преимущества параллельную обработку во время обучения модели, рекомендуется использовать один из **RevoScaleR** алгоритмы. Эти алгоритмы предназначены для распределения обработки автоматически, даже если не указать <code>@parallel =1</code> в вызове `sp_execute_external_script`. Руководство для обеспечения высокой производительности с RevoScaleR алгоритмами см. в разделе [распределенных и параллельных вычислений с ScaleR в Microsoft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing).

## <a name="create-an-r-plot-of-the-model"></a>Создание диаграммы R модели

Множество клиентов, включая SQL Server Management Studio, не могут напрямую отображать диаграммы, созданные с помощью [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Вместо этого обычно процесс создания графиков R является создание графика как часть кода R и затем записать в файл изображения.

Кроме того можно вернуть объект сериализованные двоичные построения в любое приложение, которое может отображать изображения.

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
+ Для аргументов в `tempfile`, можно указать префикс и расширение файла, а также каталог. Чтобы проверить, полное имя файла и путь, печать сообщения с помощью `str()`.
+ Функция `jpeg` создает устройство R с указанными параметрами.
+ После создания графика, можно добавить дополнительные функции visual к нему. В этом случае линии регрессии добавляется с помощью `abline`.
+ Завершив добавление компонентов диаграммы, закройте графическое устройство с помощью функции `dev.off()`.
+ Функция `readBin` принимает файл для чтения, спецификацию формата и число записей. `rb`** "Ключевое слово указывает, что файл является двоичным, а не текст.

**Результаты**

![rsql_basictut_plotresult_small](media/rsql-basictut-plotresult-small.png)

Если вы хотите создать более сложные диаграммы с помощью отличных пакетов графики для R, мы рекомендуем ознакомиться с этими статьями. В обоих случаях потребуется популярный пакет **ggplot2**.

+ [Классификация займов с помощью служб R SQL Server 2016](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/09/27/loan-classification-using-sql-server-2016-r-services/): универсальный сценарий на основе страховых данных. Требуется **изменить форму** пакета.
+ [Создание диаграмм и графиков с помощью R](../../advanced-analytics/tutorials/walkthrough-create-graphs-and-plots-using-r.md)

## <a name="conclusions"></a>Заключение

Интеграция R с SQL Server упрощает развертывание решений R в масштабе, а также позволяет использовать лучшие функции R и реляционные базы данных, повышающие производительность обработки данных и скорость анализа с использованием R. 

См. в дополнительных разделах Дополнительные образцы R:

+  [Учебники по SQL Server R](../../advanced-analytics/tutorials/sql-server-r-tutorials.md)

    Продолжайте изучение решений с использованием R с SQL Server, созданные команды разработчиков обработки и анализа данных Майкрософт и служб R сценарии начала до конца.

+ [Учебники по SQL Server Python](../../advanced-analytics/tutorials/sql-server-python-tutorials.md)

    Для SQL Server 2017 г использование широких возможностей контекста удаленных вычислений и масштабируемых алгоритм с помощью языка Python.

+ [Учебники и образцы данных для Microsoft R](https://docs.microsoft.com/r-server/r/tutorial-introduction)

    Сведения об использовании новых пакетов RevoScaleR для создания моделей и преобразования данных.

+ [Приступая к работе с MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)

    Дополнительные сведения о быстрой, масштабируемые алгоритмов машинного обучения из Microsoft Research.
