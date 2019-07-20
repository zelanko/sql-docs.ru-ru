---
title: пакет Python для microsoftml
description: Содержит описание алгоритмов и моделей машинного обучения Майкрософт для Python, связанных с рабочими нагрузками SQL Server машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 298328db563cac8183b14b47e5c75c850c782d58
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345462"
---
# <a name="microsoftml-python-module-in-sql-server"></a>microsoftml (модуль Python в SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**microsoftml** — это совместимый с Python35 модуль от Майкрософт, предоставляющий высокопроизводительные алгоритмы машинного обучения. Она включает в себя функции для обучения и преобразований, оценки, анализа текста и изображений, а также извлечения компонентов для получения значений из существующих данных.

API-интерфейсы машинного обучения разрабатывались корпорацией Майкрософт для внутренних приложений машинного обучения и были улучшены в течение нескольких лет, чтобы обеспечить высокую производительность больших данных, используя многоядерную обработку и быструю потоковую передачу данных. Этот пакет создан как эквивалент Python версии R [MicrosoftML](../r/ref-r-microsoftml.md), который имеет аналогичные функции. 

## <a name="full-reference-documentation"></a>Полная справочная документация

Библиотека **microsoftml** распространяется в нескольких продуктах Майкрософт, но их использование одинаково при получении библиотеки в SQL Server или другом продукте. Поскольку функции одинаковы, [Документация по отдельным функциям microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) публикуется только в одном расположении в справочнике по [Python](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) для Microsoft Machine Learning Server. Если существуют какие-либо поведения конкретного продукта, расхождения будут указаны на странице справки по функциям.

## <a name="versions-and-platforms"></a>Версии и платформы

Модуль **microsoftml** основан на Python 3,5 и доступен только при установке одного из следующих продуктов или файлов загрузки Майкрософт:

+ [SQL Server 2017 Службы машинного обучения](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 или более поздней версии](https://docs.microsoft.com/machine-learning-server/)
+ [Клиентские библиотеки Python для клиента обработки и анализа данных](setup-python-client-tools-sql.md)

> [!NOTE]
> Полные версии продуктов выпускаются только для Windows, начиная с SQL Server 2017. Поддержка Linux для **microsoftml** впервые добавлена в [предварительной версии SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Зависимости пакетов

Алгоритмы в **microsoftml** зависят от [revoscalepy](ref-py-revoscalepy.md) для:

+ Объекты источника данных. Данные, потребляемые функциями **microsoftml** , создаются с помощью функций **revoscalepy** .
+ Удаленное вычисление (выполнение функций сдвига до удаленного экземпляра SQL Server). Библиотека **revoscalepy** предоставляет функции для создания и активации контекста удаленного вычислений для SQL Server.

В большинстве случаев пакеты будут загружаться вместе при использовании **microsoftml**.

## <a name="functions-by-category"></a>Функции по категориям

В этом разделе перечислены функции по категориям, которые позволяют понять, как используется каждая из них. Оглавление можно также использовать [для поиска](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) функций в алфавитном порядке.

## <a name="1-training-functions"></a>1\. обучающие функции

| Компонент | Описание |
|----------|-------------|
|[microsoftml. rx_ensemble](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-ensemble) | Обучение ансамблей моделей. |
|[microsoftml. rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)  | Случайный лес. |
|[microsoftml. rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear) | Линейная модель. с метод стохастического двумя координатами. |
|[microsoftml. rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees) | Повышенные деревья. |
|[microsoftml. rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression) | Логистическая регрессия. |
|[microsoftml.rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network) | Нейронная сеть. |
|[microsoftml. rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm) | Обнаружение аномалий. |

<a name="ml-transforms"></a>

## <a name="2-transform-functions"></a>2\. функции преобразования

### <a name="categorical-variable-handling"></a>Обработка переменных категорий

| Компонент | Описание |
|----------|-------------|
|[microsoftml. Категория](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical) | Преобразует текстовый столбец в категории. |
|[microsoftml. categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash) | Хэширует и преобразует текстовый столбец в категории. |

### <a name="schema-manipulation"></a>Управление схемой

| Компонент | Описание |
|----------|-------------|
|[microsoftml.concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat) | Объединяет несколько столбцов в один вектор. |
|[microsoftml.drop_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/drop-columns) | Удаляет столбцы из набора данных. |
|[microsoftml. select_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/select-columns) | Оставляет столбцы набора данных. |


### <a name="variable-selection"></a>переменные, выбор

| Компонент | Описание |
|----------|-------------|
|[microsoftml. count_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/count-select) |Выбор компонентов на основе счетчиков. |
|[microsoftml.mutualinformation_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/mutualinformation-select) | Выбор компонентов на основе взаимной информации. |


### <a name="text-analytics"></a>Текстовая аналитика

| Компонент | Описание |
|----------|-------------|
|[microsoftml. featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text) | Преобразует текстовые столбцы в числовые функции. |
|[microsoftml.get_sentiment](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/get-sentiment) | Анализ тональности. |


### <a name="image-analytics"></a>Аналитика изображений 

| Компонент | Описание |
|----------|-------------|
|[microsoftml. load_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/load-image) | Загружает изображение. |
|[microsoftml. resize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/resize-image) | Изменяет размер изображения. |
|[microsoftml. extract_pixels](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/extract-pixels) | Извлекает Пиксели из изображения. |
|[microsoftml. featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Преобразует изображение в компоненты. |

### <a name="featurization-functions"></a>Функции Добавление признаков

| Компонент | Описание |
|----------|-------------|
|[microsoftml. rx_featurize](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-featurize) | Преобразование данных для источников данных |

<a name="ml-scoring"></a>

## <a name="3-scoring-functions"></a>3\. функции оценки

| Компонент | Описание |
|----------|-------------|
|[microsoftml.rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-predict) | Оценки, использующие модель машинного обучения Майкрософт |

## <a name="how-to-call-microsoftml"></a>Как вызвать microsoftml

Функции в **microsoftml** вызываемы в коде Python, инкапсулированном в хранимых процедурах. Большинство разработчиков создают решения **microsoftml** локально, а затем выполняют перенос завершенного кода Python в хранимые процедуры в качестве упражнения развертывания.

Пакет **microsoftml** для Python устанавливается по умолчанию, но, в отличие от **revoscalepy**, он не загружается по умолчанию при запуске сеанса Python с помощью исполняемых файлов python, установленных с SQL Server.

В качестве первого шага импортируйте пакет **microsoftml** и импортируйте **revoscalepy** , если необходимо использовать удаленные контексты вычислений или связанные объекты подключения или источники данных. Затем сослаться на нужные вам функции.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>См. также

+ [Учебники по Python](../tutorials/sql-server-python-tutorials.md)
+ [Учебник. Внедрение кода Python в T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Справочник по Python (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)

