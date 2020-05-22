---
title: Учебники по Python
titleSuffix: SQL machine learning
description: В этой статье описываются учебники по использованию Python для машинного обучения SQL. Узнайте, как выполнять сценарии и создавать модели машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7127be209c9637eb0c1cc701d16f0d157f90be54
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83605796"
---
# <a name="python-tutorials-for-sql-machine-learning"></a>Учебники по использованию Python для машинного обучения SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
В этой статье описываются учебники и краткие руководства по использованию Python для [Служб машинного обучения SQL Server](../sql-server-machine-learning-services.md) и [Кластеров больших данных](../../big-data-cluster/machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
В этой статье описываются учебники и краткие руководства по Python для [Служб машинного обучения SQL Server](../sql-server-machine-learning-services.md).
::: moniker-end

<a name="bkmk_pythontutorials"></a>

## <a name="python-tutorials"></a>Учебники по Python

| Учебник | Описание |
|-|-|
| [Прогнозирование проката лыж с помощью линейной регрессии](python-ski-rental-linear-regression.md) | Используйте Python и линейную регрессию для прогнозирования числа лыж напрокат. Используйте записные книжки в Azure Data Studio для подготовки данных и обучения модели, а также T-SQL для развертывания модели. |
| [Категоризация клиентов с помощью кластеризации методом k-средних](python-clustering-model.md) | Используйте Python для разработки и развертывания модели кластеризации методом k-средних, чтобы классифицировать клиентов. Используйте записные книжки в Azure Data Studio для подготовки данных и обучения модели, а также T-SQL для развертывания модели. |
| [Создание модели с помощью пакета revoscalepy](use-python-revoscalepy-to-create-model.md) | Демонстрирует запуск кода из удаленного клиента Python с помощью SQL Server в качестве контекста вычислений. В этом учебнике создается модель с помощью **rxLinMod** из библиотеки **revoscalepy**. |
| [Аналитика данных Python для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md) | В этом полном пошаговом руководстве демонстрируется процесс создания полного решения Python с помощью T-SQL. |

## <a name="python-quickstarts"></a>Краткие руководства для Python

Если вы еще не работали с машинным обучением SQL, можете также изучить краткие руководства по Python.

| Краткое руководство | Описание |
|-|-|
| [Запуск простых скриптов Python](quickstart-python-create-script.md) | Изучите основы вызова Python в T-SQL с помощью [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). |
| [Использование структур данных и объектов с помощью Python](quickstart-python-data-structures.md) | Показывает, как SQL использует пакет Python pandas для работы со структурами данных. |
| [Создание и оценка модели прогнозирования на Python](quickstart-python-train-score-model.md) | Объясняется, как создать, обучить и использовать модель Python для создания прогнозов на основе новых данных. |

## <a name="next-steps"></a>Дальнейшие действия

+ [Расширение Python в SQL Server](../concepts/extension-python.md)
