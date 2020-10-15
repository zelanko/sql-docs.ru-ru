---
title: Пакет microsoftml для Python
description: microsoftml — это пакет Python от Майкрософт, предоставляющий высокопроизводительные алгоритмы машинного обучения. Он включает в себя функции для обучения и преобразований, оценки, анализа текста и изображений, а также извлечения компонентов для получения значений из существующих данных. Этот пакет входит в состав Служб машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/14/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a1f7c2c49acebe30b2739115b32643b2423f91cb
ms.sourcegitcommit: afb02c275b7c79fbd90fac4bfcfd92b00a399019
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2020
ms.locfileid: "91956931"
---
# <a name="microsoftml-python-package-in-sql-server-machine-learning-services"></a>microsoftml (пакет Python в Службах машинного обучения SQL Server)
[!INCLUDE [SQL Server 2017 and later](../../includes/applies-to-version/sqlserver2017.md)]

**microsoftml** — это пакет Python от Майкрософт, предоставляющий высокопроизводительные алгоритмы машинного обучения. Он включает в себя функции для обучения и преобразований, оценки, анализа текста и изображений, а также извлечения компонентов для получения значений из существующих данных. Пакет входит в состав [Служб машинного обучения SQL Server](../sql-server-machine-learning-services.md) и поддерживает высокую производительность при работе с большими данными, используя многоядерную обработку и быструю потоковую передачу данных.

## <a name="full-reference-documentation"></a>Полная справочная документация

Пакет **microsoftml** распространяется в нескольких продуктах Майкрософт, но его использование не зависит от того, получили ли вы его в SQL Server или в другом продукте. Благодаря сходству функций [документация по отдельным функциям microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) опубликована только в одном разделе в [справочнике по Python](/machine-learning-server/python-reference/introducing-python-package-reference) для Microsoft Machine Learning Server. Если для конкретных продуктов функции будут действовать иначе, выявленные расхождения будут приведены на странице справки по функциям.

## <a name="versions-and-platforms"></a>Версии и платформы

Модуль **microsoftml** основан на Python 3.5 и доступен только при установке одного из следующих продуктов или скачиваемых файлов Майкрософт:

+ [Службы машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 или более поздней версии](/machine-learning-server/)
+ [Клиентские библиотеки Python для клиента обработки и анализа данных](setup-python-client-tools-sql.md)

> [!NOTE]
> В SQL Server 2017 полные версии выпусков продуктов доступны только для Windows. В [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md) библиотека **microsoftml** поддерживает Windows и Linux.

## <a name="package-dependencies"></a>Зависимости пакетов

Алгоритмы в **microsoftml** используют [revoscalepy](ref-py-revoscalepy.md) для следующего:

+ Объекты источников данных. Данные, потребляемые функциями **microsoftml**, создаются с помощью функций **revoscalepy**.
+ Удаленное вычисление (перенос выполнения функций в удаленный экземпляр SQL Server). Пакет **revoscalepy** предоставляет функции для создания и активации контекста удаленных вычислений для SQL Server.

В большинстве случаев при использовании **microsoftml** пакеты будут загружаться вместе.

## <a name="functions-by-category"></a>Функции по категориям

Чтобы можно было понять, как использовать каждую функцию, в этом разделе приводится описание функций по категориям. Для поиска функций в алфавитном порядке можно воспользоваться [оглавлением](/machine-learning-server/python-reference/introducing-python-package-reference).

## <a name="1-training-functions"></a>1\. Функции обучения

| Функция | Описание |
|----------|-------------|
|[microsoftml.rx_ensemble](/machine-learning-server/python-reference/microsoftml/rx-ensemble) | Обучение ансамбля моделей. |
|[microsoftml.rx_fast_forest](/machine-learning-server/python-reference/microsoftml/rx-fast-forest)  | Случайный лес. |
|[microsoftml.rx_fast_linear](/machine-learning-server/python-reference/microsoftml/rx-fast-linear) | Линейная модель. Метод стохастической оптимизации с двойными координатами. |
|[microsoftml.rx_fast_trees](/machine-learning-server/python-reference/microsoftml/rx-fast-trees) | Повышенные деревья. |
|[microsoftml.rx_logistic_regression](/machine-learning-server/python-reference/microsoftml/rx-logistic-regression) | Логистическая регрессия. |
|[microsoftml.rx_neural_network](/machine-learning-server/python-reference/microsoftml/rx-neural-network) | Нейронная сеть. |
|[microsoftml.rx_oneclass_svm](/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm) | Обнаружение аномалий. |

<a name="ml-transforms"></a>

## <a name="2-transform-functions"></a>2\. Функции преобразования

### <a name="categorical-variable-handling"></a>Обработка категориальных переменных

| Функция | Описание |
|----------|-------------|
|[microsoftml.categorical](/machine-learning-server/python-reference/microsoftml/categorical) | Преобразует текстовый столбец в категории. |
|[microsoftml.categorical_hash](/machine-learning-server/python-reference/microsoftml/categorical-hash) | Хэширует и преобразует текстовый столбец в категории. |

### <a name="schema-manipulation"></a>Управление схемой

| Функция | Описание |
|----------|-------------|
|[microsoftml.concat](/machine-learning-server/python-reference/microsoftml/concat) | Сцепляет несколько столбцов в один вектор. |
|[microsoftml.drop_columns](/machine-learning-server/python-reference/microsoftml/drop-columns) | Удаляет столбцы из набора данных. |
|[microsoftml.select_columns](/machine-learning-server/python-reference/microsoftml/select-columns) | Сохраняет столбцы из набора данных. |


### <a name="variable-selection"></a>переменные, выбор

| Функция | Описание |
|----------|-------------|
|[microsoftml.count_select](/machine-learning-server/python-reference/microsoftml/count-select) |Выбор признаков на основе количества. |
|[microsoftml.mutualinformation_select](/machine-learning-server/python-reference/microsoftml/mutualinformation-select) | Выбор признаков на основе взаимной информации. |


### <a name="text-analytics"></a>Текстовая аналитика

| Функция | Описание |
|----------|-------------|
|[microsoftml.featurize_text](/machine-learning-server/python-reference/microsoftml/featurize-text) | Преобразует текстовые столбцы в числовые признаки. |
|[microsoftml.get_sentiment](/machine-learning-server/python-reference/microsoftml/get-sentiment) | Анализ тональности. |


### <a name="image-analytics"></a>Аналитика изображений 

| Функция | Описание |
|----------|-------------|
|[microsoftml.load_image](/machine-learning-server/python-reference/microsoftml/load-image) | Загружает изображение. |
|[microsoftml.resize_image](/machine-learning-server/python-reference/microsoftml/resize-image) | Изменяет размеры изображения. |
|[microsoftml.extract_pixels](/machine-learning-server/python-reference/microsoftml/extract-pixels) | Извлекает пиксели из изображения. |
|[microsoftml.featurize_image](/machine-learning-server/python-reference/microsoftml/featurize-image) | Преобразует изображение в признаки. |

### <a name="featurization-functions"></a>Функции добавления признаков

| Функция | Описание |
|----------|-------------|
|[microsoftml.rx_featurize](/machine-learning-server/python-reference/microsoftml/rx-featurize) | Преобразование данных для источников данных. |

<a name="ml-scoring"></a>

## <a name="3-scoring-functions"></a>3\. Функции оценки

| Компонент | Описание |
|----------|-------------|
|[microsoftml.rx_predict](/machine-learning-server/python-reference/microsoftml/rx-predict) | Производит оценку с помощью модели машинного обучения Майкрософт. |

## <a name="how-to-call-microsoftml"></a>Вызов microsoftml

Функции в **microsoftml** вызываются в коде Python, инкапсулированном в хранимые процедуры. Большинство разработчиков создают решения **microsoftml** локально, а затем переносят готовый код Python в хранимые процедуры, отрабатывая, таким образом, процедуру развертывания.

Пакет **microsoftml** для Python устанавливается по умолчанию, но, в отличие от **revoscalepy**, он не загружается по умолчанию при запуске сеанса Python с использованием исполняемых файлов Python, устанавливаемых с SQL Server.

В качестве первого шага импортируйте пакет **microsoftml**, а затем импортируйте **revoscalepy**, если необходимо использовать удаленные контексты вычисления либо связанные объекты подключения и источники данных. Затем можно сослаться на нужные вам функции.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>См. также раздел

+ [Учебники по Python](../tutorials/python-tutorials.md)
+ [Справочник по Python (Microsoft Machine Learning Server)](/machine-learning-server/python-reference/introducing-python-package-reference)