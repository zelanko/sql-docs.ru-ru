---
title: Учебники по Python
description: В этой статье описываются руководства по Python для Служб машинного обучения SQL Server. Узнайте, как выполнять скрипты и создавать модели машинного обучения в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/04/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e3733f12ed93d7c84a86259742b6996333c3900f
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487357"
---
# <a name="python-tutorials-for-sql-server-machine-learning-services"></a>Учебники по Python для Служб машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описываются учебники и краткие руководства по Python для [Служб машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md).

+ Узнайте, как выполнять скрипты Python.
+ Создавайте, обучайте и развертывайте модели Python в SQL Server.
+ Узнайте об удаленных и локальных контекстах вычисления.
+ Изучите пакеты Microsoft Python для обработки и анализа данных и машинного обучения.

<a name="bkmk_pythontutorials"></a>

## <a name="python-tutorials"></a>Учебники по Python

| Учебник | Описание |
|-|-|
| [Прогнозирование проката лыж с помощью линейной регрессии](python-ski-rental-linear-regression.md) | Используйте Python и линейную регрессию для прогнозирования числа лыж напрокат. Используйте записные книжки в Azure Data Studio для подготовки данных и обучения модели, а также T-SQL для развертывания модели. |
| [Категоризация клиентов с помощью кластеризации методом k-средних](python-clustering-model.md) | Используйте Python для разработки и развертывания модели кластеризации методом k-средних, чтобы классифицировать клиентов. Используйте записные книжки в Azure Data Studio для подготовки данных и обучения модели, а также T-SQL для развертывания модели. |
| [Создание модели с помощью пакета revoscalepy](use-python-revoscalepy-to-create-model.md) | Демонстрирует запуск кода из удаленного клиента Python с помощью SQL Server в качестве контекста вычислений. В этом учебнике создается модель с помощью **rxLinMod** из библиотеки **revoscalepy**. |
| [Аналитика данных Python для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md) | В этом полном пошаговом руководстве демонстрируется процесс создания полного решения Python с помощью T-SQL. |

## <a name="python-quickstarts"></a>Краткие руководства для Python

Если вы не знакомы со службами машинного обучения SQL Server, можно также попробовать краткие руководства по Python.

| Краткое руководство | Описание |
|-|-|
| [Hello World на Python и SQL Server](quickstart-python-create-script.md) | Изучите основы вызова Python в T-SQL с помощью [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). |
| [Работа с типами данных и объектами с помощью Python в SQL Server](quickstart-python-data-structures.md) | Показывает, как SQL Server использует пакет Python pandas для работы со структурами данных. |
| [Создание и оценка модели прогнозирования на Python](quickstart-python-train-score-model.md) | Объясняется, как создать, обучить и использовать модель Python для создания прогнозов на основе новых данных. |

## <a name="next-steps"></a>Дальнейшие действия

+ [Что такое службы машинного обучения SQL Server (Python и R)?](../sql-server-machine-learning-services.md)
+ [Расширение Python в SQL Server](../concepts/extension-python.md)