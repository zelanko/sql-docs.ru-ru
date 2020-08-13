---
title: Пакет MicrosoftML R
description: MicrosoftML — это пакет R от Майкрософт, предоставляющий высокопроизводительные алгоритмы машинного обучения. Он включает в себя функции для обучения и преобразований, оценки, анализа текста и изображений, а также извлечения компонентов для получения значений из существующих данных. Пакет входит в Службы машинного обучения SQL Server и службы SQL Server 2016 R и поддерживает высокую производительность при работе с большими данными, используя многоядерную обработку и быструю потоковую передачу данных. MicrosoftML также включает многочисленные преобразования для обработки текста и изображений.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/06/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 28f043ea0005f1020581218c358aed559285a5a4
ms.sourcegitcommit: d1535944bff3f2580070cc036ece30f1d43ee2ce
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2020
ms.locfileid: "86406177"
---
# <a name="microsoftml-r-package-in-sql-server-machine-learning-services"></a>MicrosoftML (пакет R в Службах машинного обучения SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

**MicrosoftML** — это пакет R от Майкрософт, предоставляющий высокопроизводительные алгоритмы машинного обучения. Он включает в себя функции для обучения и преобразований, оценки, анализа текста и изображений, а также извлечения компонентов для получения значений из существующих данных. Пакет входит в [Службы машинного обучения SQL Server](../sql-server-machine-learning-services.md) и [службы SQL Server 2016 R](sql-server-r-services.md) и поддерживает высокую производительность при работе с большими данными, используя многоядерную обработку и быструю потоковую передачу данных. MicrosoftML также включает многочисленные преобразования для обработки текста и изображений.

## <a name="full-reference-documentation"></a>Полная справочная документация

Пакет **MicrosoftML** распространяется в нескольких продуктах Майкрософт, но его использование не зависит от того, получили ли вы его в SQL Server или в другом продукте. Благодаря сходству функций [документация по отдельным функциям RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) опубликована только в одном разделе в [справочнике по R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) для Microsoft Machine Learning Server. Если для конкретных продуктов функции будут действовать иначе, выявленные расхождения будут приведены на странице справки по функциям.

## <a name="versions-and-platforms"></a>Версии и платформы

Пакет **MicrosoftML** основан на R 3.4.3 и доступен только при установке одного из следующих продуктов или скачиваемых файлов Майкрософт:

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [Службы машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 или более поздней версии](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R Client](set-up-a-data-science-client.md)

> [!NOTE]
> В SQL Server 2017 полные версии выпусков продуктов доступны только для Windows. В [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md) библиотека **MicrosoftML** поддерживает Windows и Linux.

## <a name="package-dependencies"></a>Зависимости пакетов

Алгоритмы в **MicrosoftML** используют [RevoScaleR](ref-r-revoscaler.md) для следующего.

+ Объекты источников данных. Данные, потребляемые функциями **MicrosoftML**, создаются с помощью функций **RevoScaleR**.
+ Удаленное вычисление (перенос выполнения функций в удаленный экземпляр SQL Server). Пакет **RevoScaleR** предоставляет функции для создания и активации контекста удаленных вычислений для SQL Server.

В большинстве случаев при использовании **MicrosoftML** пакеты будут загружаться вместе.

## <a name="functions-by-category"></a>Функции по категориям

Чтобы можно было понять, как использовать каждую функцию, в этом разделе приводится описание функций по категориям. Для поиска функций в алфавитном порядке можно воспользоваться [оглавлением](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference).

<a name="ml-algorithms"></a>

## <a name="1-machine-learning-algorithms"></a>1\. Алгоритмы машинного обучения

| Имя функции | Описание |
|---------------|-------------|
|[rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees) | Реализация FastRank, дающая эффективную реализацию алгоритма градиентного бустинга MART.  |
|[rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Реализация случайного леса и леса регрессии квантилей с помощью [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees).  |
|[rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Логистическая регрессия с использованием L-BFGS.  |
|[rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm) | Одноклассовый метод опорных векторов.  
|[rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) | Алгоритм бинарной нейронной сети с несколькими классами и регрессией.  |
|[rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear) | Метод стохастической оптимизации с двойными координатами для линейной двоичной классификации и регрессии. |
|[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble) | Проводите обучение нескольких моделей различных типов, чтобы получить лучшую прогнозную производительность, чем можно получить из одной модели.|

<a name="ml-transforms"></a>

## <a name="2-transformation-functions"></a>2\. Функции преобразования

| Имя функции | Описание |
|---------------|-------------|
|[concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat) | Преобразование для создания одного столбца с векторным значением из нескольких столбцов.  |
|[categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical) | Создание вектора индикатора с помощью преобразования категорий с использованием словаря.  |
|[categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalhash) | Преобразует значение категории в массив индикаторов с помощью хэширования. |
|[featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizetext) | Формирует набор счетчиков последовательных слов, называемых n-граммами, из заданной совокупности текста. Обеспечивает определение языка, разметку, удаление стоп-слов, нормализацию текста и создание компонентов.  |
|[getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | Оценивает текст на естественном языке и создает столбец, содержащий вероятности, что тональности в тексте положительны.|
|[ngram](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/ngram) | Позволяет определять аргументы для извлечения компонентов на основе подсчета и хэширования.|
|[selectColumns](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectcolumns) | Выбирает набор столбцов для повторного обучения, удаляя все остальные. |
|[selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectfeatures) | Выбирает компоненты из указанных переменных в указанном режиме.|
|[loadImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loadimage) | Загружает данные изображения.|
|[resizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/resizeimage) | Изменяет размер изображения до указанного с помощью заданного метода изменения размера.|
|[extractPixels](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/extractpixels) | Извлекает значения пикселей из изображения.|
|[featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | Делит изображение на компоненты, используя предварительно обученную модель глубокой нейронной сети.|


## <a name="3-scoring-and-training-functions"></a>3\. Функции оценки и обучения

| Имя функции | Описание |
|---------------|-------------|
|[rxPredict.mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxpredict) | Запускает библиотеку оценки либо из SQL Server с помощью хранимой процедуры либо из кода R, обеспечивая оценку в реальном времени, чтобы повысить скорость прогнозирования.|
|[rxFeaturize](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfeaturize) | Преобразует данные из набора входных данных в набор выходных данных.|
|[mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mlmodel) | Создает сводку по модели машинного обучения Microsoft R.|


## <a name="4-loss-functions-for-classification-and-regression"></a>4\. Функции потери для классификации и регрессии

| Имя функции | Описание |
|---------------|-------------|
|[expLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации функции экспоненциальной потери для классификации. | 
|[logLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации функции логарифмической потери для классификации.  |
|[hingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации функции зависимой потери для классификации. | 
|[smoothHingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации функции сглаженной зависимой потери для классификации.  |
| [poissonLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации функции потери для регрессии Пуассона. | 
|[squaredLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации функции потери для квадратичной регрессии.   |   

## <a name="5-feature-selection-functions"></a>5\. Функции выбора компонентов

| Имя функции | Описание |
|---------------|-------------|
|[minCount](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mincount) | Спецификация выбора компонентов в режиме подсчета. |
|[mutualInformation](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mutualinformation) | Спецификация выбора компонентов в режиме взаимной информации. |

## <a name="6-ensemble-modeling-functions"></a>6\. Ансамблейные функции моделирования

| Имя функции | Описание |
|---------------|-------------|
|[fastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fasttrees) | Создает список, содержащий имя функции и аргументы, для обучения модели быстрого дерева с [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Создает список, содержащий имя функции и аргументы, для обучения модели быстрого леса с [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fastlinear) | Создает список, содержащий имя функции и аргументы, для обучения быстрой линейной модели с [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[logisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Создает список, содержащий имя функции и аргументы, для обучения модели логистической регрессии с [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[oneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/oneclasssvm) | Создает список, содержащий имя функции и аргументы, для обучения модели OneClassSvm с [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|

## <a name="7-neural-networking-functions"></a>7\. Функции нейронных сетей

| Имя функции | Описание |
|---------------|-------------|
|[optimizer](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/optimizer) | Задает алгоритмы оптимизации для алгоритма машинного обучения [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)|


## <a name="8-package-state-functions"></a>8\. Функции состояния пакета

| Имя функции | Описание |
|---------------|-------------|
|[rxHashEnv](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxHashEnv) | Объект среды, используемый для хранения состояния всего пакета. |


## <a name="how-to-use-microsoftml"></a>Как использовать MicrosoftML

Функции в **MicrosoftML** вызываются в коде R, инкапсулированном в хранимые процедуры. Большинство разработчиков создают решения **MicrosoftML** локально, а затем переносят готовый код R в хранимые процедуры, отрабатывая, таким образом, процедуру развертывания.

Пакет **MicrosoftML** для R устанавливается как встроенный в SQL Server 2017. Его также можно использовать с SQL Server 2016, если обновить компоненты R для экземпляра. [Обновление экземпляра SQL Server с помощью привязки](../install/upgrade-r-and-python.md)

Пакет не загружается по умолчанию. В качестве первого шага загрузите пакет **MicrosoftML**, а затем загрузите **RevoScaleR**, если необходимо использовать удаленные контексты вычислений либо связанные объекты подключения и источники данных. Затем можно сослаться на нужные вам функции.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

## <a name="see-also"></a>См. также раздел

+ [Учебники по R](../tutorials/sql-server-r-tutorials.md)
+ [Использование контекстов вычисления](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R для разработчиков на SQL: обучение и эксплуатация модели](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Примеры продуктов Майкрософт на сайте GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [Справочник по R (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 