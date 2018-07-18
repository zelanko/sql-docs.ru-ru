---
title: sp_rxPredict | Документация Майкрософт
ms.custom: ''
ms.date: 07/14/2017
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
author: jeannt
ms.author: jeannt
manager: craigg
ms.openlocfilehash: ede8232f36f42cc2b9758bdee8f50457ebd58dfe
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036052"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Создает на основе хранимой модели прогнозируемое значение.

Предоставляет оценки моделей машинного обучения в практически в реальном времени. `sp_rxPredict` Хранимая процедура, предоставленные как оболочка для `rxPredict` работать в [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) и [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package). Он создается на языке C + и оптимизирован специально для оценки операций. Оно поддерживает оба R или Python моделей машинного обучения.

**Этот раздел относится к**:  
- SQL Server 2017  
- SQL Server 2016 R Services обновление до Microsoft R Server  

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

Требуется один из следующих выпусков:  
- Служб SQL Server 2017 машинного обучения с (включает в себя Microsoft R Server 9.1.0)  
- Сервер машинного обучения Майкрософт  
- SQL Server R Services 2016, при обновлении экземпляра служб R Services для Microsoft R Server 9.1.0 или более поздней версии  

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

  Сведения о соответствующих типов SQL, см. в разделе [сопоставления типов SQL-CLR](https://msdn.microsoft.com/library/bb386947.aspx) или [сопоставление данных параметров CLR](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

