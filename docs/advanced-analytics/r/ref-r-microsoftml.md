---
title: Библиотека функций R MicrosoftML
description: Введение в библиотеку функций MicrosoftML в службах SQL Server 2016 R и SQL Server 2017 Службы машинного обучения с R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 6808fa01bd4b62a67b220cec86d025820958298d
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470013"
---
# <a name="microsoftml-r-library-in-sql-server"></a>MicrosoftML (библиотека R в SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**MicrosoftML** — это библиотека функций R от Майкрософт, предоставляющая высокопроизводительные алгоритмы машинного обучения. Она включает в себя функции для обучения и преобразований, оценки, анализа текста и изображений, а также извлечения компонентов для получения значений из существующих данных.

API-интерфейсы машинного обучения разрабатывались корпорацией Майкрософт для внутренних приложений машинного обучения и были улучшены в течение нескольких лет, чтобы обеспечить высокую производительность больших данных, используя многоядерную обработку и быструю потоковую передачу данных. MicrosoftML также включает многочисленные преобразования для обработки текста и изображений.

## <a name="full-reference-documentation"></a>Полная справочная документация

Библиотека **MicrosoftML** распространяется в нескольких продуктах Майкрософт, но их использование одинаково при получении библиотеки в SQL Server или другом продукте. Поскольку функции одинаковы, [Документация по отдельным функциям RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) публикуется только в одном расположении в справочнике по [R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) для Microsoft Machine Learning Server. Если существуют какие-либо поведения конкретного продукта, расхождения будут указаны на странице справки по функциям.

## <a name="versions-and-platforms"></a>Версии и платформы

Библиотека **MicrosoftML** основана на R 3.4.3 и доступна только при установке одного из следующих продуктов или загрузок Майкрософт:

+ [Службы SQL Server 2016 R](../install/sql-r-services-windows-install.md)
+ [SQL Server 2017 Службы машинного обучения](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 или более поздней версии](https://docs.microsoft.com/machine-learning-server/)
+ [Клиент Microsoft R](set-up-a-data-science-client.md)

> [!NOTE]
> Полные версии продуктов выпускаются только для Windows, начиная с SQL Server 2017. Поддержка Linux для **MicrosoftML** впервые добавлена в [предварительной версии SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Зависимости пакетов

Алгоритмы в **MicrosoftML** зависят от [RevoScaleR](ref-r-revoscaler.md) для:

+ Объекты источника данных. Данные, потребляемые функциями **MicrosoftML** , создаются с помощью функций **RevoScaleR** .
+ Удаленное вычисление (выполнение функций сдвига до удаленного экземпляра SQL Server). Библиотека **RevoScaleR** предоставляет функции для создания и активации контекста удаленного вычислений для SQL Server.

В большинстве случаев пакеты будут загружаться вместе при использовании **MicrosoftML**.

## <a name="functions-by-category"></a>Функции по категориям

В этом разделе перечислены функции по категориям, которые позволяют понять, как используется каждая из них. Оглавление можно также использовать [для поиска](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) функций в алфавитном порядке.

<a name="ml-algorithms"></a>

## <a name="1-machine-learning-algorithms"></a>алгоритмы машинного обучения 1

| Имя функции | Описание |
|---------------|-------------|
|[рксфасттрис](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees) | Реализация Фастранк, эффективная реализация алгоритма усиления градиента КИОСКа.  |
|[рксфастфорест](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Реализация случайного леса и квантилей регрессии с помощью [рксфасттрис](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees).  |
|[ркслогистикрегрессион](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Логистическая регрессия с использованием L-БФГС.  |
|[rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm) | Один класс поддерживает векторные компьютеры.  
|[ркснеуралнет](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) | Алгоритм нейронной сети с несколькими классами и регрессией.  |
|[рксфастлинеар](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear) | Метод стохастического оптимизацию с двойным координатом для линейной двоичной классификации и регрессии. |
|[рксенсембле](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble) | Проводите обучение нескольких моделей различных типов, чтобы получить лучшую прогнозную производительность, чем можно получить из одной модели.|

<a name="ml-transforms"></a>

## <a name="2-transformation-functions"></a>2 функции преобразования

| Имя функции | Описание |
|---------------|-------------|
|[сцеплен](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat) | Преобразование для создания одного столбца с векторным значением из нескольких столбцов.  |
|[категориальные](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical) | Создание вектора индикатора с помощью преобразования категорий с использованием словаря.  |
|[категорикалхаш](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalhash) | Преобразует значение категории в массив индикаторов с помощью хэширования. |
|[феатуризетекст](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizetext) | Формирует набор счетчиков последовательностей подряд слов, называемых n-граммами, из заданного совокупности текста. Он обеспечивает определение языка, разметку, стоп-слова удаление, нормализацию текста и создание компонентов.  |
|[жетсентимент](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | Оценивает текст на естественном языке и создает столбец, содержащий вероятности, что тональности в тексте является положительным.|
|[ngram](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/ngram) | позволяет определять аргументы для извлечения компонентов на основе подсчета и хэша.|
|[selectColumns](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectcolumns) | Выбирает набор столбцов для повторного обучения, удаляя все остальные. |
|[селектфеатурес](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectfeatures) | Выбирает компоненты из указанных переменных в указанном режиме.|
|[лоадимаже](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loadimage) | Загружает данные изображения.|
|[ресизеимаже](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/resizeimage) | Изменяет размер изображения до указанного измерения с помощью указанного метода изменения размера.|
|[екстрактпикселс](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/extractpixels) | Извлекает значения пикселя из изображения.|
|[феатуризеимаже](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | Феатуризес изображение, используя предварительно обученную модель глубокой нейронной сети.|


## <a name="3-scoring-and-training-functions"></a>3 — функции оценки и обучения

| Имя функции | Описание |
|---------------|-------------|
|[rxPredict. Млмодел](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxpredict) | Запускает библиотеку оценки либо из SQL Server, с помощью хранимой процедуры, либо из кода R, включив оценку в реальном времени, чтобы обеспечить более быструю производительность прогнозирования.|
|[рксфеатуризе](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfeaturize) | Преобразует данные из набора входных данных в выходной набор данных.|
|[млмодел](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mlmodel) | Содержит сводку по модели Microsoft R Машинное обучение.|


## <a name="4-loss-functions-for-classification-and-regression"></a>4 — функции потери для классификации и регрессии

| Имя функции | Описание |
|---------------|-------------|
|[експлосс](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации функции потери экспоненциальной классификации. | 
|[логлосс](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации для функции потери классификации журнала.  |
|[хинжелосс](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации для функции потери классификации шарнира. | 
|[смусхинжелосс](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации для функции потери классификации с гладким шарниром.  |
| [поиссонлосс](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации для функции потери регрессии Пуассона. | 
|[скуаредлосс](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Спецификации для функции квадратной регрессии.   |   

## <a name="5-feature-selection-functions"></a>5\. функции выбора компонентов

| Имя функции | Описание |
|---------------|-------------|
|[минкаунт](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mincount) | Спецификация выбора компонентов в режиме подсчета. |
|[мутуалинформатион](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mutualinformation) | Спецификация выбора компонентов в режиме взаимной информации. |

## <a name="6-ensemble-modeling-functions"></a>6-ансамблейные функции моделирования

| Имя функции | Описание |
|---------------|-------------|
|[фасттрис](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fasttrees) | Создает список, содержащий имя функции и аргументы для обучения быстрой модели дерева с помощью [рксенсембле](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[фастфорест](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Создает список, содержащий имя функции и аргументы для обучения модели быстрого леса с [рксенсембле](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[фастлинеар](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fastlinear) | Создает список, содержащий имя функции и аргументы для обучения быстрой линейной модели с помощью [рксенсембле](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[логистикрегрессион](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Создает список, содержащий имя функции и аргументы для обучения модели логистической регрессии с [рксенсембле](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[онекласссвм](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/oneclasssvm) | Создает список, содержащий имя функции и аргументы для обучения модели Онекласссвм с [рксенсембле](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|

## <a name="7-neural-networking-functions"></a>7 — функции нейронной сети

| Имя функции | Описание |
|---------------|-------------|
|[Оптимизатор](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/optimizer) | Задает алгоритмы оптимизации для алгоритма машинного обучения [ркснеуралнет](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) .|


## <a name="8-package-state-functions"></a>8 — функции состояния пакета

| Имя функции | Описание |
|---------------|-------------|
|[рксхашенв](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxHashEnv) | Объект среды, используемый для хранения состояния всего пакета. |


## <a name="how-to-use-microsoftml"></a>Как использовать MicrosoftML

Функции в **MicrosoftML** вызываемы в коде R, инкапсулированном в хранимых процедурах. Большинство разработчиков создают решения **MicrosoftML** локально, а затем выполняют перенос завершенного кода R в хранимые процедуры в качестве упражнения развертывания.

Пакет **MicrosoftML** для R установлен в "встроенном" в SQL Server 2017. Его также можно использовать с SQL Server 2016, если обновить компоненты R для экземпляра. [Обновление экземпляра SQL Server с помощью привязки](../install/upgrade-r-and-python.md)

Пакет по умолчанию не загружается. В качестве первого шага Загрузите пакет **MicrosoftML** , а затем загрузите **RevoScaleR** , если необходимо использовать удаленные контексты вычислений, связанные подключения или объекты источника данных. Затем сослаться на нужные вам функции.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

## <a name="see-also"></a>См. также

+ [Учебники по R](../tutorials/sql-server-r-tutorials.md)
+ [Сведения об использовании контекстов вычислений](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R для разработчиков SQL: Обучение и эксплуатацию модели](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Примеры продуктов Майкрософт на сайте GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [Справочник по R (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 