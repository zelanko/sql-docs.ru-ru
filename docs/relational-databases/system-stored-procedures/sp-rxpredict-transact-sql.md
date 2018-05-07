---
title: sp_rxPredict | Документы Microsoft
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
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Создает на основе хранимых модели прогнозируемое значение.

Предоставляет оценки на моделей машинного обучения в близком к реальному времени. `sp_rxPredict` Хранимая процедура, предоставленные как оболочка для `rxPredict` функционировать в [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) и [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package). Он записывается в C + и оптимизирован для оценки операций. Он поддерживает обе R или Python машинного обучения моделей.

**Этот раздел относится к**:  
- SQL Server 2017  
- Службы R SQL Server 2016 с обновления до Microsoft R Server  

## <a name="syntax"></a>Синтаксис

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>Аргументы

**model**

Предварительно обученные модели в поддерживаемом формате. 

**input**

Допустимый SQL-запрос

### <a name="return-values"></a>Возвращаемые значения

Возвращается столбец оценки, а также любые сквозные столбцы из источника входных данных.
Дополнительные столбцы, например доверительный интервал оценки, может быть возвращено, если алгоритм поддерживает создание таких значений.

## <a name="remarks"></a>Замечания

Чтобы включить использование хранимой процедуры, необходимо включить SQLCLR в экземпляре.

> [!NOTE]
> Рассмотрите влияние на безопасность, прежде чем включать этот параметр.

Потребности пользователей `EXECUTE` разрешения в базе данных.

### <a name="supported-platforms"></a>Поддерживаемые платформы

Требуется один из следующих выпусков:  
- Службы SQL Server 2017 г машины обучения с (включает Microsoft R Server 9.1.0)  
- Сервер Microsoft машинного обучения  
- SQL Server R Services 2016 при обновлении экземпляра служб R на сервере Microsoft R 9.1.0 или более поздней версии  

### <a name="supported-algorithms"></a>Поддерживаемые алгоритмы

Список поддерживаемых алгоритмов см. в разделе [в режиме реального времени оценки](../../advanced-analytics/real-time-scoring.md).

Приведенные ниже типы моделей являются **не** поддерживается:  
- Моделей, которые содержат другие неподдерживаемые типы преобразований R  
- Модели с помощью `rxGlm` или `rxNaiveBayes` алгоритмы в RevoScaleR  
- PMML модели  
- Модели, созданные с помощью других библиотек R из CRAN или другие репозитории  
- Моделей, которые содержат любого другого вида преобразования R, отличного от перечисленных здесь  

## <a name="examples"></a>Примеры

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

Помимо допустимый SQL-запрос, входные данные по *@inputData* должен включать столбцы, которые совместимы со столбцами в модели хранимой.

`sp_rxPredict` поддерживает только следующие типы столбцов .NET: double, float, short, ushort, long, ulong и string. Может потребоваться отфильтровать неподдерживаемых типов в качестве входных данных перед его использованием для оценки в режиме реального времени. 

  Сведения о соответствующих типов SQL см. в разделе [сопоставление типов SQL-CLR](https://msdn.microsoft.com/library/bb386947.aspx) или [сопоставления данных о параметрах CLR](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

