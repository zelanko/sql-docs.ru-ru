---
title: "ПРОГНОЗ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PREDICT
- PREDICT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PREDICT clause
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 529cb229b6658085d0f2122604a4ed638f66a84c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="predict-transact-sql"></a>ПРОГНОЗ (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

Создает прогнозируемое значение или оценки на основе хранимых модели.  

## <a name="syntax"></a>Синтаксис

```
PREDICT  
(  
  MODEL = @model | model_literal,  
  DATA = object AS <table_alias>  
)  
WITH ( <result_set_definition> )  

<result_set_definition> ::=  
  {  
    { column_name  
      data_type  
      [ COLLATE collation_name ]  
      [ NULL | NOT NULL ]  
    }  
      [,...n ]  
  }  

MODEL = @model | model_literal  
```

### <a name="arguments"></a>Аргументы

**model**

`MODEL` Параметр используется для указания модели используется для оценки и прогнозирования. Модель определяется как переменную или литерал или скалярное выражение.

Объект модели могут создаваться с помощью R, Python или другого средства.

**данные**

Параметр данных используется для указания данных, используемых для оценки и прогнозирования. Данные указываются в виде источника таблицы в запросе. Источник таблицы может быть таблицу, псевдоним таблицы, псевдоним обобщенного табличного Выражения, представление или табличную функцию.

**Параметры**

Параметры параметр используется для указания необязательных параметров определяемых пользователем, для оценки или прогнозирования.

Имя каждого параметра определяется типом модели. Например, функция rxPredict в RevoScaleR поддерживает параметр  _@computeResiduals бит_ для поддержки вычисление остатков при оценке модели логистической регрессии. Можно передать имя параметра и его значение в `PREDICT` функции.

> [ПРИМЕЧАНИЕ] Этот параметр не поддерживается в предварительной версии SQL Server 2017 г. и включен только в целях совместимости вперед.

**С помощью ( \<result_set_definition >)**

Предложение WITH используется для указания схемы выходных данных, возвращаемый `PREDICT` функции.

Помимо столбцов, возвращаемых методом `PREDICT` саму функцию, все столбцы, которые являются частью данных ввода, доступные для использования в запросе.

### <a name="return-values"></a>Возвращаемые значения

Нет предварительно определенной схемой доступна; SQL Server не проверяет содержимое модели, а не проверяет значения возвращаемого столбца.  
- `PREDICT` Функция проходит через столбцы в качестве входных данных  
- `PREDICT` Функция также создает новые столбцы, но число столбцов и их типы данных зависит от типа модели, который был использован для прогнозирования.  

Сообщения об ошибках связаны с данными, модели, либо если формат столбца возвращаются по базовой прогнозирующей функции, связанные с моделью.  
- Для RevoScaleR, — эквивалентную функцию [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict)  
- Для MicrosoftML, — эквивалентную функцию [rxPredict.mlModel](https://docs.microsoft.com/r-server/r-reference/microsoftml/rxpredict)  

Не удается просмотреть структуру внутренней модели с помощью `PREDICT`. Если вы хотите понять содержимое самой модели, необходимо загрузить объект модели, десериализацию и используйте соответствующий код R для синтаксического анализа модели.

## <a name="remarks"></a>Замечания

`PREDICT` Функция поддерживается во всех выпусках SQL Server, включая Linux.

Нет необходимости наличия на сервере для использования R, Python или другого машинного обучения языка `PREDICT` функции. Можно провести обучение модели в другой среде и сохранить его в таблицу SQL Server для использования с `PREDICT`, или вызывать из другого экземпляра SQL Server, имеет сохраненную модель модель.

### <a name="supported-algorithms"></a>Поддерживаются алгоритмы

Модели, которая используется должен быть создан с помощью одного из поддерживаемых алгоритмов из пакета RevoScaleR. Список поддерживаемых в настоящее время моделей см. в разделе [в режиме реального времени оценки](../../advanced-analytics/real-time-scoring.md).

### <a name="permissions"></a>Permissions

Разрешения не требуются для `PREDICT`, однако потребности пользователей `EXECUTE` разрешения в базе данных, а также разрешения на любые данные, которые используются в качестве входных данных запроса. Пользователь также должны быть видимы для считывания из таблицы в модели, если модель хранилось в таблице.

## <a name="examples"></a>Примеры

В следующих примерах демонстрируется синтаксис для вызова метода `PREDICT`.

### <a name="call-a-stored-model-and-use-it-for-prediction"></a>Вызовите хранимую модель и использовать его для прогноза

В этом примере вызывается существующей модели логистической регрессии, хранящиеся в таблице [models_table]. Он возвращает последнюю обученной модели, используя инструкцию SELECT, а затем передает двоичной модели функция PREDICT. Входные значения представляют функции; выходные данные представляет назначенной моделью классификации.

```sql
DECLARE @logit_model varbinary(max) = "SELECT TOP 1 @model from [models_table]";
DECLARE @input_qry = "SELECT ID, [Gender], [Income] from NewCustomers";

SELECT PREDICT [class]
FROM PREDICT( MODEL = @logit_model,  DATA = @input_qry
WITH (class string);
```

### <a name="using-predict-in-a-from-clause"></a>С помощью ПРОГНОЗА в предложении FROM

Этот пример ссылается на `PREDICT` функционировать в `FROM` предложения `SELECT` инструкции:

```sql
SELECT d.*, p.Score
FROM PREDICT(MODEL = @logit_model, 
  DATA = dbo.mytable AS d) WITH (Score float) AS p;
```

Псевдоним **d** для исходной таблицы в _данные_ параметр используется для ссылки на столбцы, принадлежащие к dbo.mytable. Псевдоним **p** указано **PREDICT** функция используется для ссылки на столбцы, возвращенные функцией PREDICT.

### <a name="combining-predict-with-an-insert-statement"></a>Объединение ПРОГНОЗ с инструкцией INSERT

Одним из наиболее распространенных случаев использования прогноза является сформировать оценку для входных данных, а затем вставить прогнозируемые значения в таблицу. В следующем примере предполагается, что вызывающее приложение использует хранимую процедуру для вставки строки, содержащей прогнозируемое значение в таблицу:

```sql
CREATE PROCEDURE InsertLoanApplication
(@p1 varchar(100), @p2 varchar(200), @p3 money, @p4 int)
AS
BEGIN
  DECLARE @model varbinary(max) = (select model
  FROM scoring_model
  WHERE model_name = 'ScoringModelV1');
  WITH d as ( SELECT * FROM (values(@p1, @p2, @p3, @p4)) as t(c1, c2, c3, c4) )

  INSERT INTO loan_applications (c1, c2, c3, c4, score)
  SELECT d.c1, d.c2, d.c3, d.c4, p.score
  FROM PREDICT(MODEL = @model, DATA = d) WITH(score float) as p;
END;
```

Если процедура принимает несколько строк через табличное значение параметра, затем его можно записать следующим образом:

```sql
CREATE PROCEDURE InsertLoanApplications (@new_applications dbo.loan_application_type)
AS
BEGIN
  DECLARE @model varbinary(max) = (SELECT model_bin FROM scoring_models WHERE model_name = 'ScoringModelV1');
  INSERT INTO loan_applications (c1, c2, c3, c4, score)
  SELECT d.c1, d.c2, d.c3, d.c4, p.score
  FROM PREDICT(MODEL = @model, DATA = @new_applications as d)
  WITH (score float) as p;
END;
```

### <a name="creating-an-r-model-and-generating-scores-using-optional-model-parameters"></a>Создание модели R и вычислению оценок, с помощью модели необязательные параметры

> [!NOTE]
> Использование аргумента параметров не поддерживается в версии-кандидата 1.

В этом примере предполагается, что созданную модель логистической регрессии, оснащен матрицу ковариации, с помощью вызова RevoScaleR, такие как это:

```R
logitObj <- rxLogit(Kyphosis ~ Age + Start + Number, data = kyphosis, covCoef = TRUE)
```

При сохранении модели в SQL Server в двоичном формате можно использовать функцию ПРОГНОЗИРОВАНИЯ для создания не только прогнозов, но Дополнительные сведения, поддерживаемых типом модели, такие как ошибки или достоверности интервалов.

В следующем коде показано эквивалентное вызов из R rxPredict:

```R
rxPredict(logitObj, data = new_kyphosis_data, computeStdErr = TRUE, interval = "confidence")
```

Использование вызов эквивалентной `PREDICT` функция также обеспечивает показатель (прогнозируемое значение), ошибка и достоверности интервалы:

```sql
SELECT d.Age, d.Start, d.Number, p.pred AS Kyphosis_Pred, p.stdErr, p.pred_lower, p.pred_higher
FROM PREDICT( MODEL = @logitObj,  DATA = new_kyphosis_data AS d,
  PARAMETERS = N'computeStdErr bit, interval varchar(30)',
  computeStdErr = 1, interval = 'confidence')
WITH (pred float, stdErr float, pred_lower float, pred_higher float) AS p;
```



