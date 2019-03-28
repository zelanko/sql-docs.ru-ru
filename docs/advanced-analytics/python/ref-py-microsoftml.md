---
title: пакет microsoftml Python - службы машинного обучения SQL Server
description: Знакомство с Microsoft алгоритмов машинного обучения и моделей для Python, применительно к рабочих нагрузок SQL Server machine learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 618c4b127c42aae6a5b8d7570f1962f8c8e38e9a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511721"
---
# <a name="microsoftml-python-module-in-sql-server"></a>microsoftml (модуль Python в SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**microsoftml** представляет собой Python35-совместимый модуль от корпорации Майкрософт, предоставляя высокопроизводительные алгоритмы обучения. Он включает функции для обучения и преобразований, оценки, анализа текста и изображений и извлечения компонентов для наследования значения на основе существующих данных.

Машинного обучения интерфейсы API были разработаны корпорацией Майкрософт для приложений внутренней машинного обучения, которые были уточненные годы для поддержки высокой производительности работы с большими данными с помощью многоядерную обработку и быструю потоковую передачу данных. Этот пакет, который изначально был эквивалента Python версии R, [MicrosoftML](../r/ref-r-microsoftml.md), который имеет аналогичные функции. 

## <a name="full-reference-documentation"></a>Полная справочная документация

**Microsoftml** library распространяется в нескольких продуктов корпорации Microsoft, но использование совпадает ли вы получаете библиотеки в SQL Server или другой продукт. Так как функции являются одинаковыми, [документации для отдельных microsoftml функций](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) публикуется только в одном месте в разделе [Справочник по Python](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) для сервера машинного обучения Майкрософт. Следует любого конкретного продукта существует поведения, несоответствия будут указаны в странице справки по функции.

## <a name="versions-and-platforms"></a>Версии и платформы

**Microsoftml** модуль исходя из Python 3.5 и доступны только в том случае, если устанавливается одно из следующих продуктов корпорации Майкрософт или файлы для загрузки:

+ [SQL Server 2017 службы машинного обучения](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 или более поздней версии](https://docs.microsoft.com/machine-learning-server/)
+ [Клиентские библиотеки Python для клиента обработки и анализа данных](setup-python-client-tools-sql.md)

> [!NOTE]
> Версии выпуска полной версии продукта: только для Windows, для начиная с SQL Server 2017. Поддержка Linux **microsoftml** возможности [предварительной версии SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Зависимости пакета

Алгоритмы в **microsoftml** зависят от [revoscalepy](ref-py-revoscalepy.md) для:

+ Объекты источника данных. Данные, используемые **microsoftml** функции создаются с помощью **revoscalepy** функции.
+ Удаленных вычислений (меняющихся выполнение функции с удаленным экземпляром SQL Server). **Revoscalepy** библиотека предоставляет функции для создания и активации удаленного вычисления контекст для SQL server.

В большинстве случаев вы загрузите пакеты вместе всякий раз, когда вы используете **microsoftml**.

## <a name="functions-by-category"></a>Функции по категориям

В этом разделе перечислены функции по категориям дать вам представление о том, как используется каждый из них. Можно также использовать [оглавление](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) следует выполнять поиск функций в алфавитном порядке.

## <a name="1-training-functions"></a>Функции 1-обучение

| Компонент | Описание |
|----------|-------------|
|[microsoftml.rx_ensemble](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-ensemble) | Обучение совокупности моделей. |
|[microsoftml.rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)  | Случайного леса. |
|[microsoftml.rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear) | Линейная модель. с помощью Стохастического парного координатного подъема. |
|[microsoftml.rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees) | Увеличивающиеся деревья принятия решений. |
|[microsoftml.rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression) | Алгоритм логистической регрессии. |
|[microsoftml.rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network) | Нейронной сети. |
|[microsoftml.rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm) | Обнаружение аномалий. |

<a name="ml-transforms"></a>

## <a name="2-transform-functions"></a>Функции преобразования 2

### <a name="categorical-variable-handling"></a>Обработка категориальных переменных

| Компонент | Описание |
|----------|-------------|
|[microsoftml.categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical) | Преобразует текстовый столбец на категории. |
|[microsoftml.categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash) | Хэширует и преобразует текстовый столбец на категории. |

### <a name="schema-manipulation"></a>Операций со схемой

| Компонент | Описание |
|----------|-------------|
|[microsoftml.concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat) | Объединяет несколько столбцов в один вектор. |
|[microsoftml.drop_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/drop-columns) | Удаляет столбцы из набора данных. |
|[microsoftml.select_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/select-columns) | Сохраняет столбцам набора данных. |


### <a name="variable-selection"></a>переменные, выбор

| Компонент | Описание |
|----------|-------------|
|[microsoftml.count_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/count-select) |Выбор компонентов, в зависимости от количества. |
|[microsoftml.mutualinformation_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/mutualinformation-select) | Выбор компонентов на основе взаимной информации. |


### <a name="text-analytics"></a>Текстовая аналитика

| Компонент | Описание |
|----------|-------------|
|[microsoftml.featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text) | Преобразует текстовые столбцы в числовые функции. |
|[microsoftml.get_sentiment](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/get-sentiment) | Анализ тональности. |


### <a name="image-analytics"></a>Анализ изображений 

| Компонент | Описание |
|----------|-------------|
|[microsoftml.load_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/load-image) | Загружает изображение. |
|[microsoftml.resize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/resize-image) | Изменяет размер изображения. |
|[microsoftml.extract_pixels](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/extract-pixels) | Извлекает пикселов из изображения. |
|[microsoftml.featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Преобразование типа image в функции. |

### <a name="featurization-functions"></a>Добавление признаков функции

| Компонент | Описание |
|----------|-------------|
|[microsoftml.rx_featurize](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-featurize) | Преобразование данных для источников данных |

<a name="ml-scoring"></a>

## <a name="3-scoring-functions"></a>Функции оценки 3

| Компонент | Описание |
|----------|-------------|
|[microsoftml.rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-predict) | Оценок с помощью модели машинного обучения Microsoft |

## <a name="how-to-call-microsoftml"></a>Как вызвать microsoftml

Функции в **microsoftml** можно вызывать в коде Python, инкапсулируются в хранимых процедурах. Большинство разработчиков создавать **microsoftml** решения локально, и затем перенести готовый код Python с хранимыми процедурами в качестве упражнения развертывания.

**Microsoftml** пакетом для Python устанавливается по умолчанию, но в отличие от **revoscalepy**, не загружаются по умолчанию, при запуске сеанса Python с помощью Python исполняемые файлы, установленные с помощью SQL Server.

В качестве первого шага, импортировать **microsoftml** пакета, а также импортировать **revoscalepy** необходимость использовать контексты удаленных вычислений или связанные объекты источника данных или подключения. Затем ссылаться на отдельные функции, которые вам нужны.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>См. также

+ [Учебники по Python](../tutorials/sql-server-python-tutorials.md)
+ [Учебник. Внедрение кода Python в T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Справочник по Python (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)

