---
title: Документация по расширениям машинного обучения и программирования на R и Python — Машинное обучение SQL Server
description: R и Python в SQL Server со встроенными моделями обработки и анализа данных и алгоритмами машинного обучения, используемыми для масштабного анализа корпоративных данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/09/2019
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 7eb5083f17ab08f19b689b3550f979f88495f604
ms.sourcegitcommit: 1f53b6a536ccffd701fc87e658ddac714f6da7a2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2019
ms.locfileid: "54206250"
---
# <a name="sql-server-machine-learning"></a>Службы машинного обучения SQL Server

::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"

## <a name="sql-server-machine-learning-and-programming-extensions-documentation"></a>Документация по программным модулям и службе машинного обучения SQL Server

Узнайте, как использовать внешние библиотеки и языки R и Python для резидентных реляционных данных, ознакомившись с краткими руководствами и статьями с инструкциями. Библиотеки R и Python в [службе машинного обучения SQL Server](what-is-sql-server-machine-learning.md) включают: базовые распределения, модели обработки и анализа данных, алгоритмы машинного обучения и функции для выполнения масштабной высокопроизводительной аналитики без необходимости передачи данных по сети. 

В SQL Server 2019 для выполнения кода Java используется та же платформа расширяемости, что для R и Python, но не требуются библиотеки функций для обработки и анализа данных и машинного обучения. Дополнительные сведения о новых возможностях в службах машинного обучения SQL Server см. в [этой статье](what-s-new-in-sql-server-machine-learning-services.md).

|   |   | 
|---|---|-
| ![Логотип R](./media/index/logo_r.png) | R с открытым кодом расширен с помощью [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) и алгоритмов ИИ Майкрософт в [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package). Эти библиотеки предоставляют модели прогнозирования, статистический анализ, визуализацию и масштабную обработку данных. <br/>Интеграция R поддерживается в [SQL Server 2016](./install/sql-r-services-windows-install.md), а также в [SQL Server 2017](./install/sql-machine-learning-services-windows-install.md). | 
| ![Логотип Python](./media/index/logo_python.png) | Для прогнозной аналитики и машинного обучения в масштабе разработчики Python могут использовать библиотеки Майкрософт [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) и [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package). Библиотеки, совместимые с Anaconda и Python 3.5, являются базовым распределением. <br/>Интеграция Python поддерживается в [SQL Server 2017](./install/sql-machine-learning-services-windows-install.md).  | 
| ![Логотип Java](./media/index/logo_java.png) | Чтобы поместить код в хранимые процедуры или в двоичный формат, доступный через Transact-SQL, разработчики Java могут использовать [расширение языка Java](java/extension-java.md). <br/>Интеграция Java поддерживается в [предварительной версии SQL Server 2019](./install/sql-machine-learning-services-ver15.md). |
::: moniker-end

::: moniker range="=sql-server-2016||=sql-server-2017"

## <a name="sql-server-machine-learning-r-and-python-documentation"></a>Документация по использованию R и Python в службе машинного обучения SQL Server

Узнайте, как использовать внешние библиотеки и языки R и Python для резидентных реляционных данных, ознакомившись с краткими руководствами и статьями с инструкциями. Библиотеки R и Python в [службе машинного обучения SQL Server](what-is-sql-server-machine-learning.md) включают: базовые распределения, модели обработки и анализа данных, алгоритмы машинного обучения и функции для выполнения масштабной высокопроизводительной аналитики без необходимости передачи данных по сети. 

|   |   | 
|---|---|-
| ![Логотип R](./media/index/logo_r.png) | R с открытым кодом расширен с помощью [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) и алгоритмов ИИ Майкрософт в [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package). Эти библиотеки предоставляют модели прогнозирования, статистический анализ, визуализацию и масштабную обработку данных. <br/>Интеграция R поддерживается в [SQL Server 2016](./install/sql-r-services-windows-install.md), а также в [SQL Server 2017](./install/sql-machine-learning-services-windows-install.md). | 
| ![Логотип Python](./media/index/logo_python.png) | Для прогнозной аналитики и машинного обучения в масштабе разработчики Python могут использовать библиотеки Майкрософт [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) и [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package). Библиотеки, совместимые с Anaconda и Python 3.5, являются базовым распределением. <br/>Интеграция Python поддерживается в [SQL Server 2017](./install/sql-machine-learning-services-windows-install.md).  | 
::: moniker-end

## <a name="5-minute-quickstarts"></a>Пятиминутные краткие руководства

+ [Руководство по созданию модели прогнозирования на R](./tutorials/rtsql-create-a-predictive-model-r.md)

+ [Руководство по получению прогнозов с помощью модели и построение графика с результатами, используя R](./tutorials/rtsql-predict-and-plot-from-model.md)


## <a name="step-by-step-tutorials"></a>Пошаговые руководства

+ [Руководство по добавлению платформы расширяемости и машинного обучения в SQL Server](install/sql-machine-learning-services-windows-install.md)

+ [Руководство по выполнению R из T-SQL и хранимых процедур](./tutorials/sqldev-in-database-r-for-sql-developers.md)

+ [Руководство по использованию встроенной аналитики в Python](./tutorials/sqldev-in-database-python-for-sql-developers.md)


## <a name="video-introduction"></a>Ознакомительное видео

> [!VIDEO https://www.youtube.com/embed/ACejZ9optCQ]

## <a name="reference"></a>Справочник

| Пакет | Язык | Описание | 
|---------|----------|-------------|
| [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | Чтение | Распределенная и параллельная обработка для задач R: преобразование данных, исследование, визуализация, статистическая и прогнозная аналитика. |
| [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | Чтение | Функции, основанные на алгоритмах ИИ Майкрософт, адаптированные для R. |
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | Чтение | Импорт данных из куба OLAP. |
| [sqlRUtils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | Чтение | Вспомогательные функции для инкапсуляции R и T-SQL. |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Python | Распределенная и параллельная обработка задач Python: преобразование данных, исследование, визуализация, статистическая и прогнозная аналитика.  | 
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Python | Функции, основанные на алгоритмах ИИ Майкрософт, адаптированные для Python.  |