---
title: Создание рабочих процессов служб SSIS и службы SSRS с помощью R - служб машинного обучения SQL Server
description: Сценарии интеграции, объединяя службы машинного обучения SQL Server и R Services, Reporting Services (SSRS) и SQL Server Integration Services (SSIS).
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 76ddf3e3fdb43fea6bb8fd224f8199cda4134b64
ms.sourcegitcommit: e9fcd10c7eb87a4f09ac2d8f7647018e83a5f5c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57976304"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>Создание рабочих процессов служб SSIS и службы SSRS с r Server в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье объясняется, как использовать хранимые процедуры в две важные возможности SQL Server, SQL Server Integration Services (SSIS) и SQL Server Reporting Services SSRS, способом, который объединяет реляционные данные, функции обработки и анализа данных из библиотеки Microsoft R и компонентов бизнес-Аналитики для преобразования согласованных данных и визуализации. Узнайте, какие возможности [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляются для решения по обработке и анализу данных. В этой статье также напоминает, что код и данные на сервере SQL Server, например встроенный код R в хранимых процедурах, упростить их использование в визуализации, указанное в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].

## <a name="bring-compute-power-to-the-data"></a>Вдохните вычислительными ресурсами данных

Получите аналитику рядом с данными было целью проектирования ключа интеграции R и Python с SQL Server. Это дает несколько преимуществ:

+ Защита данных. Перевод R ближе к источнику данных позволяет избежать затратного или небезопасного перемещения.
+ Скорость. Базы данных оптимизированы для операций на основе наборов. Последние нововведения в базах данных, таких как таблицы в памяти сводок и существенно ускоряют агрегирование и являются идеальным дополнением для обработки и анализа данных.
+ Простота развертывания и интеграции. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является отправной точкой операций для многих других задач управления данных и приложений. Используя данные, хранящиеся в базе данных или хранилище отчетов, убедитесь, что данные, используемые решения машинного обучения, согласованность и обновление. 
+ Эффективность в облачной и локальной. Вместо обработки данных на языке R можно использовать конвейеры корпоративных данных, в том числе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и фабрику данных Azure. Отчеты о результатах или анализы можно с легкостью получать с помощью Power BI или [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].

Используя правильное сочетание SQL и R для разнообразных задач по обработке и анализу данных, исследователи данных и разработчики систем могут повысить эффективность работы.

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-data-transformation-and-automation"></a>Для преобразования данных и автоматизации с помощью служб SSIS

Рабочие процессы для обработки и анализа данных имеют высокий уровень цикличности и содержат множество преобразований данных, в том числе масштабирование, агрегирование, вычисление вероятностей, переименование и слияние атрибутов. Исследователи данных могут выполнять такие задачи с использованием R, Python или других языков, но применение таких процессов к корпоративным данным требует беспроблемной интеграции со средствами и процессами извлечения, преобразования и загрузки данных.

Так как [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] позволяет выполнять сложные операции в R через Transact-SQL и хранимые процедуры, вы можете интегрировать процессы, включающие R, в уже имеющиеся процессы извлечения, преобразования и загрузки. Для этого не потребуются существенные изменения в системе. Вместо выполнения цепочки задач, интенсивно использующих память в R, подготовку данных можно оптимизировать с помощью наиболее эффективных средств, включая [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и [!INCLUDE[tsql](../../includes/tsql-md.md)]. 

Далее приведено несколько идей для как можно автоматизировать обработку данных, а также моделирования конвейерах с помощью [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ Используйте [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] задач для создания функции необходимые данные в базе данных SQL
+ использование условного ветвления, чтобы переключать контекст вычислений для задач с применением R;
+ Выполнение заданий R, которые создают свои собственные данные в базе данных и совместное использование данных с приложениями
+ При использовании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], загрузить R-сценария, сохраненного в текстовой переменной, и запустите его в SQL Server

## <a name="ssis-example"></a>Пример служб SSIS

Следующий пример исходит из записи блога MSDN теперь выведенную автором Вонг Джимми этому URL-адресу: `https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`.

В этом примере показано, как автоматизировать задачи с помощью служб SSIS. Создайте хранимые процедуры с помощью внедренных R, с помощью SQL Server Management Studio и затем исполнение этих хранимых процедур из [задачи Выполнение T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) в пакет служб SSIS.

Чтобы приступить к выполнению в этом примере, должны быть знакомы с Management Studio, служб SSIS, конструктор служб SSIS, проектирования пакета и T-SQL. Пакет служб SSIS используются три [задачи Выполнение T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) , вставка в таблицу данных для обучения, моделирования данных и оценки данных, чтобы получить выходные данные прогноза.

### <a name="create-tables"></a>Создание таблиц

Выполните следующий скрипт в SQL Server Management Studio, чтобы создать несколько таблиц: один для хранения данных, а другой для хранения модели. В таблице ssis_iris заключается в качестве обучающих данных в сценарии ввода в эксплуатацию. 

```T-SQL
Use irissql
GO

Create table ssis_iris (
    id int not null identity primary key
    , "Sepal.Length" float not null, "Sepal.Width" float not null
    , "Petal.Length" float not null, "Petal.Width" float not null
    , "Species" varchar(100) null
);
GO

Create table ssis_iris_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
GO
```

### <a name="create-a-stored-procedure-that-loads-training-data"></a>Создать хранимую процедуру, которая загружает данные для обучения

Этот скрипт создает хранимую процедуру, которая загружает Iris в кадр данных, используя встроенный набор данных R.

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

### <a name="define-an-execute-sql-task-that-refreshes-the-model"></a>Определить задачу «Выполнение SQL», обновляет модель

В конструкторе служб SSIS, создание [задача «Выполнение SQL»](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task).

![Вставка данных](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "вставки данных")

Скрипт для SQLStatement выглядит следующим образом. Этот сценарий удаляет существующие данные и затем перезагружает новых данных с помощью **load_iris** хранимая процедура, созданная на предыдущем шаге.

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

### <a name="create-a-stored-procedure-that-generates-a-model"></a>Создать хранимую процедуру, которая создает модель

Эта хранимая процедура содержится код, который создается с помощью линейной модели [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod). Библиотеки RevoScaleR и revoscalepy, автоматически загружаются в сеансах R и Python на сервере SQL Server.

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

### <a name="define-an-execute-sql-task-that-runs-the-model-generation-stored-procedure"></a>Определение «Выполнение SQL», который выполняет хранимую процедуру создания моделей

На этом шаге [задача «Выполнение SQL»](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) выполняет **generate_iris_rx_model** хранимой процедуры, создание модели и их вставка в таблицу ssis_iris_models.

![Создает модель линейной](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "создает модель линейной")

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

После завершения этой задачи вы можете запрашивать ssis_iris_models, чтобы увидеть, что он содержит один двоичная модель.

### <a name="predict-score-outcomes-using-the-trained-model"></a>Спрогнозировать результаты (оценкой), с помощью модели «обученной»

В этот упрощенный пример предполагается, что этой ssis_iris_model обученной модели. Поскольку цель обученной модели для создания прогнозов, мы стали готовы выполнить прогноз с использованием его. 

Чтобы сделать это, поместите этот сценарий R в SQL-запрос для активации [rxPredict](https://docs.microsoft.com//machine-learning-server/r-reference/revoscaler/rxpredict) встроенной функции R на ssis_iris_model. Хранимые процедуры в SQL Server вызывать **predict_species_length** выполняет эту задачу.

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

### <a name="define-an-execute-sql-task-that-predicts-outcomes"></a>Определение «Выполнение SQL», которая прогнозирует результаты

С помощью [задача «Выполнение SQL»](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task), выполнение **predict_species_length** хранимую процедуру для создания прогнозируемых лепестка длины.

![Формировать прогнозы](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "формирования прогнозов")

```T-SQL
exec predict_species_length 'rxLinMod';
```

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