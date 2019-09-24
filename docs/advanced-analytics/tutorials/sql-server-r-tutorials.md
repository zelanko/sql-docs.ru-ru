---
title: Обзор учебника SQL Server R
description: Введение в руководства по языку R для SQL Server аналитики в базе данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fc0cde616bc03be4a984d8de518770b490e4a89a
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2019
ms.locfileid: "71199349"
---
# <a name="sql-server-r-language-tutorials"></a>Учебники по языку SQL Server R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описываются руководства по языку R для аналитики в базе данных на [SQL Server 2016 служб R](../install/sql-r-services-windows-install.md) или [SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md).

+ Сведения о переносе и выполнении кода R в хранимых процедурах.
+ Сериализация и сохранение моделей на основе r для SQL Server баз данных.
+ Сведения об удаленных и локальных контекстах вычислений, а когда их следует использовать.
+ Изучите библиотеки Microsoft R для задач обработки и анализа данных и машинного обучения.

<a name="bkmk_sqltutorials"></a>

## <a name="r-quickstarts-and-tutorials"></a>Краткие руководства и учебники по R

| Ссылка | Описание |
|------|-------------|
| [Краткое руководство. Создание и выполнение простых сценариев R](quickstart-r-create-script.md) | Первый из нескольких кратких руководств, в которых показан базовый синтаксис для вызова функции R с помощью редактора запросов T-SQL, например SQL Server Management Studio. |
| [Учебник. Изучение аналитики R в базе данных для специалистов по обработке и анализу данных](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | Для разработчиков R, впервые применяющих SQL Server, в этом учебнике объясняется, как выполнять общие задачи обработки и анализа данных в SQL Server. Загрузка и визуализация данных, обучение и сохранение модели для SQL Server и использование модели для прогнозной аналитики. |
| [Учебник. Изучение аналитики R в базе данных для разработчиков SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Создавайте и развертывайте полноценное решение R, [!INCLUDE[tsql](../../includes/tsql-md.md)] используя только средства. Посвящена переносу решения в рабочую среду. Вы узнаете, как включить код на языке R в хранимую процедуру, сохранить модель R в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выполнять параметризованные вызовы модели R для составления прогнозов. |
| [Учебник. Ревоскалепр глубокое углубление](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) | Узнайте, как использовать функции в пакетах RevoScaleR. Перемещение данных между R и SQL Server и переключение контекстов вычислений в соответствии с определенной задачей. Создание моделей и графиков и их перемещение между средой разработки и сервером базы данных. |

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Примеры кода

| Ссылка | Описание |
|------|-------------|
| [Создание прогнозной модели с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Узнайте, как компания Ski Аренда может использовать машинное обучение для предсказания будущих напрокат, что помогает бизнес-плану и персоналу соответствовать будущим потребностям. |
| [Выполнение кластеризации клиентов с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Используйте неконтролируемое обучение для сегментирования клиентов на основе данных о продажах. |

## <a name="see-also"></a>См. также

+ [Расширение R для SQL Server](../concepts/extension-r.md)
+ [Учебники по Службы машинного обучения SQL Server](machine-learning-services-tutorials.md)

