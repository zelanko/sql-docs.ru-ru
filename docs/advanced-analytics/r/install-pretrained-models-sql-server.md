---
title: "Установка моделей предварительно обученные машинного обучения в SQL Server | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 14789bafd555a4980875de78c85b32f535a8c0fe
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="install-pretrained-machine-learning-models-on-sql-server"></a>Установить предварительно обученные машинного обучения моделей, основанных на SQL Server

В этом разделе описывает, как добавлять предварительно обученные модели на экземпляре SQL Server, уже имеет служб R или машины обучения службы установлены.

Обновление для Microsoft R Server (или установки обновления Microsoft Server обучения машины) предоставляются предварительно обученные модели. Сведения о том, как обновить экземпляр и получить последнюю версию Microsoft R см. в разделе [обновление компонентов R в экземпляре служб R](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

Эти модели можно установить только выполнив отдельного установщика Windows для R Server.
Однако существуют некоторые дополнительные действия для использования при установке моделей на сервере SQL Server. В этом разделе описывается процесс.

## <a name="benefits-of-using-pretrained-models"></a>Преимущества использования предварительно обученные модели

Предварительно обученной модели сделаны доступными для поддержки клиентов, которые требуются для выполнения задач, таких как анализ мнений или изображения featurization, но не имеет ресурсы для получения больших наборов данных или обучения сложные модели. С помощью предварительно обученной модели позволяет приступить к работе над текста и наиболее эффективного обработки изображений.

В настоящее время модели, которые доступны являются моделями глубокие нейронные сети (DNN) для анализа и изображение классификация мнений. Все четыре предварительно обученные модели были обучена на CNTK. Конфигурации всех сетей, был основан на следующих справочных реализаций:

+ Resnet 18
+ Resnet 50
+ ResNet 101
+ AlexNet

Дополнительные сведения о глубокие остаточные сетях и их реализации с помощью CNTK статьях:

+ [Специалисты корпорации Майкрософт алгоритм задает его вехи ImageNet запроса](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Набор средств Майкрософт вычислительной сети предлагает обучения вычислительной мощности, но наиболее эффективный распределенных глубиной](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="how-to-install-the-models-on-sql-server"></a>Установка моделей на сервере SQL Server

   > [!NOTE]
   > 
   > Если используется отдельный установщик на основе Windows для установки Microsoft R Server или обновите экземпляр сервера SQL Server, предварительно обученные модели будут доступны из установщика. В разделе [Установка R Server для Windows](https://docs.microsoft.com/en-us/r-server/install/r-server-install-windows).
   > 
   > Для использования с Microsoft R Server модели может потребоваться некоторые дополнительные действия. Дополнительные сведения см. в разделе [описывается установка и развертывание предварительно обучения моделей машинного обучения с MicrosoftML](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models)

1. Предварительно обученные модели не устанавливаются по умолчанию при установке SQL Server; их необходимо добавить, запустив программу установки из командной строки после завершения программы установки SQL Server.

2. Откройте командную строку и перейдите к папке установки начальной загрузки для SQL Server, который также содержит установщик Microsoft R.

    В экземпляре по умолчанию, версия-Кандидат 1 SQL Server 2017 г. выражение будет следующим:
    
    `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\SQL2017RC1\x64\`

3. Укажите компонент для установки и папки, куда предварительно обученные модели должны быть добавлены, используя следующие аргументы:

  + Использование моделей с **R_SERVICES**

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir <SQL_DB_instance_folder>\R_SERVICES`

    Например чтобы включить использование предварительно обученные моделей с помощью R в экземпляре по умолчанию 2017 г. SQL Server, запуске этой инструкции:

    `RSetup.exe /install /component MLM /version 9.2.0.22 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES"`

  + Использование моделей с **PYTHON_SERVICES**

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir <SQL_DB_instance_folder>\PYTHON_SERVICES`

    Например чтобы включить использование предварительно обученные модели, с помощью Python, для экземпляра по умолчанию SQL Server 2017 г запуске этой инструкции:

    `RSetup.exe /install /component MLM /version 9.2.0.22 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES"`

4. Для параметра версии поддерживаются следующие значения:

    + Версия-кандидат 0: **9.1.0.0**
    + Версия-кандидат 1: **9.2.0.22**
    + Номер последней версии (не освобождается): **9.2.0.100**

5. Если установка выполнена успешно, следующие модели должны быть добавлены в ваш R\_СЛУЖБ или PYTHON\_папок СЛУЖБ:

    - AlexNet_Updated.model
    - ImageNet1K_mean.xml
    - pretrained.Model
    - ResNet_101_Updated.model
    - ResNet_18_Updated.model
    - ResNet_50_Updated.model

## <a name="examples"></a>Примеры

После установки моделей путем вызова из кода R можно использовать модели.

### <a name="image-featurization-example"></a>Пример featurization изображения

Предварительно обученные модели для изображений поддерживает featurization изображений, которые предоставляются. Чтобы использовать модель, вызовите **featurizeImage** преобразования.

+ [featurizeImage: преобразование Featurization образ машины обучения](https://docs.microsoft.com/r-server/r-reference/microsoftml/featurizeimage)

В этом примере см. второй блок кода. Загружено изображение, размер и создания признаков, предварительно обученные модели convolutional DNN. Выходные данные DNN featurizer затем используется для обучения модели линейной классификации изображений.

Изображение необходимо изменять в соответствии с требованиями обученной модели: изображений, используемых для обучения было 224 x 224 пикселей. При использовании модели AlexNet, изображение будет изменен для 227 x 227 пикселей.

```R
 model <- rxFastLinear(
     Label ~ Features,
     data = train,
     mlTransforms = list(
         loadImage(vars = list(Features = "Path")),
         resizeImage(vars = "Features", width = 224, height = 224), 
         extractPixels(vars = "Features"),
         featurizeImage(var = "Features")
         ),
     mlTransformVars = "Path")
```

> [!NOTE]
> 
> Не является возможность считывать или изменять самой предварительно обученные модели. Эта конкретная модель основана на [CNTK](https://docs.microsoft.com/cognitive-toolkit/) модели, но были сжаты с использованием собственного формата для повышения производительности.

### <a name="text-analysis-example"></a>Пример анализа текста

В этом примере демонстрируется использование предварительно обученные модели для классификации:

[Анализ мнений, с помощью Featurizer текста](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)
