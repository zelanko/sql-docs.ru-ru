---
title: Создание рабочих процессов SSIS и SSRS на языке R
description: Сценарии интеграции, объединяющие Службы машинного обучения SQL Server и R Services, Reporting Services (SSRS) и SQL Server Integration Services (SSIS).
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/17/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2b8d55e95991437e4d76911fd26afb5b1bc9c550
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "68715170"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>Создание рабочих процессов SSIS и SSRS на языке R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье объясняется, как использовать внедренный скрипт R и Python с использованием возможностей языка и обработки и анализа данных Служб машинного обучения SQL Server с двумя важными компонентами SQL Server: SQL Server Integration Services (SSIS) и SQL Server Reporting Services (SSRS). Библиотеки R и Python в SQL Server предоставляют статистические и прогнозирующие функции. Службы SSIS и SSRS предоставляют согласованное преобразование в извлечении, преобразовании и загрузке и визуализацию соответственно. В этой статье описывается, как объединить все эти функции в этом шаблоне рабочего процесса:

> [!div class="checklist"]
> * Создание хранимой процедуры, содержащей исполняемый файл R или Python
> * Выполнение хранимой процедуры в SSIS или SSRS

Примеры в этой статье, в основном, относятся к R и SSIS, но концепции и действия применимы и к Python. Во втором разделе содержатся рекомендации и ссылки на визуализации SSRS.

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-automation"></a>Использование служб SSIS для автоматизации

Рабочие процессы для обработки и анализа данных имеют высокий уровень цикличности и содержат множество преобразований данных, в том числе масштабирование, агрегирование, вычисление вероятностей, переименование и слияние атрибутов. Исследователи данных могут выполнять такие задачи с использованием R, Python или других языков, но применение таких процессов к корпоративным данным требует беспроблемной интеграции со средствами и процессами извлечения, преобразования и загрузки данных.

Так как [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] позволяет выполнять сложные операции в R через Transact-SQL и хранимые процедуры, вы можете интегрировать задачи по обработке и анализу данных в уже имеющиеся процессы извлечения, преобразования и загрузки. Вместо выполнения цепочки задач, интенсивно использующих память, подготовку данных можно оптимизировать с помощью наиболее эффективных средств, включая [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и [!INCLUDE[tsql](../../includes/tsql-md.md)]. 

Ниже приведены некоторые идеи, которые помогут вам автоматизировать конвейеры обработки и моделирования данных с помощью [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ Извлечение данных из локальных или облачных источников для создания обучающих данных 
+ Создание и запуск моделей R или Python в рамках рабочего процесса интеграции данных
+ Повторное обучение моделей на регулярной (запланированной) основе
+ Загрузка результатов из скрипта R или Python в другие инструменты, такие как Excel, Power BI, Oracle, Teradata и т. д.
+ Использование задач SSIS для создания признаков данных в базе данных SQL
+ Использование условного ветвления, чтобы переключать контекст вычислений для задач с применением R и Python

## <a name="ssis-example"></a>Пример SSIS

Следующий пример взят из архивной записи блога MSDN, автор Джимми Вонг (Jimmy Wong), которая доступна по этому URL-адресу: `https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`

В этом примере показано, как автоматизировать задачи с помощью служб SSIS. Вы создаете хранимые процедуры с внедренным R с помощью SQL Server Management Studio, а затем выполняете эти хранимые процедуры из [задач выполнения T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task) в пакете служб SSIS.

Для пошагового выполнения этого примера необходимо иметь представление о Management Studio, службах SSIS, конструкторе служб SSIS, конструкции пакета и T-SQL. Пакет служб SSIS использует три [задачи выполнения T-SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task), которые вставляют обучающие данные в таблицу, моделируют данные и оценивают данные для получения выходных данных прогноза.

### <a name="load-training-data"></a>Загрузка обучающих данных

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

Создайте хранимую процедуру, которая загружает обучающие данные в кадр данных. В этом примере используется встроенный набор данных Iris. 

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

В конструкторе служб SSIS создайте [задачу выполнения SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task), которая выполняет только что определенную хранимую процедуру. Скрипт для **SQLStatement** удаляет существующие данные, указывает, какие данные следует вставить, а затем вызывает хранимую процедуру для предоставления данных.

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

![Вставка данных](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "Добавление данных")

### <a name="generate-a-model"></a>Формирование модели

Выполните следующий скрипт в SQL Server Management Studio, чтобы создать таблицу для хранения модели. 

```T-SQL
Use test-db
GO

Create table ssis_iris_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
GO
```

Создайте хранимую процедуру, которая формирует линейную модель с помощью [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod). Библиотеки RevoScaleR и revoscalepy автоматически доступны в сеансах R и Python на SQL Server, поэтому импортировать библиотеку не требуется.

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

В конструкторе служб SSIS создайте [задачу выполнения SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task) для выполнения хранимой процедуры **generate_iris_rx_model**. Модель сериализуется и сохраняется в таблице ssis_iris_models. Скрипт для **SQLStatement** выглядит следующим образом:

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

![Формирование линейной модели](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "Формирование линейной модели")

После завершения этой задачи в качестве контрольной точки можно отправить запрос в таблицу ssis_iris_models, чтобы увидеть, что она содержит одну двоичную модель.

### <a name="predict-score-outcomes-using-the-trained-model"></a>Прогнозирование (оценка) результатов с помощью "обученной" модели

Теперь, когда у вас есть код, загружающий обучающие данные и создающий модель, осталось только использовать модель для создания прогнозов. 

Для этого добавьте скрипт R в SQL-запрос, чтобы активировать встроенную функцию R [rxPredict](https://docs.microsoft.com//machine-learning-server/r-reference/revoscaler/rxpredict) ssis_iris_model. Эта задача выполняется с помощью хранимой процедуры **predict_species_length**.

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

В конструкторе служб SSIS создайте [задачу выполнения SQL](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task), которая выполняет хранимую процедуру **predict_species_length** для прогнозирования длины лепестка.

```T-SQL
exec predict_species_length 'rxLinMod';
```

![Создание прогнозов](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "Создание прогнозов")

### <a name="run-the-solution"></a>Запуск решения

В конструкторе служб SSIS нажмите клавишу F5, чтобы выполнить пакет. На следующем снимке экрана изображен примерный вывод команды.

![F5 для запуска в режиме отладки](../media/create-workflows-using-r-in-sql-server/ssis-exec-F5-run.png "F5 для запуска в режиме отладки")

<a name="bkmk_ssrs"></a> 

## <a name="use-ssrs-for-visualizations"></a>Использование SSRS для визуализаций

С помощью языка R можно создавать диаграммы и интересные визуализации, но он недостаточно хорошо интегрирован с внешними источниками данных. Это означает, что каждую диаграмму и график следует создавать отдельно. Совместное использование данных также может быть затруднено.

С помощью [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] вы можете выполнять сложные операции в R через хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)], которые легко можно использовать во множестве средств создания отчетов, включая [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и Power BI.

### <a name="ssrs-example"></a>Пример SSRS

[R Graphics Device for Microsoft Reporting Services (SSRS)](https://rgraphicsdevice.codeplex.com/) (Графическое устройство R для служб Microsoft Reporting Services (SSRS))

Проект CodePlex предоставляет код для создания пользовательского элемента отчета, выполняющего визуализацию графических выходных данных R в виде изображения, которое можно использовать в отчетах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  С помощью пользовательского элемента отчета можно:

+ опубликовать диаграммы и графики, созданные с помощью графического устройства R, на панелях мониторинга [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)];

+ передать параметры [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] графикам R.

> [!NOTE]
> В этом примере код, который поддерживает графическое устройство R для служб Reporting Services, должен быть установлен на сервере служб Reporting Services, а также в Visual Studio. Кроме того, требуется компиляция и настройка вручную.

## <a name="next-steps"></a>Дальнейшие действия

Примеры служб SSIS и SSRS в этой статье иллюстрируют два варианта выполнения хранимых процедур, содержащих внедренный скрипт R или Python. Ключевая идея в том, что можно сделать скрипт R или Python доступным для любого приложения или средства, которые могут отправить запрос на выполнение хранимой процедуры. Кроме того, со службами SSIS можно создавать пакеты, которые автоматизируют и планируют целый ряд операций, таких как получение данных, очистка, манипуляции и т. д., с помощью функций обработки и анализа данных R или Python, включенных в цепочку операций. Дополнительные сведения и идеи см. в разделе [Использование кода R с хранимыми процедурами в Службах машинного обучения SQL Server](operationalizing-your-r-code.md).