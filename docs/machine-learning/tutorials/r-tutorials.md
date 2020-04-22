---
title: Учебники по R
description: В этой статье описываются учебники и краткие руководства по R для Служб машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/13/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 952a33eb5a160acae44b5d1ae674c75b8d74cca5
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487306"
---
# <a name="r-tutorials-for-sql-server-machine-learning-services"></a>Учебники по R для Служб машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье описываются учебники и краткие руководства по R для [Служб машинного обучения SQL Server](../sql-server-machine-learning-services.md).

+ Узнайте, как выполнять скрипты R.
+ Создавайте, обучайте и развертывайте модели R в SQL Server.
+ Узнайте об удаленных и локальных контекстах вычисления.
+ Изучите пакеты Microsoft R для обработки и анализа данных и машинного обучения.

<a name="bkmk_sqltutorials"></a>

## <a name="r-quickstarts-and-tutorials"></a>Краткие руководства и учебники по R

| Ссылка | Описание |
|------|-------------|
| [Краткое руководство. Создание и выполнение простых скриптов R](quickstart-r-create-script.md) | Первое из нескольких кратких руководств, где показан базовый синтаксис для вызова функции R с помощью редактора запросов T-SQL, например SQL Server Management Studio. |
| [Руководство. Сведения об аналитических функциях в базе данных R для специалистов по анализу и обработке данных](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | В этом учебнике разработчики на R, впервые столкнувшиеся с SQL Server, узнают, как выполнять общие задачи обработки и анализа данных в SQL Server. Описывается загрузка и визуализация данных, обучение и сохранение модели для SQL Server, а также использование модели для прогнозной аналитики. |
| [Руководство. Изучение аналитических функций в базе данных R для разработчиков SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Описывается создание и развертывание полноценного решения R с помощью инструментов [!INCLUDE[tsql](../../includes/tsql-md.md)]. Основное внимание уделено переносу решения в рабочую среду. Вы узнаете, как включить код на языке R в хранимую процедуру, сохранить модель R в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выполнять параметризованные вызовы модели R для составления прогнозов. |
| [Руководство. Глубокое погружение в RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) | Сведения об использовании функций из пакетов RevoScaleR. Перемещение данных между R и SQL Server и переключение контекстов вычисления в соответствии с конкретной задачей. Создание моделей и диаграмм и их перемещение между средой разработки и сервером базы данных. |

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Примеры кода

| Ссылка | Описание |
|------|-------------|
| [Создание модели прогнозирования с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Сведения об использовании машинного обучения для прогнозирования будущих заказов в компании проката лыж, что позволяет создать бизнес-план и организовать работу с учетом будущего спроса. |
| [Выполнение кластеризации клиентов с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Использование неконтролируемого обучения для сегментирования клиентов на основе данных о продажах. |

## <a name="see-also"></a>См. также раздел

+ [Расширение R в SQL Server](../concepts/extension-r.md)