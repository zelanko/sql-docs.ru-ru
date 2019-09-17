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
ms.openlocfilehash: cd458727fad637414d7c71865b2633f3caf80175
ms.sourcegitcommit: 949e55b32eff6610087819a93160a35af0c5f1c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2019
ms.locfileid: "70383555"
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

| Быстрый старт | Описание |
|-|-|
| [Hello World в Python и SQL Server](quickstart-python-run-using-t-sql.md) | Изучите основы вызова Python в T-SQL. |
| [Обработку входных и выходных данных с помощью Python в SQL Server](quickstart-python-inputs-and-outputs.md) | Узнайте, как управлять входными и выходными данными для Python в [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). |
| [Структуры данных Python в SQL Server](quickstart-python-data-structures.md) | Показывает, как SQL Server использует пакет Python Pandas для работы с структурами данных. |
| [Обучение и использование первой модели](quickstart-python-train-score-in-tsql.md) | Объясняется, как создать, обучить и использовать модель Python для прогнозирования новых данных. |

## <a name="next-steps"></a>Следующие шаги

+ [Что такое Службы машинного обучения SQL Server (Python и R)?](../what-is-sql-server-machine-learning.md)
+ [Расширение Python для SQL Server](../concepts/extension-python.md)