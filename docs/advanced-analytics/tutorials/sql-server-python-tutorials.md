---
title: Учебники по Python
description: В этой статье описываются учебники по Python для SQL Server Службы машинного обучения. Узнайте, как выполнять скрипты Python. Создавайте, обучить и развертывайте модели Python для SQL Server. Сведения об удаленных и локальных контекстах вычислений. Изучите пакеты Microsoft Python для обработки и анализа данных и машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/04/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 80f714810acd8c04c80fe0b8abe5214a456f6dd6
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2019
ms.locfileid: "71199406"
---
# <a name="python-tutorials-for-sql-server-machine-learning-services"></a>Учебники по Python для SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описываются учебники и краткие руководства по Python для [SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md).

+ Узнайте, как выполнять скрипты Python.
+ Создавайте, обучить и развертывайте модели Python для SQL Server.
+ Сведения об удаленных и локальных контекстах вычислений.
+ Изучите пакеты Microsoft Python для обработки и анализа данных и машинного обучения.

<a name="bkmk_pythontutorials"></a>

## <a name="python-tutorials"></a>Учебники по Python

| Учебник | Описание |
|-|-|
| [Прогнозирование Ski аренд с линейной регрессией](python-ski-rental-linear-regression.md) | Используйте Python и линейную регрессию для прогнозирования числа Ski напрокат. Используйте записные книжки в Azure Data Studio для подготовки данных и обучения модели, а также T-SQL для развертывания модели. |
| [Классификация клиентов с помощью кластеризации с использованием k-средних](python-clustering-model.md) | Используйте Python для разработки и развертывания модели кластеризации на K-средних, чтобы классифицировать клиентов. Используйте записные книжки в Azure Data Studio для подготовки данных и обучения модели, а также T-SQL для развертывания модели. |
| [Создание модели с помощью revoscalepy](use-python-revoscalepy-to-create-model.md) | Демонстрирует запуск кода из удаленного клиента Python с помощью SQL Server в качестве контекста вычислений. В этом руководстве создается модель, использующая **rxLinMod** из библиотеки **revoscalepy** . |
| [Анализ данных Python для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md) | В этом сквозном пошаговом руководстве демонстрируется процесс создания полного решения Python с помощью T-SQL. |

## <a name="python-quickstarts"></a>Краткие руководства по Python

Если вы не знакомы с SQL Server Службы машинного обучения, можно также испытать краткие руководства по Python.

| Краткое руководство | Описание |
|-|-|
| [Hello World в Python и SQL Server](quickstart-python-create-script.md) | Изучите основы вызова Python в T-SQL с помощью [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). |
| [Работа с типами данных и объектами с помощью Python в SQL Server](quickstart-python-data-structures.md) | Показывает, как SQL Server использует пакет Python Pandas для работы с структурами данных. |
| [Создание и оценка прогнозной модели в Python](quickstart-python-train-score-model.md) | Объясняется, как создать, обучить и использовать модель Python для создания прогнозов на основе новых данных. |

## <a name="next-steps"></a>Следующие шаги

+ [Что такое Службы машинного обучения SQL Server (Python и R)?](../what-is-sql-server-machine-learning.md)
+ [Расширение Python для SQL Server](../concepts/extension-python.md)