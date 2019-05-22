---
title: 'R и Python в машинном обучении документация: службы SQL Server машинного обучения'
description: R и Python в SQL Server со встроенными моделями обработки и анализа данных и алгоритмами машинного обучения, используемыми для масштабного анализа корпоративных данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/22/2019
ms.topic: overview
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: e93d9ad5fd6415b6d8c1b6208857e81d60de2bd0
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65994129"
---
# <a name="sql-server-machine-learning-services"></a>Изучение служб машины SQL Server

## <a name="sql-server-machine-learning-services-r-and-python-documentation"></a>SQL Server в машинном обучении документации по службам (R и Python)

Узнайте, как использовать внешние библиотеки и языки R и Python для резидентных реляционных данных, ознакомившись с краткими руководствами и статьями с инструкциями. Библиотеки R и Python в [службе машинного обучения SQL Server](what-is-sql-server-machine-learning.md) включают: базовые распределения, модели обработки и анализа данных, алгоритмы машинного обучения и функции для выполнения масштабной высокопроизводительной аналитики без необходимости передачи данных по сети.

::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Документацию по Java, см. в разделе [документации расширения языка SQL Server](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview).
::: moniker-end

|   |   |
|---|:--|
| ![Логотип R](media/index/logo_r.png) | R с открытым кодом расширен с помощью [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) и алгоритмов ИИ Майкрософт в [MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package). Эти библиотеки предоставляют модели прогнозирования, статистический анализ, визуализацию и масштабную обработку данных.<br/>Интеграция R поддерживается в [SQL Server 2016](install/sql-r-services-windows-install.md), а также в [SQL Server 2017](install/sql-machine-learning-services-windows-install.md). |
| ![Логотип Python](media/index/logo_python.png) | Для прогнозной аналитики и машинного обучения в масштабе разработчики Python могут использовать библиотеки Майкрософт [revoscalepy](/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) и [microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package). Библиотеки, совместимые с Anaconda и Python 3.5, являются базовым распределением.<br/>Интеграция Python поддерживается в [SQL Server 2017](install/sql-machine-learning-services-windows-install.md). |
| &nbsp; | &nbsp; |

## <a name="5-minute-quickstarts"></a>Пятиминутные краткие руководства

- [Руководство по созданию модели прогнозирования на R](tutorials/rtsql-create-a-predictive-model-r.md)

- [Руководство по получению прогнозов с помощью модели и построение графика с результатами, используя R](tutorials/rtsql-predict-and-plot-from-model.md)

## <a name="step-by-step-tutorials"></a>Пошаговые руководства

- [Руководство по добавлению платформы расширяемости и машинного обучения в SQL Server](install/sql-machine-learning-services-windows-install.md)

- [Руководство по выполнению R из T-SQL и хранимых процедур](tutorials/sqldev-in-database-r-for-sql-developers.md)

- [Руководство по использованию встроенной аналитики в Python](tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="video-introduction"></a>Ознакомительное видео

> [!VIDEO https://www.youtube.com/embed/ACejZ9optCQ]

## <a name="reference"></a>Ссылка

| Пакет | Язык | Описание |
|:--------|:---------|:------------|
| [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) | Чтение | Распределенная и параллельная обработка для задач R: преобразование данных, исследование, визуализация, статистическая и прогнозная аналитика. |
| [MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package) | Чтение | Функции, основанные на алгоритмах ИИ Майкрософт, адаптированные для R. |
| [olapR](/machine-learning-server/r-reference/olapr/olapr) | Чтение | Импорт данных из куба OLAP. |
| [sqlRUtils](/machine-learning-server/r-reference/sqlrutils/sqlrutils) | Чтение | Вспомогательные функции для инкапсуляции R и T-SQL. |
[revoscalepy](/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Python | Распределенная и параллельная обработка задач Python: преобразование данных, исследование, визуализация, статистическая и прогнозная аналитика. |
| [microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Python | Функции, основанные на алгоритмах ИИ Майкрософт, адаптированные для Python. |
| &nbsp; | &nbsp; | &nbsp; |
