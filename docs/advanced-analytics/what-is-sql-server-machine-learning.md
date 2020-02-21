---
title: Что такое службы машинного обучения SQL Server (Python и R)?
titleSuffix: ''
description: Службы машинного обучения — это компонент SQL Server, который дает возможность выполнять скрипты Python и R с реляционными данными. Вы можете использовать платформы и пакеты с открытым исходным кодом и пакеты Майкрософт Python и R для прогнозной аналитики и машинного обучения. Скрипты выполняются в базе данных без перемещения данных за пределы SQL Server или по сети. В этой статье объясняются основы Служб машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/07/2019
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fe7a83c66dba9af372e82fc2814828aae32d6a2d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75558293"
---
# <a name="what-is-sql-server-machine-learning-services-python-and-r"></a>Что такое службы машинного обучения SQL Server (Python и R)?
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Службы машинного обучения — это компонент SQL Server, который дает возможность выполнять скрипты Python и R с реляционными данными. Вы можете использовать платформы и пакеты с открытым исходным кодом и [пакеты Майкрософт Python и R](#packages) для прогнозной аналитики и машинного обучения. Скрипты выполняются в базе данных без перемещения данных за пределы SQL Server или по сети. В этой статье объясняются основы Служб машинного обучения SQL Server.

В Базе данных SQL Azure [Службы машинного обучения](https://docs.microsoft.com/azure/sql-database/sql-database-machine-learning-services-overview) предоставляются в общедоступной предварительной версии.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Сведения о запуске Java в SQL Server см. в [документации по расширениям языков](../language-extensions/language-extensions-overview.md).
::: moniker-end

## <a name="what-is-machine-learning-services"></a>Что такое Службы машинного обучения?

Службы машинного обучения SQL Server можно использовать для запуска скриптов R или Python в базе данных. С их помощью можно подготавливать и очищать данные, выполнять проектирование признаков, а также обучать, оценивать и развертывать модели машинного обучения в базе данных. Этот компонент выполняет скрипты там, где хранятся данные, и устраняет необходимость перемещения данных по сети на другой сервер.

Базовые распределения Python и R включены в Службы машинного обучения. Вы можете установить и использовать платформы и пакеты с открытым исходным кодом, такие как PyTorch, TensorFlow и scikit-learn, в дополнение к пакетам Microsoft [revoscalepy](python/ref-py-revoscalepy.md) и [microsoftml](python/ref-py-microsoftml.md) для Python и [RevoScaleR](r/ref-r-revoscaler.md), [MicrosoftML](r/ref-r-microsoftml.md), [OLAP](r/ref-r-olapr.md) и [sqlrutils](r/ref-r-sqlrutils.md) для R.

Службы машинного обучения используют платформу расширяемости для выполнения скриптов Python и R на SQL Server. Дополнительные сведения о том, как это работает:

+ [Платформа расширяемости](concepts/extensibility-framework.md)
+ [Расширение Python](concepts/extension-python.md)
+ [Расширение R](concepts/extension-r.md)

## <a name="what-can-i-do-with-machine-learning-services"></a>Что можно сделать с помощью Служб машинного обучения?

Службы машинного обучения можно использовать для создания и обучения моделей машинного обучения и глубокого обучения в SQL Server. Можно также развернуть существующие модели в Службах машинного обучения и использовать реляционные данные для прогнозов.

Примеры типов прогнозирования, для которых можно использовать Службы машинного обучения SQL Server:

|||
|-|-|
|Классификация и категоризация|Автоматическое разделение отзывов клиентов на положительные и отрицательные|
|Регрессия/прогнозирование непрерывных значений|Прогнозирование стоимости домов на основе размера и расположения|
|Обнаружение аномалий|Обнаружение мошеннических банковских транзакций |
|Рекомендации|Предложение продуктов, которые могут понравиться покупателям Интернет-магазина, на основе их предыдущих покупок|

### <a name="how-to-execute-python-and-r-scripts"></a>Выполнение скриптов Python и R

Существует два способа выполнения скриптов Python и R в Службах машинного обучения:

+ Наиболее распространенным способом является использование хранимой процедуры T-SQL [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Вы также можете использовать предпочтительный клиент Python или R и написать скрипты, которые принудительно отправляют выполнение (так называемый *удаленный контекст вычислений*) на удаленный SQL Server. Дополнительные сведения о настройке обработки и анализа данных см. в статьях [Разработки на Python](python/setup-python-client-tools-sql.md) и [Разработки на R](r/set-up-a-data-science-client.md).

<a name="packages"></a>

## <a name="python-and-r-packages"></a>Пакеты Python и R

В дополнение к корпоративным пакетам Майкрософт можно использовать платформы и пакеты с открытым кодом. Наиболее распространенные пакеты Python и R с открытым кодом предварительно установлены в Службах машинного обучения. Также включены следующие пакеты Python и R от Майкрософт:

| Язык | Пакет | Описание |
|-|-|-|
| Python | [revoscalepy](python/ref-py-revoscalepy.md) | Основной пакет для масштабируемого Python. Преобразования и обработка данных, статистическая сводка, визуализация и многие виды моделирования. Кроме того, функции в этом пакете автоматически распределяют рабочие нагрузки между доступными ядрами для параллельной обработки. |
| Python | [microsoftml](python/ref-py-microsoftml.md) | Добавляет алгоритмы машинного обучения для создания пользовательских моделей для анализа текста, анализа изображений и анализа тональности. | 
| R | [RevoScaleR](r/ref-r-revoscaler.md) | Основной пакет для масштабируемого R. Преобразования и обработка данных, статистическая сводка, визуализация и многие виды моделирования. Кроме того, функции в этом пакете автоматически распределяют рабочие нагрузки между доступными ядрами для параллельной обработки. |
| R | [MicrosoftML (R)](r/ref-r-microsoftml.md) | Добавляет алгоритмы машинного обучения для создания пользовательских моделей для анализа текста, анализа изображений и анализа тональности. |
| R | [olapR](r/ref-r-olapr.md) | Функции R, используемые для запросов многомерных выражений к кубу OLAP SQL Server Analysis Services. |
| R | [sqlrutils](r/ref-r-sqlrutils.md) | Механизм для использования скриптов R в хранимой процедуре T-SQL, регистрации этой хранимой процедуры в базе данных и ее запуска из [среды разработки R](r/set-up-a-data-science-client.md). |
| R | [Microsoft R Open](https://mran.microsoft.com/rro) | Microsoft R Open (MRO) — это улучшенная версия R от Майкрософт. Это полная платформа с открытым кодом для статистического анализа и обработки и анализа данных. Она основана на R, полностью совместима с ним и включает дополнительные возможности для повышения производительности и воспроизводимости. |

Дополнительные сведения о том, какие пакеты устанавливаются со Службами машинного обучения и как устанавливать другие пакеты, см. в следующих статьях:

+ [Получение сведений о пакете Python](package-management/python-package-information.md)
+ [Установка пакетов Python с помощью sqlmlutils](package-management/install-additional-python-packages-on-sql-server.md)
+ [Получение сведений о пакете R](package-management/r-package-information.md)
+ [Установка новых пакетов R с помощью sqlmlutils](package-management/install-additional-r-packages-on-sql-server.md)

## <a name="how-do-i-get-started-with-machine-learning-services"></a>Как начать работу со Службами машинного обучения?

1. [Установка служб машинного обучения SQL Server](install/sql-machine-learning-services-windows-install.md)

1. Настройте средства разработки. Вы можете использовать:

    + [Azure Data Studio](../azure-data-studio/what-is.md) или [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md) для использования T-SQL и хранимой процедуры [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), чтобы выполнить скрипт Python или R.
    + Python или R на собственном ноутбуке или рабочей станции разработки для выполнения скриптов. Можно либо извлечь данные локально, либо отправить выполнение удаленно в SQL Server с помощью [revoscalepy](python/ref-py-revoscalepy.md) и [RevoScaleR](r/ref-r-revoscaler.md). Дополнительные сведения о настройке обработки и анализа данных см. в статьях [Разработки на Python](python/setup-python-client-tools-sql.md) и [Разработки на R](r/set-up-a-data-science-client.md).

1. Написание первого скрипта Python или R

    + Краткое руководство. [Создание и выполнение простых скриптов R в SQL](tutorials/quickstart-r-create-script.md)
    + Краткое руководство. [Создание и обучение модели прогнозирования на R](tutorials/quickstart-r-train-score-model.md)
    + Руководство. [Запуск Python в T-SQL](tutorials/sqldev-in-database-python-for-sql-developers.md). Просмотр данных, разработка признаков, обучение и развертывание моделей, создание прогнозов (серия из пяти частей)
    + Руководство. [Использование R в T-SQL](tutorials/sqldev-in-database-r-for-sql-developers.md). Просмотр данных, разработка признаков, обучение и развертывание моделей, создание прогнозов (серия из пяти частей)
    + Руководство. [Использование Служб машинного обучения в средствах R](tutorials/walkthrough-data-science-end-to-end-walkthrough.md): Просмотр данных, создание графов и графиков, разработка признаков, обучение и развертывание моделей, создание прогнозов (серии из шести частей)

## <a name="next-steps"></a>Дальнейшие действия

+ [Установка служб машинного обучения SQL Server](install/sql-machine-learning-services-windows-install.md)
+ Настройка клиента обработки и анализа данных для [разработки на Python](python/setup-python-client-tools-sql.md) и [разработки на R](r/set-up-a-data-science-client.md)
