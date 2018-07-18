---
title: Обучение компьютера сервера SQL Server (автономный) и R Server (изолированный) | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2c416049692f8860e4ba608e58f401ce527b135c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203046"
---
# <a name="sql-server-machine-learning-server-standalone-and-r-server-standalone"></a>Обучение компьютера сервера SQL Server (автономный) и R Server (изолированный)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Изолированный сервер представляет собой установку компонентов машины обучения, выражаются как компоненты R и Python, которые работать независимо от экземпляров компонента SQL Server database engine. Можно установить автономный сервер самостоятельно, без зависимостей на сервере SQL Server. Так как автономный сервер не зависит от SQL Server, настройки и администрирования и инструменты аналогичны более версии отличные от SQL Server обучения машины, которой можно ознакомиться в [в этой статье](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server).

Цель машины обучения изолированного сервера — для предоставления богатой средой разработки, распределенных и параллельной обработки рабочих нагрузок R и Python малых и крупных наборов данных, использование собственных пакетов и модулей вычисления устанавливается вместе с сервера. Пакеты R и Python на изолированном сервере имеют такие же, как указано в установке SQL Server (в базе данных), позволяя переносимость кода и [переключение контекста вычислений](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).

Основная причина разработчики выберите автономный сервер обучения машины заключается в перемещении за ресурсы памяти и процессора ограничения открытым исходным кодом R и Python. Автономные серверы можно загрузить и обработки больших объемов данных на нескольких ядер и собрать результаты в один выходной объединенный. Функции и алгоритмы предназначены для масштабирования и полезности: прогнозирующей аналитики, статистическое моделирование и визуализации данных и современных алгоритмов машинного обучения в коммерческих серверного продукта разработан и поддерживается Корпорация Майкрософт.

Как правило, мы рекомендуется обрабатывать (автономный) и (в базе данных) установок как взаимно монопольного во избежание конфликтов ресурсов, но если имеется достаточно ресурсов имеется не запрет на их установку на одном физическом компьютере.

На компьютере может иметь только один изолированный сервер: либо [обучения машины 2017 г сервера SQL Server (автономный)](../install/sql-machine-learning-standalone-windows-install.md) или [SQL Server 2016 R Server (изолированный)](../install/sql-r-standalone-windows-install.md). Необходимо вручную удалить одной версии перед установкой на другую версию.

## <a name="components-of-a-standalone-server"></a>Компоненты изолированного сервера

SQL Server 2016 — R только. SQL Server 2017 поддерживает R и Python. Ниже перечислены компоненты, в каждой версии.

| Компонент | Описание |
|-----------|-------------|
| R-пакеты | [RevoScaleR](revoscaler-overview.md) является первичная библиотека для масштабируемый R с помощью функций для обработки данных, преобразования, visualzation и анализа.  <br/>[MicrosoftML (R)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) добавляет алгоритмов машинного обучения для создания пользовательских моделей для анализа текста, анализ образов и анализ мнений. <br/>[mrsdeploy](operationalization-with-mrsdeploy.md) предложений веб-развертывания службы (в SQL Server 2017 г. только). <br/>[olapR](how-to-create-mdx-queries-using-olapr.md) предназначен для указания запросов многомерных Выражений в R.|
| Microsoft R Open (MRO) | [MRO](https://mran.microsoft.com/open) является открытым исходным кодом корпорации Майкрософт распределение R. Пакет и интерпретатор включены. Всегда используйте версию MRO, объединенными в программе установки. |
| Средства R | Windows консоль R и командные строки являются стандартные средства в R распространения. Найти их в \Program files\Microsoft SQL Server\140\R_SERVER\bin\x64. |
| R-Примеры и сценарии |  Пакеты с открытым исходным кодом R и RevoScaleR включают встроенные наборы данных, можно создать и запустить скрипт, используя предварительно установленные данные. Их можно найти на \Program files\Microsoft SQL Server\140\R_SERVER\library\datasets и \library\RevoScaleR. |
| Пакеты Python | [revoscalepy](../python/what-is-revoscalepy.md) является первичная библиотека для масштабируемый Python с помощью функций для обработки данных, преобразования, visualzation и анализа. <br/>[microsoftml (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) добавляет алгоритмов машинного обучения для создания пользовательских моделей для анализа текста, анализ образов и анализ мнений.  |
| Средства Python | Встроенные средства командной строки Python полезен для нерегламентированной проверки и задачи. Найдите инструмент в \Program files\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda — распределение открытым исходным кодом, Python и основные пакеты. |
| Python примеры и сценарии | С помощью R, Python включает встроенные наборы данных и сценариев. Найти данные revoscalepy в \Program files\Microsoft SQL Server\140\PYTHON_SERVER\lib\site packages\revoscalepy\data\sample данных. |
| Предварительно обученный моделей в R и Python | Предварительно обученной модели являются поддерживается и может использоваться на отдельном сервере, но их нельзя установить через программу установки SQL Server. Программа установки Microsoft Server обучения машины предоставляет моделей, которые можно установить бесплатно. Дополнительные сведения см. в разделе [установки обученная моделей машинного обучения на сервере SQL Server](install-pretrained-models-sql-server.md). |

## <a name="get-started-step-by-step"></a>Приступая к работе пошаговые

Запуск программы установки, присоединение двоичные файлы для вашего другого средства разработки и создайте первый сценарий.

### <a name="step-1-install-the-software"></a>Шаг 1: Установка программного обеспечения

Установите одну из этих версий.

+ [Обучения машины 2017 г сервера SQL Server (автономный)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Server (изолированный) — только для чтения](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>Шаг 2: Настройка средство разработки

Настройка средств разработки для использования двоичные файлы сервера обучения машины. Дополнительные сведения о Python см. в разделе [двоичные файлы Python ссылку](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools). Инструкции по подключению в R Studio см. в разделе [с помощью другой версии R](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R) и указать средству C:\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64. Вы также можете попробовать [средства R для Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation). 

### <a name="step-3-write-your-first-script"></a>Шаг 3: Создайте первый сценарий

Написать скрипт R или Python, с помощью функции RevoScaleR, revoscalepy и алгоритмов машинного обучения.
  
  + [Изучите R и RevoScaleR в 25 функции](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): основные команды R, затем хода выполнения работ по RevoScaleR распространяемый аналитические функции, которые обеспечивают высокую производительность и масштабирование решения R, начинающихся. Она содержит параллелизуемые версии многих популярных пакетов моделирования для R, например кластеризацию методом К-средних, деревья и леса принятия решений, а также средства для работы с данными.

  + [Краткое руководство: Пример двоичной классификации с помощью пакета Python microsoftml](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml): Создание модели двоичной классификации с помощью функций из microsoftml и рак груди хорошо известного набора данных.

Выберите лучший язык для задачи. R лучше всего подходит для статистических вычислений, которые трудно реализовать с помощью SQL. Для операций на основе набора данных, использовать возможности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для достижения максимальной производительности. Используете ядро базы данных в памяти для быстрого вычислений над столбцами.

### <a name="step-4-operationalize-your-solution"></a>Шаг 4: Ввода в эксплуатацию решения

Автономные серверы можно использовать [ввода в эксплуатацию](https://docs.microsoft.com//machine-learning-server/what-is-operationalization) функциональные возможности не SQL-символикой [Microsoft Server обучения машины](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server). Можно настроить изолированном сервере для ввода в эксплуатацию, что дает следующие преимущества: развертывание и размещения кода как веб-службы, запустите программу диагностики, тест емкости веб-службы.

## <a name="see-also"></a>См. также:

 [Изучение служб (в базе данных) машины SQL Server](sql-server-r-services.md)

