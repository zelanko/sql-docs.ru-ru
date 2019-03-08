---
title: Установка предварительно обученных моделей машинного обучения — SQL Server машинного обучения
description: Добавьте предварительно обученных моделей для тональности Добавление признаков анализа и образ SQL Server 2017 служб машинного обучения (R или Python) или SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/18/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: fdfb322699045a46630b7aaed4b4811f20be945f
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2019
ms.locfileid: "57579084"
---
# <a name="install-pre-trained-machine-learning-models-on-sql-server"></a>Установка предварительно обученных моделей машинного обучения в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье объясняется, как использовать Powershell для добавления свободного предварительно обученных моделей машинного обучения для *анализ тональности* и *Добавление признаков изображений* к экземпляру ядра базы данных SQL Server, R или Python Интеграция. Предварительно обученной модели созданы корпорацией Майкрософт и готовые к использованию, добавляемый экземпляр ядра СУБД как задача после установки. Дополнительные сведения об этих моделях см. в разделе [ресурсы](#bkmk_resources) этой статьи.

После установки, предварительно обученных моделей, считаются деталь реализации, power конкретных функций в MicrosoftML (R) и библиотеках microsoftml (Python). Вам не следует и не может просматривать, настраивать или повторного обучения моделей, а также можно считать их как независимый ресурс в пользовательском коде или пару других функций. 

Чтобы использовать предварительно обученных моделей, вызов функции, перечисленные в следующей таблице.

| Функция R (MicrosoftML) | Функции Python (microsoftml) | Использование |
|--------------------------|-------------------------------|-------|
| [getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | [get_sentiment](https://docs.microsoft.com//machine-learning-server/python-reference/microsoftml/get-sentiment) | Создает оценку тональности положительные отрицательные текстовые входные данные. [Дополнительные сведения](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/11/01/sentiment-analysis-with-python-in-sql-server-machine-learning-services/).|
| [featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | [featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Извлекает текстовые данные из входных файлов изображений. [Дополнительные сведения](https://blogs.msdn.microsoft.com/mlserver/2017/04/12/image-featurization-with-a-pre-trained-deep-neural-network-model/). |

## <a name="prerequisites"></a>предварительные требования

Алгоритмы машинного обучения с большим объемом вычислений. Рекомендуется 16 ГБ ОЗУ для низкой средних рабочих нагрузок, включая завершения учебника пошаговые руководства, используя все образцы данных.

Вам потребуются права администратора на компьютере и SQL Server для добавления предварительно обученных моделей.

Необходимо включить внешние скрипты и должна быть запущена служба панели запуска SQL Server. Инструкции по установке описаны шаги по включению и проверка того, эти возможности. 

[Пакет MicrosoftML R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) или [пакет microsoftml Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) содержат предварительно обученной модели.

+ [SQL Server 2017 службы машинного обучения](sql-machine-learning-services-windows-install.md) включает в себя обе версии языка библиотеки машинного обучения, поэтому это предварительное условие удовлетворяется с никаких дополнительных действий со стороны пользователя. Так как имеются библиотеки, можно использовать скрипт PowerShell, описанный в этой статье для добавления предварительно обученных моделей для этих библиотек.

+ [SQL Server 2016 R Services](sql-r-services-windows-install.md), являющийся R, не включает [пакет MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) без дополнительной настройки. Чтобы добавить MicrosoftML, необходимо выполнить [обновления компонента](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). Одним из преимуществ обновления компонента является, можно одновременно добавить предварительно обученных моделей, что делает сценария PowerShell ненужные. Однако если вы уже обновлены, но пропустили Добавление предварительно обученных моделей с первого раза, можно запустить сценарий PowerShell, как описано в этой статье. Он работает для обеих версий SQL Server. Перед выполнением, убедитесь, что библиотека MicrosoftML существует в C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library.


<a name="file-location"></a>

## <a name="check-whether-pre-trained-models-are-installed"></a>Проверить, установлены ли предварительно обученных моделей

Ниже приведены пути установки для моделей R и Python.

+ Для R: `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64`

+ Для Python: `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\microsoftml\mxLibs`

Ниже перечислены имена файлов модели.

+ AlexNet\_Updated.model
+ ImageNet1K\_mean.xml
+ pretrained.Model
+ ResNet\_101\_Updated.model
+ ResNet\_18\_Updated.model
+ ResNet\_50\_Updated.model

Если модели уже установлены, перейти к шагу [шаг проверки](#verify) для подтверждения доступности.

## <a name="download-the-installation-script"></a>Загрузите сценарий установки

Нажмите кнопку [ https://aka.ms/mlm4sql ](https://aka.ms/mlm4sql) для загрузки файла **установки MLModels.ps1**.

## <a name="execute-with-elevated-privileges"></a>Выполнение с повышенными привилегиями

1. Запустите PowerShell. На панели задач щелкните правой кнопкой мыши значок программы PowerShell и выберите **Запуск от имени администратора**.
2. Введите полный путь к файлу сценария установки и добавьте имя экземпляра. При условии, что в папке «загрузки» и экземпляр по умолчанию, команда может выглядеть следующим образом:

   ```powershell
   PS C:\WINDOWS\system32> C:\Users\<user-name>\Downloads\Install-MLModels.ps1 MSSQLSERVER
   ```

**Выходные данные**

На подключенной к Интернету машинного обучения SQL Server 2017 экземпляру по умолчанию с помощью R и Python вы увидите примерно следующие сообщения.

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

Во-первых, проверьте наличие новых файлов в [mxlibs папку](#file-location). Затем выполните демонстрационного кода, чтобы убедиться, что эти модели являются установлена и работает. 

### <a name="r-verification-steps"></a>Шаги проверки R

1. Start **RGUI.EXE** at C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64.

2. Вставьте следующий скрипт R в командной строке.

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

3. Нажмите клавишу ВВОД, чтобы просмотреть оценку мнений. Выходные данные должны иметь следующий вид:

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

1. Запуск **Python.exe** в C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES.

2. Вставьте следующий скрипт Python в командной строке

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

3. Нажмите клавишу ВВОД, чтобы распечатать результаты. Выходные данные должны иметь следующий вид:

    ```python
    >>> print(sentiment_scores)
                                                review    scores         eval
    0            I really did not like the taste of it  0.461790         BLAH
    1                  It was surprisingly quite good!  0.960192  AWESOMENESS
    2  I will never ever ever go to that place again!!  0.310344         BLAH
    >>>
    ```

> [!NOTE]
> Если не удается демонстрационные скрипты, сначала проверьте расположение файла. В системах наличие нескольких экземпляров SQL Server, и для экземпляров, где выполняется side-by-side с автономной версии, это возможно для сценария установки неверно прочесть окружение и поместить файлы в неправильном месте. Как правило вручную копирования файлов в папку правильный mxlib решает проблему.

## <a name="examples-using-pre-trained-models"></a>Примеры использования предварительно обученных моделей

Приведенные ниже ссылки включают пошаговые руководства и пример кода, вызов предварительно обученных моделей.

+ [Анализ тональности с помощью Python в службах машинного обучения SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/11/01/sentiment-analysis-with-python-in-sql-server-machine-learning-services/)

+ [Добавление признаков изображений с помощью предварительно обученной модели глубокой нейронной сети](https://blogs.msdn.microsoft.com/mlserver/2017/04/12/image-featurization-with-a-pre-trained-deep-neural-network-model/)

  Предварительно обученной модели для изображений поддерживает добавление признаков изображений, которые вы указали. Чтобы использовать модель, следует вызвать **featurizeImage** преобразования. Загрузить изображение, размер и признаки с помощью обученной модели. Выходные данные DNN featurizer затем используется для обучения модели линейной классификации изображений. Чтобы использовать эту модель, все изображения необходимо изменять в соответствии с требованиями обученной модели. Например, если вы используете модель AlexNet, изображения должны изменяться в для 227 x 227 пикселей.

+ [Пример кода: Анализ тональности с помощью Featurizer текста](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

<a name="bkmk_resources"></a> 

## <a name="research-and-resources"></a>Справочные материалы и ресурсы

В настоящее время модели, которые доступны, моделей глубокой нейронной сети (DNN) для классификации мнений анализа и изображения. Все предварительно обученных моделей прошли обучение с помощью корпорации Майкрософт [Toolkit сети вычисление](https://cntk.ai/Features/Index.html), или **CNTK**.

Конфигурация каждой сети был основан на следующих базовых реализаций:

+ ResNet-18
+ ResNet-50
+ ResNet-101
+ AlexNet

Дополнительные сведения об алгоритмах, используемых в этих моделей глубокого обучения и об их реализации и обучена с использованием CNTK, см. в статьях:

+ [Исследователи корпорации Майкрософт алгоритм задает его запрос ImageNet вехи](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Вычислительные сети средств для обеспечения предлагает наиболее эффективный распределенного глубокого обучения вычислительную мощность](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="see-also"></a>См. также

+ [SQL Server 2016 R Services](sql-r-services-windows-install.md)
+ [SQL Server 2017 службы машинного обучения](sql-machine-learning-services-windows-install.md)
+ [Обновление компонентов R и Python в экземплярах SQL Server](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
+ [Пакет MicrosoftML для R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)
+ [пакет microsoftml для Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)
