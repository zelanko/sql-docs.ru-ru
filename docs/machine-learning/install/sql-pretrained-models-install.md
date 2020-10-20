---
title: Установка предварительно обученных моделей
description: Добавление предварительно обученных моделей для анализа тональности и определения характеристик изображений в Службы машинного обучения SQL Server (R или Python) или SQL Server R Services.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/30/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a509b16abc2c52f504cf3783f5fb22370faaef94
ms.sourcegitcommit: afb02c275b7c79fbd90fac4bfcfd92b00a399019
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2020
ms.locfileid: "91956755"
---
# <a name="install-pre-trained-machine-learning-models-on-sql-server"></a>Установка предварительно обученных моделей машинного обучения в SQL Server
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

В этой статье объясняется, как использовать PowerShell для добавления бесплатных предварительно обученных моделей машинного обучения для *анализа тональности* и *определения характеристик изображений* в экземпляр SQL Server с интегрированным R или Python. Предварительно обученные модели созданы корпорацией Майкрософт и готовы к использованию. Они добавлены в экземпляр в качестве задачи, выполняемой после установки. Дополнительные сведения об этих моделях см. в разделе [Ресурсы](#bkmk_resources) этой статьи.

После установки предварительно обученные модели рассматриваются как компонент реализации, на основе которого работают специальные функции в библиотеках MicrosoftML (R) и microsoftml (Python). Вы не можете просматривать, настраивать и повторно обучать модели, а также обрабатывать их как независимый ресурс в пользовательском коде или в других функциях. 

Чтобы использовать предварительно обученные модели, вызовите функции, указанные в следующей таблице.

| Функция R (MicrosoftML) | Функция Python (microsoftml) | Использование |
|--------------------------|-------------------------------|-------|
| [getSentiment](/machine-learning-server/r-reference/microsoftml/getsentiment) | [get_sentiment](//machine-learning-server/python-reference/microsoftml/get-sentiment) | Создает положительную или отрицательную оценку тональности для текстовых входных данных. |
| [featurizeImage](/machine-learning-server/r-reference/microsoftml/featurizeimage) | [featurize_image](/machine-learning-server/python-reference/microsoftml/featurize-image) | Извлекает текстовые данные из входного файла изображения. |

## <a name="prerequisites"></a>Предварительные требования

Алгоритмы машинного обучения обладают высокими требованиями к вычислительным ресурсам. Мы рекомендуем использовать 16 ГБ ОЗУ для рабочих нагрузок с низкой или средней интенсивностью, включая пошаговые руководства со всеми примерами данных.

Для добавления предварительно обученных моделей необходимо иметь права администратора на компьютере и на SQL Server.

Необходимо включить внешние сценарии, а на SQL Server должна быть запущена служба панели запуска. Инструкции по установке содержат инструкции по включению и проверке этих компонентов. 

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
[Пакет R MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package) и [пакет Python microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) содержат предварительно обученные модели.

[Службы машинного обучения SQL Server](sql-machine-learning-services-windows-install.md) включают версии библиотеки машинного обучения для обоих языков, поэтому это условие выполняется без каких-либо дополнительных действий с вашей стороны. Так как библиотеки существуют, можно использовать сценарий PowerShell, описанный в этой статье, чтобы добавить предварительно обученные модели в эти библиотеки.
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
[Пакет MicrosoftML R](/machine-learning-server/r-reference/microsoftml/microsoftml-package) содержит предварительно обученные модели.

Службы [SQL Server R Services](sql-r-services-windows-install.md), предназначенные только для языка R, не содержат [пакет MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package). Чтобы добавить пакет MicrosoftML, необходимо выполнить [обновление компонентов](../install/upgrade-r-and-python.md). Одним из преимуществ обновления компонентов является возможность одновременного добавления предварительно обученных моделей, что делает ненужным выполнение сценария PowerShell. Однако если вы уже выполнили обновление, но не добавили предварительно обученные модели в первый раз, можно выполнить сценарий PowerShell, как описано в этой статье. Он работает для обеих версий SQL Server. Перед выполнением сценария убедитесь, что библиотека MicrosoftML в `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library` существует.
::: moniker-end

<a name="file-location"></a>

## <a name="check-whether-pre-trained-models-are-installed"></a>Проверка установки предварительно обученных моделей

Пути установки для моделей R и Python приведены ниже:

+ Для R: `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64`

+ Для Python: `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\microsoftml\mxLibs`

Ниже перечислены имена файлов модели:

+ AlexNet\_Updated.model
+ ImageNet1K\_mean.xml
+ pretrained.model
+ ResNet\_101\_Updated.model
+ ResNet\_18\_Updated.model
+ ResNet\_50\_Updated.model

Если модели уже установлены, перейдите к [шагу проверки](#verify), чтобы подтвердить доступность.

## <a name="download-the-installation-script"></a>Скачивание сценария установки

Щелкните [https://aka.ms/mlm4sql](https://aka.ms/mlm4sql), чтобы скачать файл **Install-MLModels.ps1**.

## <a name="execute-with-elevated-privileges"></a>Выполнение с повышенными привилегиями

1. Запустите PowerShell. На панели задач щелкните правой кнопкой мыши значок программы PowerShell и выберите **Запуск от имени администратора**.
2. Введите полный путь к файлу сценария установки, указав имя экземпляра. Если сценарий находится в папке Downloads и используется экземпляр по умолчанию, команда может выглядеть следующим образом:

   ```powershell
   PS C:\WINDOWS\system32> C:\Users\<user-name>\Downloads\Install-MLModels.ps1 MSSQLSERVER
   ```

**Выходные данные**

На экземпляре по умолчанию Служб машинного обучения SQL Server с R и Python, подключенном к Интернету, вы должны увидеть сообщения, аналогичные приведенным ниже.

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

Сначала проверьте наличие новых файлов в папке [mxlibs](#file-location). Затем запустите демонстрационный код, чтобы убедиться, что модели установлены и работают. 

### <a name="r-verification-steps"></a>Действия по выполнению проверки для R

1. Запустите файл **RGUI.EXE** в папке C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64.

2. Вставьте в командную строку следующий сценарий R.

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

3. Нажмите клавишу ВВОД, чтобы просмотреть оценки тональности. Выходные данные должны выглядеть следующим образом:

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

### <a name="python-verification-steps"></a>Действия по выполнению проверки для Python

1. Запустите файл **Python.exe** в папке C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES.

2. Вставьте в командную строку следующий сценарий Python.

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

3. Нажмите клавишу ВВОД, чтобы распечатать оценки. Выходные данные должны выглядеть следующим образом:

    ```python
    >>> print(sentiment_scores)
                                                review    scores         eval
    0            I really did not like the taste of it  0.461790         BLAH
    1                  It was surprisingly quite good!  0.960192  AWESOMENESS
    2  I will never ever ever go to that place again!!  0.310344         BLAH
    >>>
    ```

> [!NOTE]
> Если демонстрационные сценарии завершаются с ошибкой, проверьте расположение файла. В системах с несколькими экземплярами SQL Server или для экземпляров, работающих параллельно с автономными версиями, сценарий установки может некорректно считывать параметры среды и размещать файлы в неправильном месте. Как правило, для устранения этой проблемы достаточно вручную скопировать файлы в правильную папку mxlib.

## <a name="examples-using-pre-trained-models"></a>Примеры использования предварительно обученных моделей

По приведенной ссылке можно найти пример кода, в котором вызываются предварительно обученные модели.

+ [Пример кода: анализ тональности с помощью определения характеристик текста](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

<a name="bkmk_resources"></a> 

## <a name="research-and-resources"></a>Исследования и ресурсы

Сейчас доступны модели глубокой нейронной сети для анализа тональности и классификации изображений. Все предварительно обученные модели были обучены с помощью [Computation Network Toolkit](https://cntk.ai/Features/Index.html) от корпорации Майкрософт (**CNTK**).

Конфигурация каждой сети была основана на следующих эталонных реализациях:

+ ResNet-18
+ ResNet-50
+ ResNet-101
+ AlexNet

Дополнительные сведения об алгоритмах, используемых в этих моделях глубокого обучения, и о том, как они реализуются и обучаются с помощью CNTK, см. в следующих статьях:

+ [Наборы алгоритмов от исследователей Майкрософт устанавливают веху в решении задачи ImageNet](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft Computational Network Toolkit предлагает наиболее эффективную распределенную вычислительную производительность для глубокого обучения](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="see-also"></a>См. также раздел

+ [Службы машинного обучения SQL Server](sql-machine-learning-services-windows-install.md)
+ [Обновление компонентов R и Python в экземплярах SQL Server](../install/upgrade-r-and-python.md)
+ [Пакет MicrosoftML для R](/machine-learning-server/r-reference/microsoftml/microsoftml-package)
+ [Пакет microsoftml для Python](/machine-learning-server/python-reference/microsoftml/microsoftml-package)
