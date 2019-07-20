---
title: Создание рабочих процессов SSIS и SSRS на языке R
description: Сценарии интеграции объединяют SQL Server Службы машинного обучения и службы R, Reporting Services (SSRS) и SQL Server Integration Services (SSIS).
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/17/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 09547f5f77eae8cff0924dfdf227c31563c10abd
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345592"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>Создание рабочих процессов служб SSIS и SSRS с помощью R на SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье объясняется, как использовать внедренный скрипт R и Python с использованием функций языка и обработки и анализа данных SQL Server Службы машинного обучения с двумя важными SQL Server функциями. SQL Server Integration Services (SSIS) и службы SSRS SQL Server Reporting Services. Библиотеки R и Python в SQL Server предоставляют статистические и прогнозирующие функции. Службы SSIS и SSRS предоставляют согласованное преобразование и визуализацию ETL соответственно. В этой статье описывается, как объединить все эти функции в этом шаблоне рабочего процесса:

> [!div class="checklist"]
> * Создание хранимой процедуры, содержащей исполняемый файл R или Python
> * Выполнение хранимой процедуры из служб SSIS или SSRS

Примеры в этой статье в основном относятся к R и SSIS, но концепции и действия применимы и к Python. Во втором разделе содержатся рекомендации и ссылки на визуализации SSRS.

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-automation"></a>Использование служб SSIS для автоматизации

Рабочие процессы для обработки и анализа данных имеют высокий уровень цикличности и содержат множество преобразований данных, в том числе масштабирование, агрегирование, вычисление вероятностей, переименование и слияние атрибутов. Исследователи данных могут выполнять такие задачи с использованием R, Python или других языков, но применение таких процессов к корпоративным данным требует беспроблемной интеграции со средствами и процессами извлечения, преобразования и загрузки данных.

Поскольку [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] позволяет выполнять сложные операции в R с помощью Transact-SQL и хранимых процедур, можно интегрировать задачи обработки и анализа данных с существующими процессами ETL. Вместо того, чтобы создавать цепочку ресурсоемких задач, можно оптимизировать подготовку данных с помощью наиболее эффективных средств, включая [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и. [!INCLUDE[tsql](../../includes/tsql-md.md)] 

Ниже приведены некоторые идеи, которые помогут автоматизировать процессы обработки и моделирования данных с помощью [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ Извлечение данных из локальных или облачных источников для создания обучающих данных 
+ Создание и запуск моделей R или Python в рамках рабочего процесса интеграции данных
+ Повторное обучение моделей на регулярной (запланированной) основе
+ Загрузите результаты из скрипта R или Python в другие назначения, такие как Excel, Power BI, Oracle и Teradata, чтобы наименовать несколько
+ Использование задач SSIS для создания функций данных в базе данных SQL
+ Использование условного ветвления для переключения контекста вычислений для заданий R и Python

## <a name="ssis-example"></a>Пример служб SSIS

Следующий пример основан на немедленно отмененной записи блога MSDN, созданной с помощью Джимми Вонг (по этому URL-адресу:`https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`

В этом примере показано, как автоматизировать задачи с помощью служб SSIS. Вы создаете хранимые процедуры с внедренным R с помощью SQL Server Management Studio, а затем выполняете эти хранимые процедуры из [задачи «Выполнение задач T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) » в пакете служб SSIS.

Для пошагового выполнения этого примера необходимо ознакомиться с Management Studio, службами SSIS, конструктором служб SSIS, конструкцией пакета и T-SQL. Пакет служб SSIS использует три [задачи «Выполнение T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) », которые вставляют обучающие данные в таблицу, моделируют данные и оценивают данные для получения выходных данных прогноза.

### <a name="load-training-data"></a>Загрузка данных для обучения

Выполните следующий скрипт в SQL Server Management Studio, чтобы создать таблицу для хранения данных. Для выполнения этого упражнения необходимо создать и использовать тестовую базу данных. 

```T-SQL
Use test-db
GO

Create table ssis_iris (
    id int not null identity primary key
    , "Sepal.Length" float not null, "Sepal.Width" float not null
    , "Petal.Length" float not null, "Petal.Width" float not null
    , "Species" varchar(100) null
);
GO
```

Создайте хранимую процедуру, которая загружает обучающие данные в кадр данных. В этом примере используется встроенный набор данных IRI. 

```T-SQL
Create procedure load_iris
as
begin
    execute sp_execute_external_script
        @language = N'R'
        , @script = N'iris_df <- iris;'
        , @input_data_1 = N''
        , @output_data_1_name = N'iris_df'
    with result sets (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100)));
end;
```

В конструкторе служб SSIS создайте [задачу «Выполнение SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) », которая выполняет только что определенную хранимую процедуру. Скрипт для **SQLStatement** удаляет существующие данные, указывает, какие данные следует вставить, а затем вызывает хранимую процедуру для предоставления данных.

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

![Вставка данных](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "Вставка данных")

### <a name="generate-a-model"></a>Создание модели

Выполните следующий скрипт в SQL Server Management Studio, чтобы создать таблицу, в которой хранится модель. 

```T-SQL
Use test-db
GO

Create table ssis_iris_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
GO
```

Создайте хранимую процедуру, которая создает линейную модель с помощью [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod). Библиотеки RevoScaleR и revoscalepy автоматически доступны в сеансах R и Python на SQL Server, поэтому импортировать библиотеку не требуется.

```T-SQL
Create procedure generate_iris_rx_model
as
begin
    execute sp_execute_external_script
        @language = N'R'
        , @script = N'
          irisLinMod <- rxLinMod(Sepal.Length ~ Sepal.Width + Petal.Length + Petal.Width + Species, data = ssis_iris);
          trained_model <- data.frame(payload = as.raw(serialize(irisLinMod, connection=NULL)));'
        , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from ssis_iris'
        , @input_data_1_name = N'ssis_iris'
        , @output_data_1_name = N'trained_model'
    with result sets ((model varbinary(max)));
end;
GO
```

В конструкторе служб SSIS создайте [задачу «Выполнение SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) » для выполнения хранимой процедуры **generate_iris_rx_model** . Модель сериализуется и сохраняется в таблицу ssis_iris_models. Скрипт для **SQLStatement** выглядит следующим образом:

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

![Формирует линейную модель](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "Формирует линейную модель")

После завершения этой задачи в качестве контрольной точки можно запросить ssis_iris_models, чтобы увидеть, что она содержит одну двоичную модель.

### <a name="predict-score-outcomes-using-the-trained-model"></a>Прогнозирование (оценка) результатов с помощью "обученной" модели

Теперь, когда у вас есть код, загружающий обучающие данные и создающий модель, единственным шагом является использование модели для создания прогнозов. 

Для этого добавьте сценарий R в SQL-запрос, чтобы активировать встроенную функцию R [rxPredict](https://docs.microsoft.com//machine-learning-server/r-reference/revoscaler/rxpredict) в ssis_iris_model. Эта задача достигается с помощью хранимой процедуры с именем **predict_species_length** .

```T-SQL
Create procedure predict_species_length (@model varchar(100))
as
begin
    declare @rx_model varbinary(max) = (select model from ssis_iris_models where model_name = @model);
    -- Predict based on the specified model:
    exec sp_execute_external_script
        @language = N'R'
        , @script = N'
irismodel <-unserialize(rx_model);
irispred <- rxPredict(irismodel, ssis_iris[,2:6]);
OutputDataSet <- cbind(ssis_iris[1], irispred$Sepal.Length_Pred, ssis_iris[2]);
colnames(OutputDataSet) <- c("id", "Sepal.Length.Actual", "Sepal.Length.Expected");
#OutputDataSet <- subset(OutputDataSet, Species.Length.Actual != Species.Expected);
'
    , @input_data_1 = N'
    select id, "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from ssis_iris
    '
    , @input_data_1_name = N'ssis_iris'
    , @params = N'@rx_model varbinary(max)'
    , @rx_model = @rx_model
    with result sets ( ("id" int, "Species.Length.Actual" float, "Species.Length.Expected" float)
        );
end;
```

В конструкторе служб SSIS создайте [задачу «Выполнение SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) », которая выполняет хранимую процедуру **predict_species_length** для создания прогнозируемой длины лепестка.

```T-SQL
exec predict_species_length 'rxLinMod';
```

![Сформировать прогнозы](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "Сформировать прогнозы")

### <a name="run-the-solution"></a>Запуск решения

В конструкторе служб SSIS нажмите клавишу F5, чтобы выполнить пакет. Вы увидите результат, аналогичный показанному на следующем снимке экрана.

![F5 для запуска в режиме отладки](../media/create-workflows-using-r-in-sql-server/ssis-exec-F5-run.png "F5 для запуска в режиме отладки")

<a name="bkmk_ssrs"></a> 

## <a name="use-ssrs-for-visualizations"></a>Использование SSRS для визуализаций

Хотя R может создавать диаграммы и интересные визуализации, она не интегрирована с внешними источниками данных, что означает, что каждая диаграмма или диаграмма должна быть создана отдельно. Совместное использование данных также может быть затруднено.

С помощью [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]можно выполнять сложные операции в R с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимых процедур, которые можно легко использовать в различных средствах корпоративного создания отчетов, включая [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и Power BI.

### <a name="ssrs-example"></a>Пример SSRS

[R Graphics Device for Microsoft Reporting Services (SSRS)](https://rgraphicsdevice.codeplex.com/) (Графическое устройство R для служб Microsoft Reporting Services (SSRS))

Этот проект CodePlex предоставляет код, помогающий создать пользовательский элемент отчета, который визуализирует графические выходные данные R в виде изображения, которое можно использовать в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] отчетах.  С помощью пользовательского элемента отчета можно:

+ опубликовать диаграммы и графики, созданные с помощью графического устройства R, на панелях мониторинга [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)];

+ передать параметры [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] графикам R.

> [!NOTE]
> В этом примере код, поддерживающий графическое устройство R для Reporting Services, должен быть установлен на сервере Reporting Services, а также в Visual Studio. Кроме того, требуется компиляция и настройка вручную.

## <a name="next-steps"></a>Следующие шаги

Примеры служб SSIS и SSRS в этой статье иллюстрируют два варианта выполнения хранимых процедур, содержащих внедренный скрипт R или Python. Ключевым мысль является то, что можно сделать скрипт R или Python доступным для любого приложения или средства, которое может отправить запрос на выполнение хранимой процедуры. Дополнительным мысльом для служб SSIS является возможность создания пакетов, автоматизирующих и планирующих широкий спектр операций, таких как получение данных, очистка, манипуляции и т. д., с помощью функций обработки и анализа данных R или Python, включенных в цепочку операций. Дополнительные сведения и идеи см. [в разделе эксплуатацию R Code using with хранимые процедуры в SQL Server службы машинного обучения](operationalizing-your-r-code.md).