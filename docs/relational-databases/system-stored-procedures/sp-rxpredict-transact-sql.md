---
title: sp_rxPredict | Документация Майкрософт
ms.custom: ''
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_rxPredict procedure
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8f46403afef0e2f6cf967561a8fd24ec6409fe93
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "40434864"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Создает прогнозируемое значение для данного входа на основе машины обучения модели, сохраненной в двоичном формате в базе данных SQL Server.

Предоставляет оценку на R и Python моделей машинного обучения в практически в реальном времени. `sp_rxPredict` Хранимая процедура, предоставленные как оболочка для `rxPredict` функции R в [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) и [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)и [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) функции Python в [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) и [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package). Он создается на языке C + и оптимизирован специально для оценки операций.

**Эта статья относится к**:  
- SQL Server 2017  
- SQL Server 2016 R Services с [обновить компоненты R](https://docs.microsoft.com/sql/advanced-analytics/r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server)

## <a name="syntax"></a>Синтаксис

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>Аргументы

**model**

Предварительно обученной модели в поддерживаемом формате. 

**input**

Допустимый SQL-запрос

### <a name="return-values"></a>Возвращаемые значения

Возвращается столбец оценки, а также любой сквозные столбцы из источника входных данных.
Дополнительные столбцы, например доверительный интервал оценки, могут быть возвращены, если алгоритм поддерживает создание таких значений.

## <a name="remarks"></a>Примечания

Чтобы включить использование хранимой процедуры, необходимо включить SQLCLR в экземпляре.

> [!NOTE]
> Рассмотрите влияние на безопасность, прежде чем включать этот параметр.

Нужные пользователю `EXECUTE` разрешение в базе данных.

### <a name="supported-platforms"></a>Поддерживаемые платформы
 
- Служб SQL Server 2017 машинного обучения с (включает в себя R Server 9.2)  
- Сервер SQL Server 2017 машинного обучения (автономный) 
- SQL Server R Services 2016, при обновлении экземпляра служб R для R Server 9.1.0 или более поздней версии  

### <a name="supported-algorithms"></a>Поддерживаемые алгоритмы

Список поддерживаемых алгоритмов, см. в разделе [оценки в реальном времени](../../advanced-analytics/real-time-scoring.md).

Следующие типы модели **не** поддерживается:  
- Модели, содержащий другие неподдерживаемые типы преобразований R  
- Моделирует использование `rxGlm` или `rxNaiveBayes` алгоритмы в RevoScaleR  
- PMML модели  
- Модели, созданные с помощью других библиотек R из CRAN или других репозиториев  
- Модели, содержащая любые другие виды преобразования R, отличного от перечисленных здесь  

## <a name="examples"></a>Примеры

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

Кроме того, что допустимый SQL-запрос, входные данные в *@inputData* должна включать столбцы, которые совместимы со столбцами в сохраненную модель.

`sp_rxPredict` поддерживает только следующие типы .NET столбца: double, float, short, ushort, long, ulong и строка. Может потребоваться отфильтровать неподдерживаемые типы входных данных перед его использованием для оценки в реальном времени. 

  Сведения о соответствующих типов SQL, см. в разделе [сопоставления типов SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) или [сопоставление данных параметров CLR](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

