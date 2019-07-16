---
title: Библиотека функций MicrosoftML R - служб машинного обучения SQL Server
description: Общие сведения о библиотеке функции MicrosoftML в SQL Server 2016 R Services и служб SQL Server 2017 машинного обучения с помощью языка R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: e3dc94026f90ef769abb3889a716b5dadb317c4b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962504"
---
# <a name="microsoftml-r-library-in-sql-server"></a>MicrosoftML (библиотека R в SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**MicrosoftML** — это библиотека функция R от корпорации Майкрософт, предоставляя высокопроизводительные алгоритмы обучения. Он включает функции для обучения и преобразований, оценки, анализа текста и изображений и извлечения компонентов для наследования значения на основе существующих данных.

Машинного обучения интерфейсы API были разработаны корпорацией Майкрософт для внутреннего приложения для машинного обучения и были уточненные годы для поддержки высокой производительности на основе больших данных с помощью многоядерную обработку и быструю потоковую передачу данных. MicrosoftML также включает в себя множество преобразований для обработки изображений и текста.

## <a name="full-reference-documentation"></a>Полная справочная документация

**MicrosoftML** library распространяется в нескольких продуктов корпорации Microsoft, но использование совпадает ли вы получаете библиотеки в SQL Server или другой продукт. Так как функции являются одинаковыми, [документации для отдельных функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) публикуется только в одном месте в разделе [ссылку R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) для сервера машинного обучения Майкрософт. Следует любого конкретного продукта существует поведения, несоответствия будут указаны в странице справки по функции.

## <a name="versions-and-platforms"></a>Версии и платформы

**MicrosoftML** библиотеки на основе R 3.4.3 и доступны только в том случае, если устанавливается одно из следующих продуктов корпорации Майкрософт или файлы для загрузки:

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [SQL Server 2017 службы машинного обучения](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 или более поздней версии](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R client](set-up-a-data-science-client.md)

> [!NOTE]
> Версии выпуска полной версии продукта: только для Windows, для начиная с SQL Server 2017. Поддержка Linux **MicrosoftML** возможности [предварительной версии SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Зависимости пакета

Алгоритмы в **MicrosoftML** зависят от [RevoScaleR](ref-r-revoscaler.md) для:

+ Объекты источника данных. Данные, используемые **MicrosoftML** функции создаются с помощью **RevoScaleR** функции.
+ Удаленных вычислений (меняющихся выполнение функции с удаленным экземпляром SQL Server). **RevoScaleR** библиотека предоставляет функции для создания и активации удаленного вычисления контекст для SQL server.

В большинстве случаев вы загрузите пакеты вместе всякий раз, когда вы используете **MicrosoftML**.

## <a name="functions-by-category"></a>Функции по категориям

В этом разделе перечислены функции по категориям дать вам представление о том, как используется каждый из них. Можно также использовать [оглавление](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) следует выполнять поиск функций в алфавитном порядке.

<a name="ml-algorithms"></a>

## <a name="1-machine-learning-algorithms"></a>Алгоритмы 1 машинного обучения

| Имя функции | Описание |
|---------------|-------------|
|[rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees) | Реализация FastRank, эффективную реализацию алгоритма градиентного бустинга MART.  |
|[rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Случайные леса и Квантильной регрессии леса реализации с помощью [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees).  |
|[rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Алгоритм логистической регрессии с помощью L-BFGS.  |
|[rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm) | Один класс опорных векторов.  
|[rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) | Двоичный файл, многоклассовой и регрессии Нейронная сеть.  |
|[rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear) | Оптимизация стохастического парного координатного подъема для линейной двоичной классификации и регрессии. |
|[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble) | Обучает несколько моделей, чтобы получить лучше производительности, прогнозирования, не может быть получен из одной модели разные виды.|

<a name="ml-transforms"></a>

## <a name="2-transformation-functions"></a>Функции преобразования 2

| Имя функции | Описание |
|---------------|-------------|
|[Concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat) | Преобразование, чтобы создать единый столбец вектор возвращающих табличные значения из нескольких столбцов.  |
|[категориальные](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical) | Создайте вектор индикатора с помощью категориальные преобразования со словарем.  |
|[categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalhash) | Преобразует категориальные значения в массив индикатора путем хэширования. |
|[featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizetext) | Создает контейнер счетчиков последовательностей последовательных слов, называемых n грамм, из совокупности заданного текста. Он предлагает распознавание языка, разметки, удаление стоп-слов, нормализацию текста и создание признаков.  |
|[getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | Оценивает текст естественных языков и создает столбец, содержащий значения вероятности, что мнения в тексте являются положительными.|
|[ngram](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/ngram) | возможность определения аргументов для извлечения признаков на основе количества и на основе хэша.|
|[selectColumns](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectcolumns) | Выбирает набор столбцов для повторного обучения, удалив все остальные. |
|[selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectfeatures) | Выбирает функции из указанных переменных, использующее указанный режим.|
|[loadImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loadimage) | Загружает изображения данных.|
|[resizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/resizeimage) | Изменяет размер изображения и указанное измерение, с помощью заданного метода для изменения размера.|
|[extractPixels](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/extractpixels) | Извлекает значения пикселов из изображения.|
|[featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | Создает признаки изображений изображения с помощью предварительно обученной модели глубокой нейронной сети.|


## <a name="3-scoring-and-training-functions"></a>Функции обучения и оценки 3

| Имя функции | Описание |
|---------------|-------------|
|[rxPredict.mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxpredict) | Запускает оценки библиотеки из SQL Server, с помощью хранимой процедуры, или из кода R, включение оценки в реальном времени для предоставления гораздо быстрее производительность прогнозирования.|
|[rxFeaturize](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfeaturize) | Преобразует данные из входного набора данных для выходного набора данных.|
|[mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mlmodel) | Предоставляет сводку по модели Microsoft R машинного обучения.|


## <a name="4-loss-functions-for-classification-and-regression"></a>4-потери функции для классификации и регрессии

| Имя функции | Описание |
|---------------|-------------|
|[expLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации функции потерь экспоненциального классификации. | 
|[logLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации функции потерь классификации журнала.  |
|[hingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации функции потерь Ранжирующая классификации. | 
|[smoothHingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации функции потерь smooth Ранжирующая классификации.  |
| [poissonLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации функции потерь регрессии Пуассона. | 
|[squaredLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации функции потерь квадрате регрессии.   |   

## <a name="5-feature-selection-functions"></a>Функции выбора компонентов 5

| Имя функции | Описание |
|---------------|-------------|
|[minCount](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mincount) | Спецификация для выбора компонентов в режиме подсчета. |
|[mutualInformation](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mutualinformation) | Спецификация для выбора компонентов в режиме взаимной информации. |

## <a name="6-ensemble-modeling-functions"></a>Функции моделирования совокупности 6

| Имя функции | Описание |
|---------------|-------------|
|[fastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fasttrees) | Создает список, содержащий имя функции и аргументы для обучения модели Fast дерева с [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Создает список, содержащий имя функции и аргументы для обучения модели быстрый на базе леса с [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fastlinear) | Создает список, содержащий имя функции и аргументы для обучения модели быстрый Линейный с [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[logisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Создает список, содержащий имя функции и аргументы для обучения модели логистической регрессии с помощью [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[oneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/oneclasssvm) | Создает список, содержащий имя функции и аргументы для обучения модели OneClassSvm с [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|

## <a name="7-neural-networking-functions"></a>7-нейронной сети функции

| Имя функции | Описание |
|---------------|-------------|
|[оптимизатор](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/optimizer) | Указывает алгоритмы оптимизации для [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) алгоритм машинного обучения.|


## <a name="8-package-state-functions"></a>Функции управления состоянием 8-package

| Имя функции | Описание |
|---------------|-------------|
|[rxHashEnv](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxHashEnv) | Объект среды, используемого для хранения состояние на уровне пакета. |


## <a name="how-to-use-microsoftml"></a>Как использовать MicrosoftML

Функции в **MicrosoftML** можно вызывать в коде R инкапсулируются в хранимых процедурах. Большинство разработчиков создавать **MicrosoftML** решения локально, и затем перенести готовый код R в хранимые процедуры с действий развертывания.

**MicrosoftML** пакетом для R — это установленных «out-of--box» в SQL Server 2017. Оно доступно для использования с SQL Server 2016 при обновлении компонентов R для экземпляра: [Обновить экземпляр SQL Server с помощью привязки](../install/upgrade-r-and-python.md)

Пакет не загружается по умолчанию. В качестве первого шага, загрузить **MicrosoftML** пакета, а затем загрузите **RevoScaleR** необходимость использовать контексты удаленных вычислений или связанные объекты источника данных или подключения. Затем ссылаться на отдельные функции, которые вам нужны.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

## <a name="see-also"></a>См. также

+ [Учебники по R](../tutorials/sql-server-r-tutorials.md)
+ [Узнайте, как использовать контексты вычислений](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R для разработчиков SQL: Обучение и ввод модели в эксплуатацию](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Образцы продуктов Microsoft на GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [Справочник по R (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 