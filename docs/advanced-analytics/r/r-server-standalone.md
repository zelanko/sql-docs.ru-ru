---
title: SQL Server Machine Learning Server (изолированную версию) и R Server (изолированный) | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a8cdceabc26c55b6eade57712fa610d3e84808f5
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174791"
---
# <a name="sql-server-machine-learning-server-standalone-and-r-server-standalone"></a>SQL Server Machine Learning Server (изолированную версию) и R Server (изолированный)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Изолированный сервер — это установка компонентов машинного обучения, определена как компоненты R и Python, которые работать независимо от экземпляров компонента SQL Server database engine. Можно установить изолированный сервер самостоятельно, без зависимостей на сервере SQL Server. Так как изолированный сервер не зависит от SQL Server, настройки и администрирования и средства больше похожи на версию сервера машинного обучения, в котором можно узнать в отличных от SQL [в этой статье](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server).

Цель машины обучения изолированного сервера — среду разработки, с распределенной и параллельной обработки рабочих нагрузок R и Python для малых и крупных наборов данных, используя частные пакеты и модули расчета установить на сервере. Пакеты R и Python на изолированном сервере совпадают, которые описаны в экземпляр SQL Server (в базе данных), что обеспечивает переносимость кода и [переключение контекста вычислений](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).

Основная причина разработчики предпочли машины обучения изолированного сервера — за ограничения памяти и обработки открытым исходным кодом R и Python. Изолированные серверы можно загрузить и обработки больших объемов данных на нескольких ядрах и статистическая обработка результатов в виде одного объединенного вывода. Функции и алгоритмы предназначены для масштабирования и служебной программы: прогнозной аналитики, статистического моделирования, визуализации данных и передовых алгоритмов машинного обучения в коммерческих серверного продукта разработаны и поддерживаемых Корпорация Майкрософт.

Как правило, мы рекомендуем обрабатывать (изолированный) и (в базе данных) установок как взаимно монопольного, чтобы избежать конфликта ресурсов, но если у вас есть достаточно ресурсов имеется не запрет на их установку на одном физическом компьютере.

На компьютере может иметь только один изолированный сервер: либо [сервера SQL Server 2017 машинного обучения (изолированного)](../install/sql-machine-learning-standalone-windows-install.md) или [SQL Server 2016 R Server (изолированный)](../install/sql-r-standalone-windows-install.md). Перед установкой другой версии, необходимо вручную удалить одной версии.

## <a name="components-of-a-standalone-server"></a>Компоненты автономного сервера

SQL Server 2016 — R только. SQL Server 2017 поддерживает R и Python. Ниже перечислены функции, в каждой версии.

| Компонент | Описание |
|-----------|-------------|
| Пакеты R | [RevoScaleR](revoscaler-overview.md) является основной библиотекой для масштабируемый R с функциями для преобразования, visualzation, анализа и обработки данных.  <br/>[MicrosoftML (R)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) добавляет алгоритмов машинного обучения для создания пользовательских моделей для анализа текста, анализ образов и анализ тональности. <br/>[mrsdeploy](operationalization-with-mrsdeploy.md) предложения веб-развертывание службы (в SQL Server 2017 г. только). <br/>[olapR](how-to-create-mdx-queries-using-olapr.md) предназначен для указания запросов многомерных Выражений в R.|
| Microsoft R Open (MRO) | [MRO](https://mran.microsoft.com/open) является открытым исходным кодом корпорации Майкрософт распределение R. Включены пакета и интерпретатор. Всегда используйте версию MRO, объединенными в программе установки. |
| Инструменты R | Окнах консоли R и Командная строка, стандартные средства в дистрибутив R. Найти их на \Program files\Microsoft SQL Server\140\R_SERVER\bin\x64. |
| R Примеры и сценарии |  Пакеты с открытым исходным кодом R и RevoScaleR описан встроенных наборов данных, что можно создать и запустить сценарий с помощью предварительно установленных данных. Их можно найти в \Program files\Microsoft SQL Server\140\R_SERVER\library\datasets и \library\RevoScaleR. |
| Пакеты Python | [revoscalepy](../python/what-is-revoscalepy.md) является основной библиотекой для масштабируемый Python с помощью функций для преобразования, visualzation, анализа и обработки данных. <br/>[microsoftml (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) добавляет алгоритмов машинного обучения для создания пользовательских моделей для анализа текста, анализ образов и анализ тональности.  |
| Инструменты Python | Встроенное средство командной строки Python полезен для нерегламентированной отладки и задачи. Найти средство в \Program files\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda — дистрибутив открытым исходным кодом Python и основных пакетов. |
| Примеры Python и сценарии | С помощью R, Python, содержит встроенные наборы данных и сценарии. Найти данные revoscalepy в \Program files\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-packages\revoscalepy\data\sample-data. |
| Предварительно обученных моделей R и Python | Предварительно обученных моделей поддерживается и может использоваться на изолированном сервере, но их нельзя установить через программу установки SQL Server. Программа установки сервера машинного обучения Майкрософт предоставляет моделей, которые можно установить бесплатно. Дополнительные сведения см. в разделе [Install обученная моделей машинного обучения на сервере SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="get-started-step-by-step"></a>Начало работы пошаговые

Начните с установки, присоединить двоичные файлы привычного средства разработки и написанию первого скрипта.

### <a name="step-1-install-the-software"></a>Шаг 1: Установка программного обеспечения

Установите одну из этих версий:

+ [Сервер SQL Server 2017 машинного обучения (автономный)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Server (изолированный) — только для чтения](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>Шаг 2: Настройка средство разработки

Настройка средств разработки для использования двоичных файлов сервера машинного обучения. Дополнительные сведения о Python см. в разделе [двоичные файлы Python ссылку](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools). Инструкции по подключению в R Studio, см. в разделе [с помощью разных версий R](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R) и указать средству C:\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64. Вы также можете попробовать [инструменты R для Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation). 

### <a name="step-3-write-your-first-script"></a>Шаг 3: Создайте первый сценарий

Написать сценарий R или Python, с помощью функций RevoScaleR и revoscalepy, алгоритмов машинного обучения.
  
  + [Explore R and Обзор RevoScaleR в 25 функциях](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): Начните с основных команд R, затем хода выполнения работ по RevoScaleR распространяемых аналитических функций, которые обеспечивают высокую производительность и масштабирование решений r. Она содержит параллелизуемые версии многих популярных пакетов моделирования для R, например кластеризацию методом К-средних, деревья и леса принятия решений, а также средства для работы с данными.

  + [Краткое руководство: Пример двоичной классификации с помощью пакета Python microsoftml](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml): Создание модели двоичной классификации с помощью функций из microsoftml и рака молочной хорошо известного набора данных.

Выберите наилучший язык, для задачи. R — это наилучшим образом подходит для статистических вычислений, которые трудно реализовать с помощью SQL. Для операций на основе набора данных, воспользуйтесь преимуществами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для достижения максимальной производительности. Используйте ядро базы данных в памяти для очень быстро вычислений по столбцам.

### <a name="step-4-operationalize-your-solution"></a>Шаг 4: Ввод в эксплуатацию решения

Можно использовать автономные серверы [ввода в эксплуатацию](https://docs.microsoft.com//machine-learning-server/what-is-operationalization) функциональных возможностей без SQL-фирменной символики [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server). Можно настроить изолированный сервер для ввода в эксплуатацию, который предоставляет следующие возможности: развернуть и разместить код, как веб-службы, выполните диагностику, тестовая емкость службы web.

## <a name="see-also"></a>См. также

 [SQL Server службы машинного обучения (в базе данных)](sql-server-r-services.md)

