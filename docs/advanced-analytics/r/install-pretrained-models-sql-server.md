---
title: "Установка моделей предварительно обученные машинного обучения в SQL Server | Документы Microsoft"
ms.date: 11/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 46f8039a6c3ec6f592d2516463f802bda81249f1
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="install-pretrained-machine-learning-models-on-sql-server"></a>Установить предварительно обученные машинного обучения моделей, основанных на SQL Server

В этой статье описывает, как добавлять предварительно обученные модели на экземпляре SQL Server, уже имеет служб R или машины обучения службы установлены.

Возможность установки предварительно обученные модели доступен при использовании отдельного установщика Windows для Microsoft R Server или машины обучения. Для получения только предварительно обученные модели можно использовать этот установщик, или можно использовать его для [обновление машинного обучения компонентов](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md) в экземпляре SQL Server 2016 или 2017 г. SQL Server.

После загрузки предварительно обученные модели с помощью программы установки, существуют некоторые дополнительные действия по настройке моделей для использования с SQL Server. В этой статье описан процесс.

Пример использования предварительно обученные модели с данными SQL Server см. в записи командой SQL Server машинного обучения: 

+ [Анализ мнений с Python в службах SQL Server машины обучения](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/11/01/sentiment-analysis-with-python-in-sql-server-machine-learning-services/)

## <a name="benefits-of-using-pretrained-models"></a>Преимущества использования предварительно обученные модели

Эти предварительно обученной модели были созданы для помощи клиентам, которым требуется для выполнения задач, таких как featurization мнений анализа или изображения, но не обладают ресурсы для получения больших наборов данных или обучения сложные модели. С помощью предварительно обученной модели позволяет приступить к работе над текста и эффективной обработки изображений.

В настоящее время модели, которые доступны являются моделями глубокие нейронные сети (DNN) для анализа и изображение классификация мнений. Все предварительно обученные модели прошли обучение с помощью корпорации Майкрософт [Toolkit сети вычисление](https://cntk.ai/Features/Index.html), или **CNTK**.

Конфигурации всех сетей, был основан на следующих справочных реализаций:

+ ResNet 18
+ ResNet 50
+ ResNet 101
+ AlexNet

Дополнительные сведения об этих моделях см. в разделе [предварительно обученной моделей машинного обучения для анализа и образа обнаружения мнений](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)

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

    + Если ранее вы установили машины Server обучения и обновленные компоненты R или Python, с помощью параметра привязки, оставьте все ранее выбранные варианты **как**и выберите параметры предварительно обученные модели. Не отменяйте Выбор все выбранные ранее параметры; Если это сделать, программа установки удаляет компоненты.

3. После завершения установки откройте командную строку Windows **администратор**и перейдите к папке установки начальной загрузки для SQL Server, который также содержит установщик Microsoft R. Папка в экземпляре по умолчанию 2017 г. SQL Server, будет:
    
    `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\SQL2017\x64\`

4. Запустите RSetup.exe и указать компонент для установки, версии и к папке, содержащей исходные файлы модели, с помощью командной строки показано в следующих примерах:

    + Использование моделей с **R_SERVICES**:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<SQL_DB_instance_folder>\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    Например чтобы включить использование последней версии предварительно обученные модели для R в экземпляре по умолчанию 2017 г. SQL Server, запуске этой инструкции:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    Для именованного экземпляра команда будет выглядеть примерно следующим образом:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    + Для использования предварительно обученные модели R Server (изолированный) или машины обучения Server (изолированный):

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "~\R_SERVER\library\MicrosoftML\mxLibs\x64"`

    Например чтобы включить использование последней версии предварительно обученные модели для R, при установке по умолчанию сервера R с SQL Server 2016 запуске этой инструкции:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir ‘C:\Program Files\Microsoft SQL Server\130\R_SERVER\library\MicrosoftML\mxLibs\"`
    
    + Чтобы использовать предварительно обученные модели с **PYTHON_SERVICES**:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<SQL_DB_instance_folder>\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    Например позволяя использовать последнюю версию предварительно обученные модели для Python в экземпляре по умолчанию 2017 г. SQL Server, выполните эту инструкцию:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    Для именованного экземпляра команда будет выглядеть примерно следующим образом:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    + Чтобы использовать Python обученная моделей с машины обучения Server (изолированный):

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<sql_folder>\PYTHON_SERVER\site-packages\microsoftml\mxLibs"`

    Например при условии, что установки по умолчанию машины обучения Server (автономный) с помощью программы установки SQL Server 2017 г., выполните следующую инструкцию:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER\Lib\site-packages\microsoftml\mxLibs"`

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


> [!NOTE]
> 
> Если слишком длинный путь к файлу модели, может возникнуть ошибка при вызове файла модели из кода Python. Это связано с ограничением в текущей реализации Python. Эта проблема будет исправлена в будущих исправлений.

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
