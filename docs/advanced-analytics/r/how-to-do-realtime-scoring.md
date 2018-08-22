---
title: Как выполнить оценки в реальном времени или собственной оценкой в машинного обучения SQL Server | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: dfea308f268d666ce070c21a7dd9afa513f95406
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2018
ms.locfileid: "40392224"
---
# <a name="how-to-perform-real-time-scoring-or-native-scoring-in-sql-server"></a>Как выполнить оценки в реальном времени или собственной оценкой в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье показано два подхода в SQL Server для прогнозирования результатов в практически в реальном времени, с помощью предварительно обученных моделей, на языке R. Как для оценки в реальном времени, так и для собственной оценки предназначены для использования модели машинного обучения без необходимости устанавливать R. Учитывая предварительно обученную модель в формате, совместимом - сохраняются в базе данных SQL Server — можно использовать методы доступа к данным, стандартные для быстрого создания прогнозирующие оценки для новых входных данных.

## <a name="choose-a-scoring-method"></a>Выбор метода количественной оценки

Для быстрого пакетное прогнозирование поддерживаются следующие параметры:

+ **Собственная Оценка**: функция PREDICT T-SQL в SQL Server 2017 Windows, Linux с SQL Server 2017 и базе данных SQL Azure.
+ **Оценки в реальном времени**: с помощью хранимой процедуры\_rxPredict хранимую процедуру в SQL Server 2016 или SQL Server 2017 (только Windows).

> [!NOTE]
> Рекомендуется использовать функцию PREDICT в SQL Server 2017.
> Использовать процедуру sp\_rxPredict необходимо включить интеграцию SQLCLR. Рассмотрите влияние на безопасность, прежде чем включать этот параметр.

Аналогично общего процесса по подготовке модели и затем вычисление оценок:

1. Создайте модель, используя поддерживаемый алгоритм.
2. Сериализует модель с помощью специальных двоичный формат.
3. Сделать модель доступной для SQL Server. Как правило, это означает сохранение сериализованную модель в таблице SQL Server.
4. Вызовите функции или хранимой процедуры и передайте модели и входных данных.

### <a name="requirements"></a>Требования

+ Функция PREDICT доступен во всех выпусках SQL Server 2017 и включена по умолчанию. Установка R или включить дополнительные компоненты не нужно.

+ При использовании sp\_rxPredict, требуются некоторые дополнительные действия. См. в разделе [включить оценки в реальном времени](#bkmk_enableRtScoring).

+ В настоящее время совместимых моделей можно создавать только RevoScaleR и MicrosoftML. Модель дополнительные типы становятся доступны в будущем. Список поддерживаемых алгоритмов, см. в разделе [оценки в реальном времени](../real-time-scoring.md).

### <a name="serialization-and-storage"></a>Сериализация и хранение

Чтобы использовать модель с любой из быстрой параметры оценки, сохраните модель с помощью специальных сериализованный формат, который был оптимизирован для размера и оценку эффективности.

+ Вызовите `rxSerializeModel` записываемый поддерживаемые модели для **необработанные** формат.
+ Вызовите `rxUnserializeModel` для воссоздания модели для использования в другой код R, или для просмотра модели.

Дополнительные сведения см. в разделе [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel).

**С помощью SQL**

Из кода SQL, вы можете обучить модель с помощью `sp_execute_external_script`и непосредственно вставлять обученных моделей в таблицу, в столбец типа **varbinary(max)**.

Простой пример, см. в разделе [этот учебник](../tutorials/rtsql-create-a-predictive-model-r.md)

**С помощью языка R**

Из кода R существует два способа сохранения модели в таблицу:

+ Вызовите `rxWriteObject` функции из пакета RevoScaleR, записываемое модели непосредственно к базе данных.

  `rxWriteObject()` Функции извлечения объектов R из источника данных ODBC, например SQL Server, или записи объектов в SQL Server. API моделируется простого хранилища значений ключей.
  
  Если вы используете эту функцию, убедитесь, что сериализации модели сначала с помощью новой функции сериализации. Затем задайте *сериализации* аргумента в `rxWriteObject` значение FALSE, чтобы избежать повторения шага сериализации.

+ Можно также сохранить модель в необработанном формате в файл и затем считываются из файла в SQL Server. Этот параметр может быть полезен, если выполняется перемещение или копирование моделей между средами.

## <a name="native-scoring-with-predict"></a>Собственная Оценка с PREDICT

В этом примере создания модели и затем вызвать в режиме реального времени прогнозирующую функцию из T-SQL.

### <a name="step-1-prepare-and-save-the-model"></a>Шаг 1. Подготовка и сохранение модели

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

Теперь создайте таблицу для хранения моделей.

```SQL
DROP TABLE IF EXISTS ml_models;
GO
CREATE TABLE ml_models ( model_name nvarchar(100) not null primary key
  , model_version nvarchar(100) not null
  , native_model_object varbinary(max) not null);
GO
```

Следующий код создает модель на основе **iris** набора данных и сохраняет его в таблицу с именем **моделей**.

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
> Обязательно используйте [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) функции RevoScaleR для сохранения модели. Стандартный R `serialize` функции не удается создать требуемый формат.

Можно выполнить инструкцию, такую как следующую команду, чтобы просмотреть сохраненную модель в двоичном формате:

```SQL
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Шаг 2. Выполнение ПРОГНОЗ для модели

Следующая инструкция простой ПРОГНОЗ Возвращает классификацию из модели дерева принятия решений с помощью **собственной оценки** функции. Она предсказывает виды цветов ириса на основе атрибутов, которые вы предоставляете, длина лепестка и ширина.

```SQL
DECLARE @model varbinary(max) = (
  SELECT native_model_object
  FROM ml_models
  WHERE model_name = 'iris.dtree'
  AND model_version = 'v1');
SELECT d.*, p.*
  FROM PREDICT(MODEL = @model, DATA = dbo.iris_rx_data as d)
  WITH(setosa_Pred float, versicolor_Pred float, virginica_Pred float) as p;
go
```

Если появится ошибка «произошла ошибка во время выполнения функции PREDICT. Модель повреждена», это обычно означает, что запрос не вернул модели. Проверьте ли правильно ввели имя модели, или если в таблице модели пуст.

> [!NOTE]
> Так как столбцы и значения, возвращенные **PREDICT** могут зависеть от типа модели, необходимо определить схему для возвращаемых данных с помощью **WITH** предложение.

## <a name="real-time-scoring-with-sprxpredict"></a>Оценка с sp_rxPredict в реальном времени

В этом разделе описываются шаги, необходимые для настройки **в режиме реального времени** прогноза, а также приводятся примеры того, как вызвать функцию из T-SQL.

### <a name ="bkmk_enableRtScoring"></a> Шаг 1. Включить процесс оценки в режиме реального времени

Необходимо включить эту функцию для каждой базы данных, который вы хотите использовать для оценки. Администратор сервера должен запустить служебную программу командной строки RegisterRExt.exe, входящий в состав пакета RevoScaleR.

> [!NOTE]
> В порядке для оценки в реальном времени для работы функции SQL CLR необходимо включить в экземпляре; Кроме того база данных должна быть помечена заслуживающая доверия. При выполнении сценарий, эти действия выполняются автоматически. Тем не менее рассмотрите влияние на дополнительную безопасность, прежде чем сделать это!

1. Откройте командную строку с повышенными правами и перейдите к папке, где находится RegisterRExt.exe. При установке по умолчанию можно использовать следующий путь:
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Выполните следующую команду, подставив имя своего экземпляра и целевой базы данных, где вы хотите включить расширенные хранимые процедуры:

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Например чтобы добавить расширенную хранимую процедуру CLRPredict базы данных на экземпляре по умолчанию, введите следующую команду:

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Имя экземпляра является необязательным, если база данных находится на экземпляре по умолчанию. Если вы используете именованный экземпляр, укажите имя экземпляра.

3. RegisterRExt.exe создает следующие объекты:

    + Доверенных сборок
    + Хранимая процедура `sp_rxPredict`
    + Роль базы данных, `rxpredict_users`. Администратор базы данных позволяют этой роли разрешение для пользователей, которые используют функции оценки в режиме реального времени.

4. Добавить всех пользователей, которым необходимо запустить `sp_rxPredict` в новую роль.

> [!NOTE]
> 
> В SQL Server 2017 дополнительные меры безопасности, чтобы избежать возникновения неполадок в интеграции со средой CLR. Эти меры налагаются дополнительные ограничения на использование этой хранимой процедуры. 

### <a name="step-2-prepare-and-save-the-model"></a>Шаг 2. Подготовка и сохранение модели

Двоичный формат, требуемый sp\_rxPredict совпадает со значением в формат, необходимый для использования функции PREDICT. Таким образом, в коде R включают вызов [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)и не забудьте указать `realtimeScoringOnly = TRUE`, как показано в этом примере:

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>Шаг 3. Вызов sp_rxPredict

Вы вызываете sp\_rxPredict, как вы и другие хранимой процедуры. В текущем выпуске, хранимая процедура принимает только два параметра:  _\@модели_ для модели в двоичном формате и  _\@inputData_ для данных, используемыми при оценке, определяется как допустимый SQL-запрос.

Так как двоичный формат имеет те же данные, используется функция PREDICT, можно использовать в таблице моделей и данных из предыдущего примера.

```SQL
DECLARE @irismodel varbinary(max)
SELECT @irismodel = [native_model_object] from [ml_models]
WHERE model_name = 'iris.dtree' 
AND model_version = 'v1''

EXEC sp_rxPredict
@model = @irismodel,
@inputData = N'SELECT * FROM iris_rx_data'
```

> [!NOTE]
> 
> Вызов sp\_rxPredict завершается неудачей, если входные данные для оценки не входят столбцы, которые соответствуют требованиям модели. В настоящее время поддерживаются только следующие типы данных .NET: double, float, short, ushort, long, ulong и строка.
> 
> Таким образом может потребоваться отфильтровать неподдерживаемые типы входных данных перед его использованием для оценки в реальном времени.
> 
> Сведения о соответствующих типов SQL, см. в разделе [сопоставления типов SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) или [сопоставление данных параметров CLR](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

## <a name="disable-real-time-scoring"></a>Отключить оценки в реальном времени

Чтобы отключить функцию в режиме реального времени оценки, откройте командную строку с повышенными привилегиями и выполните следующую команду: `RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="real-time-scoring-in-other-microsoft-product"></a>Оценка в другой продукт Майкрософт в реальном времени

При использовании автономного сервера или сервера машинного обучения Майкрософт, а не анализа в базе данных SQL Server, другими способами помимо хранимые процедуры и функции T-SQL для создания прогнозов.

Изолированный сервер и сервер машинного обучения поддерживают понятие *веб-службы* для развертывания кода. Можно объединить R или Python предварительно обученной модели веб-службы, вызываемых во время выполнения для оценки новых входных данных. Дополнительные сведения см. в следующих статьях:

+ [Что такое веб-служб в Machine Learning Server](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services)
+ [Что такое ввода в эксплуатацию](https://docs.microsoft.com/machine-learning-server/operationalize/concept-operationalize-deploy-consume)
+ [Развертывание модели Python в качестве веб-службы azureml модели management-sdk](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service)
+ [Публикация в блоке кода R или модель в режиме реального времени в виде новой веб-службы](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)
+ [пакет mrsdeploy для R](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)
