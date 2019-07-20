---
title: SQL Server 2017. Обзор учебника по Python
description: Введение в учебники по Python для аналитики в базе данных SQL Server 2017.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 86c5eaa600da0dbe9106278dd36b21eba322e2b7
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345963"
---
# <a name="sql-server-2017-python-tutorials"></a>Руководства по Python для SQL Server 2017
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описываются учебники по Python для аналитики в базе данных на [SQL Server 2017 службы машинного обучения](../install/sql-machine-learning-services-windows-install.md). 

+ Сведения о переносе и выполнении кода Python в хранимых процедурах.
+ Сериализация и сохранение моделей на основе Python для SQL Server баз данных.
+ Сведения об удаленных и локальных контекстах вычислений, а когда их следует использовать.
+ Изучите модули Microsoft Python для задач обработки и анализа данных и машинного обучения.

<a name="bkmk_pythontutorials"></a>

## <a name="python-quickstarts-and-tutorials"></a>Краткие руководства и учебники по Python

| Ссылка | Описание |
|------|-------------|
| [QuickStart Сценарий Python "Hello World" в SQL Server](quickstart-python-run-using-t-sql.md) | Изучите основы вызова Python в T-SQL. |
| [QuickStart Создание, обучение и использование модели Python с хранимыми процедурами в SQL Server](quickstart-python-train-score-in-tsql.md) | Описывает механизм внедрения кода Python в хранимую процедуру, предоставляя входные данные и выполнение хранимой процедуры. |
| [Учебник. Создание модели с помощью revoscalepy](use-python-revoscalepy-to-create-model.md) | Демонстрирует запуск кода из удаленного терминала Python с помощью SQL Server контекста вычислений. Вы должны быть несколько знакомы со средствами и средами Python. Приведен пример кода, который создает модель с помощью **rxLinMod**из новой библиотеки **revoscalepy** . |
| [Учебник. Изучение в базе данных аналитики Python для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md) | В этом сквозном пошаговом руководстве демонстрируется процесс создания полного решения Python с помощью хранимых процедур T-SQL. Весь код Python включен.|

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Примеры кода

Эти примеры и демонстрационные версии, предоставляемые командой разработчиков SQL Server, выделяют способы использования внедренной аналитики в реальных приложениях.

| Ссылка | Описание |
|------|-------------|
| [Создание прогнозной модели с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Узнайте, как компания Ski Аренда может использовать машинное обучение для предсказания будущих напрокат, что помогает бизнес-плану и персоналу соответствовать будущим потребностям. |
| [Выполнение кластеризации клиентов с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Узнайте, как использовать алгоритм Кмеанс для выполнения неконтролируемого кластеризации клиентов. |

## <a name="see-also"></a>См. также

+ [Расширение Python для SQL Server](../concepts/extension-python.md)
+ [Учебники по Службы машинного обучения SQL Server](machine-learning-services-tutorials.md)
