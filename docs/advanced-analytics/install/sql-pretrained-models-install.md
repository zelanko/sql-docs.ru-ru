---
title: Установка предварительно обученных моделей машинного обучения
description: Добавьте предварительно обученные модели для анализа тональности и Image Добавление признаков в SQL Server 2017 Службы машинного обучения (R или Python) или SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 2045d6611d5f418a9ed102a1d776080973c08659
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344970"
---
# <a name="install-pre-trained-machine-learning-models-on-sql-server"></a>Установка предварительно обученных моделей машинного обучения на SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье объясняется, как использовать PowerShell для добавления бесплатных предварительно подготовленных моделей машинного обучения для *анализа тональности* и *Image добавление признаков* на экземпляр SQL Server с интеграцией R или Python. Предварительно обученные модели созданы корпорацией Майкрософт и готовы к использованию, добавлены в экземпляр в качестве задачи, выполняемой после установки. Дополнительные сведения об этих моделях см. в разделе " [ресурсы](#bkmk_resources) " этой статьи.

После установки предварительно обученные модели рассматриваются как сведения о реализации функций, связанных с питанием, в библиотеках MicrosoftML (R) и MicrosoftML (Python). Не следует (и не может) просматривать, настраивать или переучить модели, а также обрабатывать их как независимый ресурс в пользовательском коде или в парных других функциях. 

Чтобы использовать предварительно обученные модели, вызовите функции, перечисленные в следующей таблице.

| Функция R (MicrosoftML) | Функция Python (microsoftml) | Использование |
|--------------------------|-------------------------------|-------|
| [жетсентимент](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | [get_sentiment](https://docs.microsoft.com//machine-learning-server/python-reference/microsoftml/get-sentiment) | Создает положительную отрицательную оценку тональности для входных данных текста. |
| [феатуризеимаже](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | [featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Извлекает текстовые данные из входных данных файла изображения. |

## <a name="prerequisites"></a>предварительные требования

Алгоритмы машинного обучения — это ресурсоемкие вычисления. Рекомендуется 16 ГБ ОЗУ для рабочих нагрузок с низкой или средней интенсивностью, включая выполнение пошаговых руководств, использующих все примеры данных.

Для добавления предварительно обученных моделей необходимо иметь права администратора на компьютере и SQL Server.

Внешние скрипты должны быть включены, а SQL Server должна быть запущена служба панели запуска. Инструкции по установке содержат инструкции по включению и проверке этих возможностей. 

[Пакет MicrosoftML R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) или [пакет MicrosoftML Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) содержат предварительно обученные модели.

+ [SQL Server 2017 службы машинного обучения](sql-machine-learning-services-windows-install.md) включает в себя языковые версии библиотеки машинного обучения, поэтому это условие выполняется без каких-либо дополнительных действий с вашей стороны. Так как библиотеки существуют, можно использовать скрипт PowerShell, описанный в этой статье, чтобы добавить предварительно обученные модели в эти библиотеки.

+ [SQL Server 2016 служб r](sql-r-services-windows-install.md), которые относятся только к R, не включают [пакет MicrosoftML из упаковки](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) . Чтобы добавить MicrosoftML, необходимо выполнить [обновление компонента](../install/upgrade-r-and-python.md). Одним из преимуществ обновления компонентов является возможность одновременного добавления предварительно обученных моделей, что делает ненужным выполнение сценария PowerShell. Однако если вы уже обновляли, но не добавили предварительно обученные модели в первый раз, можно запустить сценарий PowerShell, как описано в этой статье. Он работает для обеих версий SQL Server. Прежде чем делать это, убедитесь, что библиотека MicrosoftML существует в папке C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library.


<a name="file-location"></a>

## <a name="check-whether-pre-trained-models-are-installed"></a>Проверить, установлены ли предварительно обученные модели

Пути установки для моделей R и Python приведены ниже.

+ Для R:`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64`

+ Для Python:`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\microsoftml\mxLibs`

Ниже перечислены имена файлов модели.

+ AlexNet\_обновлен. Model
+ ImageNet1K\_, среднее значение. XML
+ предварительно обученный. Model
+ ResNet\_101\_обновлена. Model
+ ResNet\_18\_Обновлено. модель
+ ResNet\_50\_обновлена. Model

Если модели уже установлены, перейдите к [шагу проверки](#verify) , чтобы подтвердить доступность.

## <a name="download-the-installation-script"></a>Скачивание скрипта установки

Щелкните [https://aka.ms/mlm4sql](https://aka.ms/mlm4sql) , чтобы скачать файл **Инсталл-млмоделс. ps1**.

## <a name="execute-with-elevated-privileges"></a>Выполнение с повышенными привилегиями

1. Запустите PowerShell. На панели задач щелкните правой кнопкой мыши значок программы PowerShell и выберите команду **Запуск от имени администратора**.
2. Введите полный путь к файлу сценария установки и укажите имя экземпляра. При наличии папки Downloads и экземпляра по умолчанию команда может выглядеть следующим образом:

   ```powershell
   PS C:\WINDOWS\system32> C:\Users\<user-name>\Downloads\Install-MLModels.ps1 MSSQLSERVER
   ```

**Проверки**

В подключении к Интернету SQL Server 2017 Машинное обучение экземпляре по умолчанию с R и Python, вы должны увидеть сообщения, аналогичные приведенным ниже.

   ```powershell
   MSSQL14.MSSQLSERVER
        Verifying R models [9.2.0.24]
        Downloading R models [C:\Users\<user-name>\AppData\Local\Temp]
        Installing R models [C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\]
        Verifying Python models [9.2.0.24]
        Installing Python models [C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\]
   PS C:\WINDOWS\system32>
   ```

<a name="verify"> </a>

## <a name="verify-installation"></a>Проверка установки

Сначала проверьте наличие новых файлов в [папке мкслибс](#file-location) Затем запустите демонстрационный код, чтобы убедиться, что модели установлены и работают. 

### <a name="r-verification-steps"></a>Шаги проверки R

1. Start **RGUI.EXE** at C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64.

2. Вставьте в командную строку следующий скрипт R.

    ```R
    # Create the data
    CustomerReviews <- data.frame(Review = c(
    "I really did not like the taste of it",
    "It was surprisingly quite good!",
    "I will never ever ever go to that place again!!"),
    stringsAsFactors = FALSE)

    # Get the sentiment scores
    sentimentScores <- rxFeaturize(data = CustomerReviews, 
                                    mlTransforms = getSentiment(vars = list(SentimentScore = "Review")))

    # Let's translate the score to something more meaningful
    sentimentScores$PredictedRating <- ifelse(sentimentScores$SentimentScore > 0.6, 
                                            "AWESOMENESS", "BLAH")

    # Let's look at the results
    sentimentScores
    ```

3. Нажмите клавишу ВВОД, чтобы просмотреть показатели тональности. Выходные данные должны выглядеть следующим образом:

    ```R
    > sentimentScores
                                            Review SentimentScore
    1           I really did not like the taste of it      0.4617899
    2                 It was surprisingly quite good!      0.9601924
    3 I will never ever ever go to that place again!!      0.3103435
    PredictedRating
    1            BLAH
    2     AWESOMENESS
    3            BLAH
    ```

### <a name="python-verification-steps"></a>Шаги проверки Python

1. Запустите **Python. exe** в папке C:\PROGRAM Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES.

2. Вставьте в командную строку следующий скрипт Python.

    ```python
    import numpy
    import pandas
    from microsoftml import rx_logistic_regression, rx_featurize, rx_predict, get_sentiment

    # Create the data
    customer_reviews = pandas.DataFrame(data=dict(review=[
                "I really did not like the taste of it",
                "It was surprisingly quite good!",
                "I will never ever ever go to that place again!!"]))
                
    # Get the sentiment scores
    sentiment_scores = rx_featurize(
        data=customer_reviews,
        ml_transforms=[get_sentiment(cols=dict(scores="review"))])
        
    # Let's translate the score to something more meaningful
    sentiment_scores["eval"] = sentiment_scores.scores.apply(
                lambda score: "AWESOMENESS" if score > 0.6 else "BLAH")
    print(sentiment_scores)
    ```

3. Нажмите клавишу ВВОД, чтобы напечатать баллы. Выходные данные должны выглядеть следующим образом:

    ```python
    >>> print(sentiment_scores)
                                                review    scores         eval
    0            I really did not like the taste of it  0.461790         BLAH
    1                  It was surprisingly quite good!  0.960192  AWESOMENESS
    2  I will never ever ever go to that place again!!  0.310344         BLAH
    >>>
    ```

> [!NOTE]
> Если Демонстрационные сценарии завершаются ошибкой, сначала проверьте расположение файла. В системах с несколькими экземплярами SQL Server или для экземпляров, работающих параллельно с автономными версиями, сценарий установки может некорректно считывать среду и размещать файлы в неправильном месте. Как правило, копирование файлов вручную в соответствующую папку мкслиб устраняет проблему.

## <a name="examples-using-pre-trained-models"></a>Примеры использования предварительно обученных моделей

Приведенная ниже ссылка включает пример кода, который вызывает предварительно обученные модели.

+ [Пример кода: анализ тональности с помощью Характеризатора текста](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

<a name="bkmk_resources"></a> 

## <a name="research-and-resources"></a>Исследование и ресурсы

В настоящее время доступные модели — это модели глубокой нейронной сети (DNN) для анализа тональности и классификации образов. Все предварительно обученные модели были обучены с помощью [набора средств](https://cntk.ai/Features/Index.html)Microsoft для вычислительной сети или **CNTK**.

Конфигурация каждой сети была основана на следующих эталонных реализациях:

+ ResNet-18
+ ResNet-50
+ ResNet-101
+ AlexNet

Дополнительные сведения о алгоритмах, используемых в этих моделях для глубокого обучения, а также о том, как они реализуются и обучены с помощью CNTK, см. в следующих статьях:

+ [Контрольный ImageNet по запросам для исследователей Майкрософт](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Набор средств вычислительной сети (Майкрософт) предлагает наиболее эффективную распределенную вычислительную производительность для глубокого обучения](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="see-also"></a>См. также

+ [Службы SQL Server 2016 R](sql-r-services-windows-install.md)
+ [SQL Server 2017 Службы машинного обучения](sql-machine-learning-services-windows-install.md)
+ [Обновление компонентов R и Python в экземплярах SQL Server](../install/upgrade-r-and-python.md)
+ [Пакет MicrosoftML для R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)
+ [пакет microsoftml для Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)
