---
title: Использование пакета MicrosoftML со SQL Server | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a75ed22e46576c701e281f495d5bc123ca489526
ms.sourcegitcommit: 2a47e66cd6a05789827266f1efa5fea7ab2a84e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/31/2018
ms.locfileid: "43348465"
---
# <a name="using-the-microsoftml-package-with-sql-server"></a>Использование пакета MicrosoftML со SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[ **MicrosoftML** ](https://msdn.microsoft.com/microsoft-r/microsoftml-introduction) пакет, который входит в состав Microsoft R Server и SQL Server 2017 включает в себя несколько алгоритмов машинного обучения. Эти интерфейсы API были разработаны корпорацией Майкрософт для внутреннего приложения для машинного обучения и были уточненные годы для поддержки высокой производительности на основе больших данных с помощью многоядерную обработку и быструю потоковую передачу данных. MicrosoftML также включает в себя множество преобразований для обработки изображений и текста.

В SQL Server 2017 была добавлена поддержка языка Python. **Microsoftml** пакетом для Python содержит функции, эквивалентные функциям в пакет MicrosoftML для R. 

+ **MicrosoftML для R**

    Справочник по введение и пакета: [MicrosoftML: машинные алгоритмы обучения R](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)

    Так как R учитывается регистр, убедитесь, что вы указываете имя правильно при загрузке пакета.

+ **microsoftml для Python**

    Справочник по введение и пакета: [microsoftml (функции библиотеки для Python)](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package). 

## <a name="whats-in-microsoftml"></a>Что такое в MicrosoftML

MicrosoftML содержит широкий набор алгоритмов машинного обучения и преобразований, которые оптимизированы для повышения производительности.

### <a name="machine-learning-algorithms"></a>Алгоритмы машинного обучения

-  Линейные модели: `rxFastLinear` линейное средство обучения основан на стохастического парного координатного подъема, который может использоваться для двоичной классификации или регрессии. Модель поддерживает регуляризацию L1 и L2.

- Дерево и принятия решений модели леса принятия решений: `rxFastTree` — это алгоритм дерева принятия решений, ранее известный как FastRank, который был разработан для использования в Bing. Это одно из самых популярных и быстрых средств обучения. Поддерживает двоичную классификацию и регрессию.

  `rxFastForest` модель логистической регрессии на основе метода случайного леса. Этот вариант похож на функцию `rxLogit` в RevoScaleR, но поддерживает регуляризацию L1 и L2. Поддерживает двоичную классификацию и регрессию.

- Логистическая Регрессия: `rxLogisticRegression` подобна модели логистической регрессии `rxLogit` функции в RevoScaleR, с дополнительной поддержкой регуляризации L1 и L2. Поддерживает двоичную или многоклассовую классификацию.

- Нейронных сетей: `rxNeuralNet` функция поддерживает двоичной классификации, многоклассовой классификации и регрессии с использованием нейронных сетей. Настраиваемые и поддерживает сверточные сети с ускорением GPU, с помощью одного графического Процессора.

- Обнаружение аномалий.  `rxOneClassSvm` Функция зависит от метода опорных Векторов, однако оптимизирован для двоичной классификации в несбалансированных наборах данных.

### <a name="transformation-functions"></a>Функции преобразования

MicrosoftML включает в себя множество специализированных функций, которые можно использовать для преобразования данных и извлечения компонентов.

- Обработка текста возможности включают в себя `featurizeText` и `getSentiment` функции. Вычисление n грамм, определения используемого языка или выполняют нормализацию текста. Можно также выполнять операции, такие как удаление стоп-слово очистки общий текст или создания хэшированных или на основе количества функций из текста.

- Выбор компонентов и возможностей функции преобразования, такие как `selectFeatures` или `getSentiment`, анализ данных и создание признаков, которые наиболее важны для моделирования.

- Работать с категориальными переменными с помощью таких как `categorical` или `categoricalHash`, которой преобразование категориальных значений в индексированных массивы для повышения производительности.

- Функции, специфичные для обработки и анализа, таких как `extractPixels` или `featurizeImage`, позволяют получить большая часть сведений образов и быстрее обработки изображений.

Дополнительные сведения см. в статье [MicrosoftML: State-of-the-Art Machine Learning R Algorithms from Microsoft Corporation](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml) (MicrosoftML. Современные алгоритмы машинного обучения от корпорации Майкрософт).

## <a name="how-to-use-microsoftml"></a>Как использовать MicrosoftML

В этом разделе описывается, как для поиска и загрузки пакета в коде R и Python.

+ Пакет MicrosoftML для R устанавливается по умолчанию с помощью Microsoft R Server 9.1.0 и в SQL Server 2017.

    Оно доступно для использования с SQL Server 2016 при обновлении компонентов R для экземпляра, с помощью установщика Microsoft R Server как описано здесь: [обновить экземпляр SQL Server с помощью привязки](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

+ **Microsoftml** пакетом для Python устанавливается по умолчанию вместе с SQL Server 2017 

   Чтобы использовать этот пакет, мы рекомендуем выполнить обновление релиз-кандидат 2 или более поздней версии. Более ранней версии был выпущен вместе с версии-кандидата 1, но библиотека претерпел значительные редакции, включая изменения в имена функций. 

Тем не менее R и Python, пакет не загружается по умолчанию; Таким образом необходимо явно загрузить пакет как часть код, чтобы использовать его функции.

### <a name="calling-microsoftml-functions-from-r-in-sql-server"></a>Вызов функции MicrosoftML из R в SQL Server

В коде R загрузить пакет MicrosoftML и вызывать его функции, как и любой другой пакет.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

**Примечания**

+ Пакет MicrosoftML полностью интегрирован с конвейером обработки данных, предоставляемые пакетом RevoScaleR. Таким образом можно использовать пакет MicrosoftML в любом контексте вычислений на основе Windows, включая экземпляр SQL Server с поддержкой расширений машинного обучения.

    Тем не менее MicrosoftML требует ссылку на RevoScaleR и ее функций для использования удаленных контекстов вычислений.

### <a name="calling-microsoftml-functions-from-python-in-sql-server"></a>Вызов функции microsoftml из Python в SQL Server

Для вызова функций из пакета, в коде Python, импортировать **microsoftml** пакета, а также импортировать **revoscalepy** Если вам нужно использовать контексты удаленных вычислений или связанные подключения или источник данных объекты. Затем ссылаться на отдельные функции, которые вам нужны.

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

**Примечания**

+ В SQL Server 2017 **microsoftml** — это модуль Python35-совместимой. 

+ Функции в **microsoftml** интегрированы с вычислительных контекстов и источниками данных, поддерживаемых **revoscalepy**. Таким образом, можно использовать **microsoftml** пакет Python для создания и оценки на основе моделей в любом контексте вычислений на основе Windows, включая экземпляр SQL Server, который имеет расширений машинного обучения. включено.

    Тем не менее **microsoftml** для Python требуется ссылка на **revoscalepy** и ее функций для использования удаленных контекстов вычислений.

Дополнительные сведения о revoscalepy см. в разделе:

+ [Что такое revoscalepy](python/what-is-revoscalepy.md)

+ [Библиотека revoscalepy-функция](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) 
