---
title: "Как выполнять оценки в реальном времени или собственного оценки в SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 08/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2a72ac24f681d562adc7b43f02a4e91cdeb80bbc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="how-to-perform-realtime-scoring-or-native-scoring-in-sql-server"></a>Как выполнять оценки в реальном времени или собственного оценки в SQL Server

В этом разделе содержатся инструкции и образец кода для выполнения оценки в реальном времени и собственные оценки функции SQL Server 2016 и 2017 г. SQL Server. Оценки в реальном времени и оценки собственного предназначена для повышения производительности операций оценки небольшими группами.

Оценки в реальном времени и оценки собственного призваны позволяют использовать модель машинного обучения без необходимости устанавливать R. Все, что нужно сделать — получить предварительно обученные модели в совместимом формате и сохраните его в базе данных SQL Server.

## <a name="choosing-a-scoring-method"></a>Выбор метода количественной оценки

Для быстрого пакетный прогноз поддерживаются следующие параметры:

+ **Оценки собственного**: функция ПРОГНОЗИРОВАНИЯ T-SQL в SQL Server 2017 г.
+ **В реальном времени оценки**: использование sp_rxPredict хранимой процедуры в SQL Server 2016 или 2017 г. SQL Server.

> [!NOTE]
> В SQL Server 2017 г., рекомендуется использовать функции ПРОГНОЗИРОВАНИЯ.
> Для использования sp_rxPredict необходимо включить интеграцию SQLCLR. Рассмотрите влияние на безопасность, прежде чем включать этот параметр.

Процесс подготовки модели и затем формировать оценки очень похож:

1. Создайте модель с помощью поддерживаемый алгоритм.
2. Сериализует модель с использованием специальных двоичного формата.
3. Сделать модель доступной для SQL Server. Обычно это означает хранение сериализованную модель в таблицу SQL Server.
4. Вызов функции или хранимой процедуры и передать модели и входных данных.

### <a name="requirements"></a>Требования

+ Функция PREDICT доступен во всех выпусках SQL Server 2017 г. и включен по умолчанию. Необходимо установить R и включить дополнительные функции.

+ При использовании sp\_rxPredict, требуются некоторые дополнительные шаги. В разделе [включить оценки в реальном времени](#bkmk_enableRtScoring).

+ На момент написания этой статьи только RevoScaleR и MicrosoftML можно создать совместимых моделей. Дополнительные типы могут отображаться в будущем. Список поддерживаемых алгоритмов см. в разделе [оценки в реальном времени](../real-time-scoring.md).

### <a name="serialization-and-storage"></a>Сериализация и хранение

При использовании модели с любой из параметров быстрой оценки модели необходимо сохранить в специальном формате сериализованной, которая оптимизирована для размера и повышения эффективности.

+ Вызовите `rxSerializeModel` для записи поддерживаемые модели для **необработанные** формат.
+ Вызовите `rxUnserializeModel` для воссоздания модели для использования в другой код R, или для просмотра модели.

Дополнительные сведения см. в разделе [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel).

**С помощью SQL**

Из кода SQL, вы можете обучить модель с помощью `sp_execute_external_script`и непосредственно вставлять обученных моделей в таблицу, столбец типа **varbinary(max)**.

Простой пример см. в разделе [этого учебника](../tutorials/rtsql-create-a-predictive-model-r.md)

**С помощью R**

Из кода R можно сохранить в таблицу модели двумя способами:

+ Вызовите `rxWriteObject` функции из пакета RevoScaleR, чтобы записать модели в базу данных.

  `rxWriteObject()` Функции можно получить объекты R из источника данных ODBC, например SQL Server или записи объектов в SQL Server. API-Интерфейс моделируется простой хранилищу ключей и значений.
  
  При использовании этой функции, убедитесь, что для сериализации модели сначала с помощью новой функции сериализации. Затем задайте *сериализации* флаг в `rxWriteObject` значение FALSE во избежание повторения шага сериализации.

+ Можно также сохранить модель в необработанном формате в файл и считываются из файла в SQL Server. Этот параметр может быть полезен, если выполняется перемещение или копирование моделей между средами.

## <a name="native-scoring-with-predict"></a>Оценки с PREDICT машинный код

В этом примере предстоит создать модель и вызов функции прогнозирования в реальном времени из T-SQL.

### <a name="step-1-prepare-and-save-the-model"></a>Шаг 1. Подготовка и сохранить модель

Выполните следующий код для создания образца базы данных и обязательными таблицами.

```SQL
CREATE DATABASE NativeScoringTest;
GO
USE NativeScoringTest;
GO
DROP TABLE IF EXISTS iris_rx_data;
GO
CREATE TABLE iris_rx_data (
  "Sepal.Length" float not null, "Sepal.Width" float not null
  , "Petal.Length" float not null, "Petal.Width" float not null
  , "Species" varchar(100) null
);
GO
```

Используйте следующую инструкцию для заполнения таблицы данных с данными из **iris** набора данных.

```SQL
INSERT INTO iris_rx_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width" , "Species")
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

Теперь можно создайте таблицу для хранения моделей.

```SQL
DROP TABLE IF EXISTS ml_models;
GO
CREATE TABLE ml_models ( model_name nvarchar(100) not null primary key
  , model_version nvarchar(100) not null
  , native_model_object varbinary(max) not null);
GO
```

В следующем коде создается модель, основанную на **iris** набора данных и сохраняет его в таблицу модели.

```SQL
DECLARE @model varbinary(max);
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'
    iris.sub <- c(sample(1:50, 25), sample(51:100, 25), sample(101:150, 25))
    iris.dtree <- rxDTree(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = iris[iris.sub, ])
    model <- rxSerializeModel(iris.dtree, realtimeScoringOnly = TRUE)
    '
  , @params = N'@model varbinary(max) OUTPUT'
  , @model = @model OUTPUT
  INSERT [dbo].[ml_models]([model_name], [model_version], [native_model_object])
  VALUES('iris.dtree','v1', @model) ;
```

> [!NOTE] 
> Необходимо использовать [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel) функции RevoScaleR для сохранения модели. Стандартная R `serialize` функции не удается создать требуемый формат.

Можно выполнить инструкцию, такую как следующую команду для просмотра хранимых модели в двоичном формате:

```SQL
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Шаг 2. Выполнить ПРОГНОЗ для модели

Следующая простая инструкция PREDICT Возвращает классификацию из модели дерева принятия решений с помощью **оценки собственного** функции. Прогнозируется iris указывает, на основе атрибутов, лепесток длины и ширины.

```SQL
DECLARE @model varbinary(max) = (
  SELECT native_model_object
  FROM ml_models
  WHERE model_name = 'iris.dtree.model'
  AND model_version = 'v1');
SELECT d.*, p.*
  FROM PREDICT(MODEL = @model, DATA = dbo.iris_rx_data as d)
  WITH(setosa_Pred float, versicolor_Pred float, virginica_Pred float) as p;
go
```

Если появляется ошибка «произошла ошибка во время выполнения функции ПРОГНОЗА. Модель имеет поврежденный или недопустимый», это обычно означает, что запрос не вернул модели. Проверьте вы правильно ли указано имя модели, или если в таблице модели пуст.

> [!NOTE]
> Так как столбцы и значения, возвращенные **PREDICT** меняется в зависимости от типа модели, необходимо определить схему для возвращаемых данных с помощью **WITH** предложения.

## <a name="realtime-scoring-with-sprxpredict"></a>Оценки с sp_rxPredict в реальном времени

В этом разделе описываются шаги, необходимые для настройки **в реальном времени** прогноза и пример того, как можно вызвать функцию из T-SQL.

### <a name ="bkmk_enableRtScoring"></a>Шаг 1. Включить в реальном времени, оценки процедуры

Необходимо включить эту функцию для каждой базы данных, который требуется использовать для оценки. Администратор сервера должен программа командной строки, RegisterRExt.exe, входящий в состав пакета RevoScaleR.

> [!NOTE]
> Для оценки работы в режиме реального времени, функции SQL CLR необходимо включить в экземпляр и база данных должна быть отмечена как доверенная. При выполнении скрипта, эти действия выполняются автоматически. Тем не менее следует рассмотреть результаты дополнительную защиту для этого.

1. Откройте командную строку и перейдите к папке, где находится RegisterRExt.exe. При установке по умолчанию можно использовать следующий путь:
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Выполните следующую команду, подставив имя экземпляра и в целевую базу данных, которой вы хотите включить расширенные хранимые процедуры:

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Например чтобы добавить расширенные хранимые процедуры CLRPredict базы данных на экземпляре по умолчанию, введите следующую команду:

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Имя экземпляра является обязательным, если база данных находится на экземпляре по умолчанию. При использовании именованного экземпляра необходимо указать имя экземпляра.

3. RegisterRExt.exe создает следующие объекты:

    + Доверенных сборок
    + Хранимая процедура`sp_rxPredict`
    + Роль базы данных, `rxpredict_users`. Администратор базы данных можно использовать этой роли разрешение для пользователей, используйте функцию оценки в реальном времени.

4. Добавьте пользователей, которым требуется выполнять `sp_rxPredict` новой роли.

> [!NOTE]
> 
> В SQL Server 2017 г дополнительные меры безопасности находятся в месте, чтобы предотвратить возникновение проблем с интеграцией со средой CLR. Эти меры налагаются дополнительные ограничения на использование этой хранимой процедуры.


### <a name="step-2-prepare-and-save-the-model"></a>Шаг 2. Подготовка и сохранить модель

Двоичный формат, требуемый sp\_rxPredict является таким же, как для ПРОГНОЗА.

Поэтому в коде R включают в себя вызов [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel)и не забудьте указать _realtimeScoringOnly_ = TRUE, как показано в примере:

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>Шаг 3. Вызов sp_rxPredict

Вызовите sp_rxPredict, как и любой другой хранимой процедуры. В текущем выпуске, хранимая процедура принимает только два параметра:  _@model_  для модели в двоичном формате и  _@inputData_  для данных, используемыми при оценке, определенное как допустимый SQL-запрос .

Поскольку двоичный формат имеет те же данные, используется функция PREDICT, можно использовать в таблице модели и данные из предыдущего примера.

```SQL
DECLARE @irismodel varbinary(max)
SELECT @irismodel = [native_model_object] from [ml_models]
WHERE model_name = 'iris.dtree.model' AND model_version = 'v1''

EXEC sp_rxPredict
@model = @irismodel,
@inputData = N'SELECT * FROM iris_rx_data'
```

> [!NOTE]
> 
> Вызов `sp_rxPredict` завершается сбоем, если входные данные для оценки не включает столбцы, которые соответствуют требованиям модели. В настоящее время поддерживаются только следующие типы данных .NET: double, float, short, ushort, long, ulong и string.
> 
> Таким образом может потребоваться отфильтровать неподдерживаемых типов в качестве входных данных перед его использованием для оценки в реальном времени.
> 
> Сведения о соответствующих типов SQL см. в разделе [сопоставление типов SQL-CLR](https://msdn.microsoft.com/library/bb386947.aspx) или [сопоставления данных о параметрах CLR](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

### <a name="disable-realtime-scoring"></a>Отключить оценки в реальном времени

Чтобы отключить функции количественной оценки в реальном времени, откройте окно командной строки с повышенными привилегиями и выполните следующую команду:`RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

### <a name="realtime-scoring-in-microsoft-r-server"></a>В реальном времени, оценки в Microsoft R Server

Сведения, касающиеся в реальном времени оценки в распределенной среде, в зависимости от Microsoft R Server можно найти [publishService](https://msdn.microsoft.com/microsoft-r/mrsdeploy/packagehelp/publishservice) функции в [mrsDeploy пакета](https://msdn.microsoft.com/microsoft-r/mrsdeploy/mrsdeploy), который поддерживает Публикация модели для оценки в качестве новой веб-службы, запущенные на сервере R в реальном времени.

