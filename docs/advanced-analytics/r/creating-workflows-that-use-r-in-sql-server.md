---
title: Создание рабочих процессов служб SSIS и службы SSRS с помощью R - служб машинного обучения SQL Server
description: Сценарии интеграции, объединяя службы машинного обучения SQL Server и R Services, Reporting Services (SSRS) и SQL Server Integration Services (SSIS).
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/17/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 5d480b7cd24200b051fa2626fc41fa757703eaf8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62642639"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>Создание рабочих процессов служб SSIS и службы SSRS с r Server в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается использование внедренного скрипта R и Python, используя возможности обработки и анализа языка и данных службы машинного обучения SQL Server с две важные возможности SQL Server: SQL Server Integration Services (SSIS) и SQL Server Reporting Services SSRS. Библиотеки R и Python в SQL Server предоставляют функции, статистические и прогнозирования. Службы SSIS и службы SSRS предоставляют скоординированной преобразования ETL и визуализации, соответственно. В этой статье объясняется, как объединить все эти функции в этом шаблоне рабочего процесса:

> [!div class="checklist"]
> * Создать хранимую процедуру, которая содержит исполняемый файл R или Python
> * Выполните хранимую процедуру из служб SSIS или SSRS

В этой статье относятся, например направлен R и служб SSIS, но основные понятия и действия также применяются Python. Во втором разделе содержатся рекомендации и ссылки, для визуализации SSRS.

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-automation"></a>Для автоматизации с помощью служб SSIS

Рабочие процессы для обработки и анализа данных имеют высокий уровень цикличности и содержат множество преобразований данных, в том числе масштабирование, агрегирование, вычисление вероятностей, переименование и слияние атрибутов. Исследователи данных могут выполнять такие задачи с использованием R, Python или других языков, но применение таких процессов к корпоративным данным требует беспроблемной интеграции со средствами и процессами извлечения, преобразования и загрузки данных.

Так как [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] позволяет выполнять сложные операции в R через Transact-SQL и хранимых процедур, задач обработки и анализа данных можно интегрировать с существующими процессами ETL. Вместо выполнения цепочки задач с интенсивным использованием памяти, подготовки данных можно оптимизировать с помощью наиболее эффективных средств, включая [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и [!INCLUDE[tsql](../../includes/tsql-md.md)]. 

Далее приведено несколько идей для как можно автоматизировать обработку данных, а также моделирования конвейерах с помощью [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ Извлечение данных из локальной среды или облачных источников для создания обучающих данных 
+ Построение и выполнение моделей R или Python как часть рабочего процесса интеграции данных
+ Повторное Обучение моделей на регулярной основе (запланированное)
+ Загрузить результаты из скрипта R или Python в другие назначения, таких как Excel, Power BI, Oracle и Teradata и др
+ Задачи служб SSIS использовать для создания компонентов данных в базе данных SQL
+ Использование условного ветвления, чтобы переключать контекст вычислений для заданий R и Python

## <a name="ssis-example"></a>Пример служб SSIS

Следующий пример исходит из записи блога MSDN теперь выведенную автором Вонг Джимми этому URL-адресу: `https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`

В этом примере показано, как автоматизировать задачи с помощью служб SSIS. Создайте хранимые процедуры с помощью внедренных R, с помощью SQL Server Management Studio и затем исполнение этих хранимых процедур из [задачи Выполнение T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) в пакет служб SSIS.

Чтобы приступить к выполнению в этом примере, должны быть знакомы с Management Studio, служб SSIS, конструктор служб SSIS, проектирования пакета и T-SQL. Пакет служб SSIS используются три [задачи Выполнение T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) , вставка в таблицу данных для обучения, моделирования данных и оценки данных, чтобы получить выходные данные прогноза.

### <a name="load-training-data"></a>Загрузки обучающих данных

Выполните следующий скрипт в SQL Server Management Studio, чтобы создать таблицу для хранения данных. Необходимо создать и использовать тестовую базу данных для этого упражнения. 

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

Создайте хранимую процедуру, которая загружает обучающие данные во фрейм данных. В этом примере используется встроенный набор данных Iris. 

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

В конструкторе служб SSIS, создание [задача «Выполнение SQL»](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) , выполняет хранимую процедуру, вы только что определили. Скрипт для **SQLStatement** удаляет существующие данные, указывающий, какие данные для вставки, а затем вызывает хранимую процедуру для предоставления данных.

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

![Вставка данных](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "вставки данных")

### <a name="generate-a-model"></a>Формирование модели

Выполните следующий скрипт в SQL Server Management Studio, чтобы создать таблицу, в которой хранятся модели. 

```T-SQL
Use test-db
GO

Create table ssis_iris_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
GO
```

Создать хранимую процедуру, которая создает линейной модели с помощью [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod). Библиотеки RevoScaleR и revoscalepy автоматически доступны в сеансы R и Python на сервере SQL Server, поэтому нет необходимости импортировать в библиотеку.

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

В конструкторе служб SSIS, создание [задача «Выполнение SQL»](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) для выполнения **generate_iris_rx_model** хранимой процедуры. Модель сериализуется и сохранении ssis_iris_models таблицу. Скрипт для **SQLStatement** выглядит следующим образом:

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

![Создает модель линейной](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "создает модель линейной")

Как контрольную точку после завершения этой задачи вы можете запрашивать ssis_iris_models, чтобы увидеть, что он содержит один двоичная модель.

### <a name="predict-score-outcomes-using-the-trained-model"></a>Спрогнозировать результаты (оценкой), с помощью модели «обученной»

Теперь, когда у вас есть код, который загружает данные для обучения и создает модель, единственное действие слева использует модель для создания прогнозов. 

Чтобы сделать это, поместите этот сценарий R в SQL-запрос для активации [rxPredict](https://docs.microsoft.com//machine-learning-server/r-reference/revoscaler/rxpredict) встроенной функции R на ssis_iris_model. Хранимая процедура вызвана **predict_species_length** выполняет эту задачу.

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

В конструкторе служб SSIS, создание [задача «Выполнение SQL»](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) , выполняющего **predict_species_length** хранимую процедуру для создания прогнозируемых лепестка длины.

```T-SQL
exec predict_species_length 'rxLinMod';
```

![Формировать прогнозы](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "формирования прогнозов")

### <a name="run-the-solution"></a>Запуск решения

В конструкторе служб SSIS нажмите клавишу F5, чтобы выполнить пакет. Вы должны увидеть результат как на следующем снимке экрана.

![F5 для запуска в режиме отладки](../media/create-workflows-using-r-in-sql-server/ssis-exec-F5-run.png "F5 для запуска в режиме отладки")

<a name="bkmk_ssrs"></a> 

## <a name="use-ssrs-for-visualizations"></a>Используется для визуализации с помощью SSRS

Несмотря на то, что R можно создать диаграммы и интересные визуализации, это не хорошо интегрируются с внешними источниками данных, это означает, что каждую диаграмму и график приходится создавать отдельно. Совместное использование данных также может быть затруднено.

С помощью [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], вы можете выполнять сложные операции в R через [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимых процедур, которые легко можно использовать с помощью разнообразных средств создания отчетов, включая [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и Power BI.

### <a name="ssrs-example"></a>Пример SSRS

[R Graphics Device for Microsoft Reporting Services (SSRS)](https://rgraphicsdevice.codeplex.com/) (Графическое устройство R для служб Microsoft Reporting Services (SSRS))

Проект CodePlex предоставляет код для создания пользовательского элемента отчета, который выполняет визуализацию графических выходных данных R в виде изображения, которое можно использовать в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] отчеты.  С помощью пользовательского элемента отчета можно:

+ опубликовать диаграммы и графики, созданные с помощью графического устройства R, на панелях мониторинга [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)];

+ передать параметры [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] графикам R.

> [!NOTE]
> В этом примере код, который поддерживает графическое устройство R для служб Reporting Services должны быть установлены на сервере служб Reporting Services, а также в Visual Studio. Кроме того, требуется компиляция и настройка вручную.

## <a name="next-steps"></a>Следующие шаги

В примерах служб SSIS и службы SSRS в этой статье показано два случая выполнения хранимых процедур, содержащих внедренный скрипт R или Python. Ключевым моментом является то, что вы можете предоставить скрипт R или Python в любое приложение или средство, которое можно отправить запрос на выполнение хранимой процедуры. Дополнительные отсюда вывод: для служб SSIS — что можно создавать пакеты, автоматизировать и планировать широкий спектр операций, таких как получение данных, очистки, манипуляции и т. д. с помощью R или Python функции обработки и анализа данных, включенные в цепочки операций. Дополнительные сведения и идеи, см. в разделе [кода ввод в эксплуатацию R с помощью хранимых процедур в службах машинного обучения SQL Server](operationalizing-your-r-code.md).