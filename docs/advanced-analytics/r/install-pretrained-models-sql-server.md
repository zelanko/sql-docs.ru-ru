---
title: "Установка моделей предварительно обученные машинного обучения в SQL Server | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 10/18/2017
ms.prod: sql-server-2017
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 8f4a145700d12f31a868cc3fc20a9dbdbe6f45ea
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="install-pretrained-machine-learning-models-on-sql-server"></a>Установить предварительно обученные машинного обучения моделей, основанных на SQL Server

В этой статье описывает, как добавлять предварительно обученные модели на экземпляре SQL Server, уже имеет служб R или машины обучения службы установлены.

Предварительно обученные модели представляют собой параметр при установке Microsoft R Server или обучения компьютере, на сервер с помощью автономного установщика. Можно использовать этот установщик для получения только предварительно обученные модели или его можно использовать для обновления машинного обучения компонентов в экземпляр SQL Server 2016 или 2017 г. SQl Server.

После загрузки предварительно обученные модели с помощью программы установки, существуют некоторые дополнительные действия по настройке моделей для использования с SQL Server. В этой статье описан процесс.

Дополнительные сведения см. в следующих статьях:

+ [Предварительно обученный моделей машинного обучения для анализа и образа обнаружения мнений](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)

+ [Обновление компонентов R в экземпляре служб R](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="benefits-of-using-pretrained-models"></a>Преимущества использования предварительно обученные модели

Эти предварительно обученной модели, созданные для клиентов, которым требуется выполнять задачи, такие как анализ мнений или изображения featurization, но нет ресурсов для получения больших наборов данных или обучения сложные модели. С помощью предварительно обученной модели позволяет приступить к работе над текста и наиболее эффективного обработки изображений.

В настоящее время модели, которые доступны являются моделями глубокие нейронные сети (DNN) для анализа и изображение классификация мнений. Все предварительно обученные модели прошли обучение с помощью корпорации Майкрософт [Toolkit сети вычисление](https://cntk.ai/Features/Index.html), или **CNTK**. 

Конфигурации всех сетей, был основан на следующих справочных реализаций:

+ ResNet 18
+ ResNet 50
+ ResNet 101
+ AlexNet

Дополнительные сведения о сетях углубленного обучения и их реализации с помощью CNTK статьях:

+ [Специалисты корпорации Майкрософт алгоритм задает его вехи ImageNet запроса](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Набор средств Майкрософт вычислительной сети предлагает обучения вычислительной мощности, но наиболее эффективный распределенных глубиной](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="how-to-install-the-models-on-sql-server"></a>Установка моделей на сервере SQL Server

1. Запустите отдельного установщика Windows для компьютера сервера обучения. Для расположения загрузки см.:

    + [Установка машинного обучения для Windows Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
    + [Установка R Server 9.1 для Windows](https://docs.microsoft.com/r-server/install/r-server-install-windows)

2. Выбор компонентов для установки зависит от того, получение только модели, или выполнение других обновлений с помощью установщика.
 
    + Если это новую установку сервера Machine обучения, и не требуется вносить другие изменения R или Python компоненты, выберите **только** параметр предварительно обученные модели. Примите все остальные, включая лицензионных соглашений.

    + Обновление компонентов R или Python, в то же время, выберите язык (R, Python и/или), который требуется обновить и выберите параметр предварительно обученные модели. Выберите один или несколько экземпляров для применения этих изменений.

    + Если ранее вы установили машины Server обучения и обновленные компоненты R или Python, с помощью параметра привязки, оставьте все ранее выбранные варианты **как**и выберите параметры предварительно обученные модели. Не отменяйте Выбор все ранее выбранные параметры, или они будут удалены.

3. После завершения установки откройте командную строку Windows **администратор**и перейдите к папке установки начальной загрузки для SQL Server, который также содержит установщик Microsoft R. Папка в экземпляре по умолчанию 2017 г. SQL Server, будет:
    
    `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\SQL2017\x64\`

4. Укажите компонент для установки, версии и к папке, содержащей исходные файлы модели, используя аргументы RSetup.exe, как показано в следующих примерах:

  + Использование моделей с **R_SERVICES**, используйте следующий синтаксис и пути:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir <SQL_DB_instance_folder>\R_SERVICES\library\MicrosoftML\mxLibs\x64`

    Например чтобы включить использование последней версии предварительно обученные модели для R в экземпляре по умолчанию 2017 г. SQL Server, запуске этой инструкции:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    Для именованного экземпляра команда будет выглядеть примерно следующим образом:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

  + Использование моделей с **PYTHON_SERVICES**, используйте следующий синтаксис и пути:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir <SQL_DB_instance_folder>\PYTHON_SERVICES\Lib\site-packages\microsoftml\mxLibs`

    Например позволяя использовать последнюю версию предварительно обученные модели для Python в экземпляре по умолчанию 2017 г. SQL Server, выполните эту инструкцию:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\microsoftml\mxLibs"`

    Для именованного экземпляра команда будет выглядеть примерно следующим образом:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\PYTHON_SERVICES\Lib\site-packages\microsoftml\mxLibs"`

5. Для параметра версии поддерживаются следующие значения:

    + Версия-кандидат 0: **9.1.0.0**
    + Версия-кандидат 1: **9.2.0.22**
    + RTM: **9.2.0.100**
    + Накопительное обновление 1: **9.2.0.24**

6. Если установка выполнена успешно, следующие модели должны быть добавлены в ваш R\_СЛУЖБ или PYTHON\_папок СЛУЖБ:

    - AlexNet\_Updated.model
    - ImageNet1K\_mean.xml
    - pretrained.Model
    - ResNet\_101\_Updated.model
    - ResNet\_18\_Updated.model
    - ResNet\_50\_Updated.model

## <a name="examples"></a>Примеры

После установки моделей можно использовать модели путем вызова из кода приложения.

### <a name="image-featurization-example"></a>Пример featurization изображения

Предварительно обученные модели для изображений поддерживает featurization изображений, которые предоставляются. Это модель была обучена с помощью [CNTK](https://docs.microsoft.com/cognitive-toolkit/). 

Чтобы использовать модель, вызовите **featurizeImage** преобразования.

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
> Это не возможность считывать или изменять предварительно обученные модели, так как они будут сжаты, использование собственного формата для повышения производительности.


### <a name="text-analysis-example"></a>Пример анализа текста

См. следующий пример показывает, как использовать модель featurization предварительно обученные текст для текстовой классификации:

[Анализ мнений, с помощью Featurizer текста](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

