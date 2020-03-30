---
title: Пакет microsoftml для Python
description: Общие сведения об алгоритмах и моделях машинного обучения Майкрософт для Python, связанных с рабочими нагрузками машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7ecbfd2edd20a312fc8a6d451938f1407585ded5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "73706957"
---
# <a name="microsoftml-python-module-in-sql-server"></a>microsoftml (модуль Python в SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**microsoftml** — это совместимый с Python35 модуль от корпорации Майкрософт, предоставляющий высокопроизводительные алгоритмы машинного обучения. Он включает в себя функции для обучения и преобразований, оценки, анализа текста и изображений, а также извлечения компонентов для получения значений из существующих данных.

Интерфейсы API машинного обучения разрабатывались корпорацией Майкрософт для внутренних приложений машинного обучения и улучшались в течение нескольких лет, чтобы обеспечить высокую производительность применительно к большим данным благодаря многоядерной обработке и быстрой потоковой передаче данных. Изначально пакет создавался как аналог версии для R ([MicrosoftML](../r/ref-r-microsoftml.md)), имеющей аналогичные функции. 

## <a name="full-reference-documentation"></a>Полная справочная документация

Библиотека **MicrosoftML** распространяется в нескольких продуктах Майкрософт и используется так же, как при получении в SQL Server или другом продукте. Благодаря сходству функций [документация по отдельным функциям microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) опубликована только в одном разделе в [справочнике по Python](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) для Microsoft Machine Learning Server. Если для конкретных продуктов функции будут действовать иначе, выявленные расхождения будут приведены на странице справки по функциям.

## <a name="versions-and-platforms"></a>Версии и платформы

Модуль **microsoftml** основан на Python 3.5 и доступен только при установке одного из следующих продуктов или скачиваемых файлов Майкрософт:

+ [Службы машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 или более поздней версии](https://docs.microsoft.com/machine-learning-server/)
+ [Клиентские библиотеки Python для клиента обработки и анализа данных](setup-python-client-tools-sql.md)

> [!NOTE]
> В SQL Server 2017 полные версии выпусков продуктов доступны только для Windows. В [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md) библиотека **microsoftml** поддерживает Windows и Linux.

## <a name="package-dependencies"></a>Зависимости пакетов

Алгоритмы в **microsoftml** используют [revoscalepy](ref-py-revoscalepy.md) для следующего:

+ Объекты источников данных. Данные, потребляемые функциями **microsoftml**, создаются с помощью функций **revoscalepy**.
+ Удаленное вычисление (перенос выполнения функций в удаленный экземпляр SQL Server). Библиотека **revoscalepy** предоставляет функции для создания и активации удаленного контекста вычисления для SQL Server.

В большинстве случаев при использовании **microsoftml** пакеты будут загружаться вместе.

## <a name="functions-by-category"></a>Функции по категориям

Чтобы можно было понять, как использовать каждую функцию, в этом разделе приводится описание функций по категориям. Для поиска функций в алфавитном порядке можно воспользоваться [оглавлением](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference).

## <a name="1-training-functions"></a>1\. Функции обучения

| Компонент | Описание |
|----------|-------------|
|[microsoftml.rx_ensemble](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-ensemble) | Обучение ансамбля моделей. |
|[microsoftml.rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)  | Случайный лес. |
|[microsoftml.rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear) | Линейная модель. Метод стохастической оптимизации с двойными координатами. |
|[microsoftml.rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees) | Повышенные деревья. |
|[microsoftml.rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression) | Логистическая регрессия. |
|[microsoftml.rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network) | Нейронная сеть. |
|[microsoftml.rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm) | Обнаружение аномалий. |

<a name="ml-transforms"></a>

## <a name="2-transform-functions"></a>2\. Функции преобразования

### <a name="categorical-variable-handling"></a>Обработка категориальных переменных

| Компонент | Описание |
|----------|-------------|
|[microsoftml.categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical) | Преобразует текстовый столбец в категории. |
|[microsoftml.categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash) | Хэширует и преобразует текстовый столбец в категории. |

### <a name="schema-manipulation"></a>Управление схемой

| Компонент | Описание |
|----------|-------------|
|[microsoftml.concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat) | Сцепляет несколько столбцов в один вектор. |
|[microsoftml.drop_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/drop-columns) | Удаляет столбцы из набора данных. |
|[microsoftml.select_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/select-columns) | Сохраняет столбцы из набора данных. |


### <a name="variable-selection"></a>переменные, выбор

| Компонент | Описание |
|----------|-------------|
|[microsoftml.count_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/count-select) |Выбор признаков на основе количества. |
|[microsoftml.mutualinformation_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/mutualinformation-select) | Выбор признаков на основе взаимной информации. |


### <a name="text-analytics"></a>Текстовая аналитика

| Компонент | Описание |
|----------|-------------|
|[microsoftml.featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text) | Преобразует текстовые столбцы в числовые признаки. |
|[microsoftml.get_sentiment](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/get-sentiment) | Анализ тональности. |


### <a name="image-analytics"></a>Аналитика изображений 

| Компонент | Описание |
|----------|-------------|
|[microsoftml.load_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/load-image) | Загружает изображение. |
|[microsoftml.resize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/resize-image) | Изменяет размеры изображения. |
|[microsoftml.extract_pixels](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/extract-pixels) | Извлекает пиксели из изображения. |
|[microsoftml.featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Преобразует изображение в признаки. |

### <a name="featurization-functions"></a>Функции добавления признаков

| Компонент | Описание |
|----------|-------------|
|[microsoftml.rx_featurize](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-featurize) | Преобразование данных для источников данных. |

<a name="ml-scoring"></a>

## <a name="3-scoring-functions"></a>3\. Функции оценки

| Компонент | Описание |
|----------|-------------|
|[microsoftml.rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-predict) | Производит оценку с помощью модели машинного обучения Майкрософт. |

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

+ [Учебники по Python](../tutorials/sql-server-python-tutorials.md)
+ [Руководство. Внедрение кода Python в T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Справочник по Python (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)

