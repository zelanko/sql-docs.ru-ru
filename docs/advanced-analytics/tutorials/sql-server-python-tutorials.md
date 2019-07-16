---
title: Обзор SQL Server 2017 Python tutorial - машинного обучения SQL Server
description: Общие сведения о пособия для аналитики в базе данных SQL Server 2017.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: d5a434b6e089cd77a2bd685506e5552c4e1e7f6d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961949"
---
# <a name="sql-server-2017-python-tutorials"></a>Учебники по SQL Server 2017 Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается в руководствах Python для анализа в базе данных на [службы машинного обучения SQL Server 2017](../install/sql-machine-learning-services-windows-install.md). 

+ Узнайте, как переносить и выполнять код Python в хранимых процедурах.
+ Сериализации и сохранения моделей на основе Python к базам данных SQL Server.
+ Дополнительные сведения об удаленных и локальных вычислительных контекстов и когда их следует использовать.
+ Изучите модули Microsoft Python для обработки и анализа данных и задач машинного обучения.

<a name="bkmk_pythontutorials"></a>

## <a name="python-quickstarts-and-tutorials"></a>Python краткие руководства и учебники

| Ссылка | Описание |
|------|-------------|
| [Краткое руководство. Скрипт Python «Hello world» в SQL Server](quickstart-python-run-using-t-sql.md) | Основы вызова Python в T-SQL. |
| [Краткое руководство. Создавать, обучать и использовать модели Python с хранимыми процедурами в SQL Server](quickstart-python-train-score-in-tsql.md) | Описывает механизм встраивания кода Python в хранимую процедуру, предоставляя входных данных и выполнение хранимой процедуры. |
| [Учебник. Создание модели с помощью revoscalepy](use-python-revoscalepy-to-create-model.md) | Показано, как выполнять код из удаленного терминала Python, используя контекст вычислений SQL Server. Можно немного знаком с Python инструменты и среды. Образец кода находится, создающий модель с помощью **rxLinMod**, из новой **revoscalepy** библиотеки. |
| [Учебник. Дополнительные аналитические функции Python в базе данных для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md) | В этом пошаговом руководстве end-to-end демонстрирует процесс создания полного решения Python с помощью T-SQL хранимой процедуры. Включается весь код Python.|

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Примеры кода

Эти примеры и образцы, предоставляемые группой разработки SQL Server особенно пристально, внедренной аналитики можно использовать в реальных приложениях.

| Ссылка | Описание |
|------|-------------|
| [Создание прогнозной модели с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Узнайте, как ski использование машинного обучения для прогнозирования будущих проката, что позволяет бизнес-плана и сотрудников для удовлетворения будущего спроса. |
| [Выполнение клиента кластеризации с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Узнайте, как использовать алгоритм методом k-средних для выполнения без учителя кластеризации клиентов. |

## <a name="see-also"></a>См. также

+ [Расширения Python для SQL Server](../concepts/extension-python.md)
+ [Учебники службы машинного обучения SQL Server](machine-learning-services-tutorials.md)
