---
title: PREDICT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 02/25/2018
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|queries
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 0983ecd61dd50accda0039dbb02bf6daebf627f1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="predict-transact-sql"></a>PREDICT (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Создает предсказанное значение или оценки на основе хранимой модели.  

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

Параметр `MODEL` используется для указания модели, используемой для оценки и прогнозирования. Модель указывается как переменная или литерал или скалярное выражение.

Объект модели можно создавать с помощью R, Python или другого средства.

**data**

Параметр DATA используется для указания данных, используемых для оценки и прогнозирования. Данные указываются в виде источника таблицы в запросе. Источник таблицы может быть таблицей, псевдонимом таблицы, псевдонимом обобщенного табличного выражения, представлением или функцией с табличным значением.

**parameters**

Параметр PARAMETERS используется для указания необязательных определяемых пользователем параметров, используемых для оценки или прогнозирования.

Имя каждого параметра определяется типом модели. Например, функция [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) в RevoScaleR поддерживает параметр `@computeResiduals`, который указывает, необходимо ли вычислять остатки при оценке модели логистической регрессии. При вызове совместимой модели можно передать имя этого параметра и значение TRUE или FALSE функции `PREDICT`.

> [!NOTE]
> Этот параметр не работает в предварительных версиях SQL Server 2017.

**WITH ( <result_set_definition> )**

Предложение WITH используется для указания схемы выходных данных, возвращаемых функцией `PREDICT`.

Помимо столбцов, возвращаемых самой функцией `PREDICT`, в запросе можно использовать все столбцы, которые являются частью входных данных.

### <a name="return-values"></a>Возвращаемые значения

Предопределенные схемы недоступны. SQL Server не проверяет содержимое модели и не проверяет возвращаемые значения столбца.

- Функция `PREDICT` проходит через столбцы в качестве входных данных.
- Функция `PREDICT` также создает новые столбцы, но число столбцов и типы данных зависят от типа модели, использованной для прогнозирования.

Сообщения об ошибках, связанные с данными, моделью или форматом столбца, выводятся функцией прогнозирования, связанной с моделью.

- В RevoScaleR эквивалентом этой функции является [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict)  
- В MicrosoftML эквивалентом этой функции является [rxPredict.mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxpredict)  

Невозможно просмотреть внутреннюю структуру модели с помощью `PREDICT`. Если вы хотите понять содержимое самой модели, необходимо загрузить объект модели, десериализировать его и использовать подходящий код R для анализа модели.

## <a name="remarks"></a>Remarks

Функция `PREDICT` поддерживается во всех выпусках SQL Server, включая Linux, и в базе данных SQL Azure, независимо от того, доступны ли другие функции машинного обучения. Но требуется SQL Server 2017 или более поздней версии. 

Чтобы использовать функцию `PREDICT`, необязательно устанавливать на сервер R, Python или другой язык машинного обучения. Можно обучить модель в другой среде и сохранить ее в таблицу SQL Server для использования с `PREDICT` или вызвать модель из другого экземпляра SQL Server, где имеется сохраненная модель.

### <a name="supported-algorithms"></a>Поддерживаемые алгоритмы

Используемая модель должна быть создана с помощью одного из поддерживаемых алгоритмов из пакета RevoScaleR. Актуальный список поддерживаемых моделей см. в разделе [Оценка в режиме реального времени](../../advanced-analytics/real-time-scoring.md).

### <a name="permissions"></a>Разрешения

Для `PREDICT` разрешения не требуются, но пользователю нужно разрешение `EXECUTE` на базу данных и разрешение на запрос любых данных, используемых в качестве входных. У пользователя должна быть возможность чтения модели из таблицы, если модель хранится в таблице.

## <a name="examples"></a>Примеры

В следующих примерах демонстрируется синтаксис вызова `PREDICT`.

### <a name="call-a-stored-model-and-use-it-for-prediction"></a>Вызов хранимой модели и использование ее для прогнозирования

В этом примере вызывается существующая модель логистической регрессии, хранящаяся в таблице [models_table]. Последняя обученная модель вызывается инструкцией SELECT, а затем двоичная модель передается функции PREDICT. Входные значения представляют компоненты; выходные значения представляют классификацию, назначенную моделью.

```sql
DECLARE @logit_model varbinary(max) = "SELECT TOP 1 [model_binary] from [models_table] ORDER BY [trained_date] DESC";
DECLARE @input_qry = "SELECT ID, [Gender], [Income] from NewCustomers";

SELECT PREDICT [class]
FROM PREDICT( MODEL = @logit_model,  DATA = @input_qry
WITH (class string);
```

### <a name="using-predict-in-a-from-clause"></a>Использование PREDICT в предложении FROM

Этот пример ссылается на функцию `PREDICT` в предложении `FROM` инструкции `SELECT`:

```sql
SELECT d.*, p.Score
FROM PREDICT(MODEL = @logit_model, 
  DATA = dbo.mytable AS d) WITH (Score float) AS p;
```

Псевдоним **d**, указанный для источника таблицы в параметре `DATA`, используется для ссылки на столбцы, принадлежащие таблице dbo.mytable. Псевдоним **p**, указанный для функции **PREDICT**, используется для ссылки на столбцы, возвращенные функцией PREDICT.

### <a name="combining-predict-with-an-insert-statement"></a>Использование предложения PREDICT с инструкцией INSERT

Прогнозирование часто используется для оценки входных данных и последующей вставки прогнозируемых значений в таблицу. В следующем примере предполагается, что вызывающее приложение использует хранимую процедуру для вставки строки, содержащей предсказанное значение, в таблицу:

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

Если процедура принимает несколько строк через параметр табличных значений, ее можно записать следующим образом:

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

### <a name="creating-an-r-model-and-generating-scores-using-optional-model-parameters"></a>Создание модели R и вычисление оценок с помощью дополнительных параметров модели

> [!NOTE]
> Использование аргумента параметров не поддерживается в релизе-кандидате 1.

В этом примере предполагается, что вы создали модель логистической регрессии, оснащенную матрицей ковариации, с помощью вызова RevoScaleR, например:

```R
logitObj <- rxLogit(Kyphosis ~ Age + Start + Number, data = kyphosis, covCoef = TRUE)
```

При сохранении модели в SQL Server в двоичном формате можно использовать функцию PREDICT для создания не только прогнозов, но и дополнительных сведений, поддерживаемых типом модели, например ошибок и доверительных интервалов.

В следующем коде показан эквивалентный вызов из R в [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict):

```R
rxPredict(logitObj, data = new_kyphosis_data, computeStdErr = TRUE, interval = "confidence")
```

Эквивалентный вызов с помощью функции `PREDICT` также предоставляет оценку (предсказанное значение), ошибки и доверительные интервалы:

```sql
SELECT d.Age, d.Start, d.Number, p.pred AS Kyphosis_Pred, p.stdErr, p.pred_lower, p.pred_higher
FROM PREDICT( MODEL = @logitObj,  DATA = new_kyphosis_data AS d,
  PARAMETERS = N'computeStdErr bit, interval varchar(30)',
  computeStdErr = 1, interval = 'confidence')
WITH (pred float, stdErr float, pred_lower float, pred_higher float) AS p;
```
