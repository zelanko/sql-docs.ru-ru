---
title: Учебники по Python
titleSuffix: SQL machine learning
description: В этой статье описываются учебники по использованию Python для машинного обучения SQL. Узнайте, как выполнять сценарии и создавать модели машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/21/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: f93fc25139a69f80afa15840d254c33d2195b335
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730455"
---
# <a name="python-tutorials-for-sql-machine-learning"></a>Учебники по использованию Python для машинного обучения SQL
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
В этой статье описываются учебники и краткие руководства по использованию Python для [Служб машинного обучения SQL Server](../sql-server-machine-learning-services.md) и [Кластеров больших данных](../../big-data-cluster/machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
В этой статье описываются учебники и краткие руководства по Python для [Служб машинного обучения SQL Server](../sql-server-machine-learning-services.md).
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
В этой статье описываются учебники и краткие руководства по Python для [Служб машинного обучения в Управляемом экземпляре SQL Azure](/azure/azure-sql/managed-instance/machine-learning-services-overview).
::: moniker-end

<a name="bkmk_pythontutorials"></a>

## <a name="python-tutorials"></a>Учебники по Python

::: moniker range=">=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions"
| Учебник | Описание |
|-|-|
| [Прогнозирование проката лыж с помощью линейной регрессии](python-ski-rental-linear-regression.md) | Используйте Python и линейную регрессию для прогнозирования числа лыж напрокат. Используйте записные книжки в Azure Data Studio для подготовки данных и обучения модели, а также T-SQL для развертывания модели. |
| [Категоризация клиентов с помощью кластеризации методом k-средних](python-clustering-model.md) | Используйте Python для разработки и развертывания модели кластеризации методом k-средних, чтобы классифицировать клиентов. Используйте записные книжки в Azure Data Studio для подготовки данных и обучения модели, а также T-SQL для развертывания модели. |
| [Создание модели с помощью пакета revoscalepy](use-python-revoscalepy-to-create-model.md) | Демонстрирует запуск кода из удаленного клиента Python с помощью SQL Server в качестве контекста вычислений. В этом учебнике создается модель с помощью **rxLinMod** из библиотеки **revoscalepy**. |
| [Аналитика данных Python для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md) | В этом полном пошаговом руководстве демонстрируется процесс создания полного решения Python с помощью T-SQL. |
::: moniker-end
::: moniker range="=azuresqldb-mi-current"
| Учебник | Описание |
|-|-|
| [Прогнозирование проката лыж с помощью линейной регрессии](python-ski-rental-linear-regression.md) | Используйте Python и линейную регрессию для прогнозирования числа лыж напрокат. Используйте записные книжки в Azure Data Studio для подготовки данных и обучения модели, а также T-SQL для развертывания модели. |
| [Категоризация клиентов с помощью кластеризации методом k-средних](python-clustering-model.md) | Используйте Python для разработки и развертывания модели кластеризации методом k-средних, чтобы классифицировать клиентов. Используйте записные книжки в Azure Data Studio для подготовки данных и обучения модели, а также T-SQL для развертывания модели. |
::: moniker-end

## <a name="python-quickstarts"></a>Краткие руководства для Python

Если вы еще не работали с машинным обучением SQL, можете также изучить краткие руководства по Python.

| Краткое руководство | Описание |
|-|-|
| [Запуск простых скриптов Python](quickstart-python-create-script.md) | Изучите основы вызова Python в T-SQL с помощью [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). |
| [Использование структур данных и объектов с помощью Python](quickstart-python-data-structures.md) | Показывает, как SQL использует пакет Python pandas для работы со структурами данных. |
| [Создание и оценка модели прогнозирования на Python](quickstart-python-train-score-model.md) | Объясняется, как создать, обучить и использовать модель Python для создания прогнозов на основе новых данных. |

## <a name="next-steps"></a>Дальнейшие действия

+ [Расширение Python в SQL Server](../concepts/extension-python.md)
