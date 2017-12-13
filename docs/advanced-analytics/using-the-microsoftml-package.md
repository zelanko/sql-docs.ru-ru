---
title: "С помощью пакета MicrosoftML с SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 08/23/2017
ms.prod: sql-non-specified
ms.prod_service: r-services
ms.service: 
ms.component: advanced-analytics
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 1c377717-e281-431e-8171-3924dcce1cdd
caps.latest.revision: "132"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b802daf9a02734245bc5adb0695fded14063fca5
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="using-the-microsoftml-package-with-sql-server"></a>С помощью пакета MicrosoftML с SQL Server

[ **MicrosoftML** ](https://msdn.microsoft.com/microsoft-r/microsoftml-introduction) пакет, который входит в состав Microsoft R Server и SQL Server 2017 г. включает в себя несколько алгоритмов машинного обучения. Эти API-интерфейсы разработанные корпорацией Майкрософт для внутренних машинного обучения приложений и были более точно распределить ресурсы за несколько лет, для поддержки высокой производительности на больших данных с помощью многоядерными обработки и потоковой передачи данных быстро. MicrosoftML также включает множество преобразований для обработки изображений и текста.

В SQL Server 2017 г CTP 2.0 была добавлена поддержка языка Python. **Microsoftml** пакета Python содержит функции, эквивалентные функциям в пакете MicrosoftML для R. 

+ **MicrosoftML для R**

    Введение в пакет и ссылка: [MicrosoftML: машинные алгоритмы обучения R](https://docs.microsoft.com/en-us/r-server/r-reference/microsoftml/microsoftml-package)

    Поскольку R учитывается регистр, убедитесь, что необходимо сослаться на имя правильно при загрузке пакета.

+ **microsoftml для Python**

    Введение в пакет и ссылка: [microsoftml (Библиотека функций Python)](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package). 

## <a name="whats-in-microsoftml"></a>Возможности MicrosoftML

MicrosoftML содержит разнообразные машинного обучения алгоритмы и преобразований, которые оптимизированы для повышения производительности.

### <a name="machine-learning-algorithms"></a>Алгоритмы машинного обучения

-  Линейные модели: `rxFastLinear` линейной ученик основан на вероятностного двух координат Восхождение, можно использовать для двоичной классификации или регрессии. Модель поддерживает регуляризацию L1 и L2.

- Дерево и принятия решений модели леса принятия решений: `rxFastTree` — это алгоритм дерева решений, ранее известные как FastRank, который был разработан для использования в Bing. Это одно из самых популярных и быстрых средств обучения. Поддерживает двоичную классификацию и регрессию.

  `rxFastForest`модель логистической регрессии основана на метод случайного леса. Этот вариант похож на функцию `rxLogit` в RevoScaleR, но поддерживает регуляризацию L1 и L2. Поддерживает двоичную классификацию и регрессию.

- Алгоритм логистической регрессии: `rxLogisticRegression` аналогична модель логистической регрессии `rxLogit` функции в RevoScaleR, с дополнительной поддержкой L1 и L2. Поддерживает двоичные или мультиклассовой классификации.

- Нейронных сетей: `rxNeuralNet` функция поддерживает двоичной классификации мультиклассовой классификации и регрессии с использованием нейронных сетей. Настраиваемые и поддерживает сложные сети с применением ускорения GPU, с помощью одного GPU.

- Обнаружение аномалий.  `rxOneClassSvm` Функция основана на метод SVM, но оптимизирована для двоичной классификации в несбалансированной наборов данных.

### <a name="transformation-functions"></a>Функции преобразования

MicrosoftML включает множество специализированных функций, которые полезны для преобразования данных и извлечения компонентов.

- Следующие возможности обработки текста `featurizeText` и `getSentiment` функции. Число n грамм, определить язык, используемый или выполнять нормализацию текста. Также можно выполнять операции, например удаление стоп-слово очистки общий текст или создавать хэшированное или на основе количества признаки из текста.

- Выбор компонентов и возможностей функции преобразования, такие как `selectFeatures` или `getSentiment`, анализировать данные и создавать функции, которые часто используются для моделирования.

- Работать с категориальные переменные, такие как использование `categorical` или `categoricalHash`, которой преобразование категориальных значений на индексированного массива для повышения производительности.

- Функции, специфичные для обработки и анализа, такие как `extractPixels` или `featurizeImage`, позволяют получить большая часть сведений образов и быстрее обрабатывать образы.

Дополнительные сведения см. в статье [MicrosoftML: State-of-the-Art Machine Learning R Algorithms from Microsoft Corporation](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml) (MicrosoftML. Современные алгоритмы машинного обучения от корпорации Майкрософт).

## <a name="how-to-use-microsoftml"></a>Как использовать MicrosoftML

В этом разделе описывается найдите и загрузите его в коде R и Python.

+ Пакет MicrosoftML для R установлен по умолчанию с Microsoft R Server 9.1.0 и 2017 г. SQL Server.

    Эта схема также доступна для использования с SQL Server 2016 при обновлении компонентов R для экземпляра, с помощью установщика Microsoft R Server, как описано здесь: [обновить экземпляр SQL Server с помощью привязки](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

+ **Microsoftml** пакета на Python устанавливается по умолчанию вместе с SQL Server 2017 г. 

   Чтобы использовать этот пакет, рекомендуется обновить до версии-кандидата 2 или более поздней. Более ранней версии, выпущенной с версии-кандидата 1, но библиотеке произошло существенное редакции, включая изменения в имена функций. 

Тем не менее R и Python, пакет не загружается по умолчанию. Таким образом необходимо явно загрузить пакет как часть кода, чтобы использовать его функции.

### <a name="calling-microsoftml-functions-from-r-in-sql-server"></a>Вызов функций MicrosoftML из R в SQL Server

В коде R загрузить пакет MicrosoftML и вызывать его функции, как в других пакетах.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

**Примечания**

+ Пакет MicrosoftML полностью интегрирован с конвейером обработки данных, предоставляемые пакета RevoScaleR. Таким образом можно использовать пакет MicrosoftML в любом контексте вычислений на основе Windows, включая экземпляр SQL Server с расширениями обучения машины включена.

    Однако MicrosoftML требует ссылку на RevoScaleR и функций для использования удаленных контекстов вычислений.

### <a name="calling-microsoftml-functions-from-python-in-sql-server"></a>Вызов функций microsoftml из Python в SQL Server

Для вызова функций из пакета, в коде Python Импорт **microsoftml** пакета, а также импортировать **revoscalepy** Если необходимо использовать контекстах удаленных вычислений или связанные подключения или источник данных объекты. Затем ссылаться на отдельные функции, которые необходимо.

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

**Примечания**

+ В SQL Server 2017 г **microsoftml** Python35-совместимый модуль. 

+ Функции в **microsoftml** интегрированы с вычислительных контекстов и источников данных, поддерживаемых **revoscalepy**. Таким образом, можно воспользоваться **microsoftml** пакета Python для создания и оценки из моделей в любом контексте вычислений на основе Windows, включая экземпляр SQL Server с расширениями машины обучения. включена.

    Тем не менее **microsoftml** для Python требует ссылку на **revoscalepy** и его функций для использования удаленных контекстов вычислений.

Дополнительные сведения о revoscalepy см. в разделе:

+ [Что такое revoscalepy](python/what-is-revoscalepy.md)

+ [Библиотека функций revoscalepy](https://docs.microsoft.com/en-us/r-server/python-reference/revoscalepy/revoscalepy-package) 
