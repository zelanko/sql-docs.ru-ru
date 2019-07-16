---
title: Обзор руководства SQL Server R - машинного обучения SQL Server
description: Общие сведения о руководствах языка R для анализа в базе данных SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 467c9320880f1b113cecd36101345f6ee99f7b75
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961935"
---
# <a name="sql-server-r-language-tutorials"></a>Учебники по языку SQL Server R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается язык учебные материалы по R в базе данных аналитики на [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) или [службы машинного обучения SQL Server 2017](../install/sql-machine-learning-services-windows-install.md).

+ Узнайте, как переносить и выполнять код R в хранимые процедуры.
+ Сериализации и сохранения моделей на основе r базы данных SQL Server.
+ Дополнительные сведения об удаленных и локальных вычислительных контекстов и когда их следует использовать.
+ Изучение библиотеки Microsoft R для обработки и анализа данных и задач машинного обучения.

<a name="bkmk_sqltutorials"></a>

## <a name="r-quickstarts-and-tutorials"></a>R краткие руководства и учебники

| Ссылка | Описание |
|------|-------------|
| [Краткое руководство. С помощью языка R в T-SQL](rtsql-using-r-code-in-transact-sql-quickstart.md) | Первый из несколько кратких руководств, с этой иллюстрирует базовый синтаксис для вызова функции R в редакторе запросов T-SQL, например SQL Server Management Studio. |
| [Учебник. Узнайте аналитики R в базе данных для специалистов по анализу данных](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | Для разработчиков R в SQL Server, в этом учебнике объясняется как распространенные задачи обработки и анализа данных выполнение в SQL Server. Загрузить и визуализации данных, обучения и сохранения модели в SQL Server и использовать модели для прогнозной аналитики. |
| [Учебник. Узнайте аналитики R в базе данных для разработчиков SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Создание и развертывание полное решение R, используя только [!INCLUDE[tsql](../../includes/tsql-md.md)] средства. Описание перемещения решения в рабочую среду. Вы узнаете, как включить код на языке R в хранимую процедуру, сохранить модель R в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выполнять параметризованные вызовы модели R для составления прогнозов. |
| [Учебник. Глубокое погружение в обработку RevoScalepR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) | Узнайте, как использовать функции в пакетах RevoScaleR. Перемещение данных между R и SQL Server и коммутатором контекстов вычисления для выполнения определенной задачи. Создание моделей и графиков и перемещать их между средой разработки и сервер базы данных. |

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Примеры кода

| Ссылка | Описание |
|------|-------------|
| [Создание прогнозной модели с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Узнайте, как ski использование машинного обучения для прогнозирования будущих проката, что позволяет бизнес-плана и сотрудников для удовлетворения будущего спроса. |
| [Выполнение клиента кластеризации с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Используйте неконтролируемого обучения для сегментирования потребителей на основе данных о продажах. |

## <a name="see-also"></a>См. также

+ [Расширения R для SQL Server](../concepts/extension-r.md)
+ [Учебники службы машинного обучения SQL Server](machine-learning-services-tutorials.md)

