---
title: Учебники по R
description: Введение в учебники по языку R для аналитики внутри базы данных в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7c71ebfbda37e66050f868fa7676d0247e84840e
ms.sourcegitcommit: add39e028e919df7d801e8b6bb4f8ac877e60e17
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2019
ms.locfileid: "74119225"
---
# <a name="sql-server-r-language-tutorials"></a>Учебники по языку R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта статья описывает учебники по языку R для аналитики внутри базы данных в [службах SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) или [Службах машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md).

+ Сведения о выполнении кода R и создании оболочки для него в хранимых процедурах.
+ Сериализация и сохранение моделей на основе R в базах данных SQL Server.
+ Сведения об удаленных и локальных контекстах вычисления и их использовании.
+ Изучение библиотек Microsoft R для задач обработки и анализа данных и машинного обучения.

<a name="bkmk_sqltutorials"></a>

## <a name="r-quickstarts-and-tutorials"></a>Краткие руководства и учебники по R

| Ссылка | Описание |
|------|-------------|
| [Краткое руководство. Создание и выполнение простых скриптов R](quickstart-r-create-script.md) | Первое из нескольких кратких руководств, где показан базовый синтаксис для вызова функции R с помощью редактора запросов T-SQL, например SQL Server Management Studio. |
| [Учебник. Сведения об аналитических функциях в базе данных R для специалистов по анализу и обработке данных](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | В этом учебнике разработчики на R, впервые столкнувшиеся с SQL Server, узнают, как выполнять общие задачи обработки и анализа данных в SQL Server. Описывается загрузка и визуализация данных, обучение и сохранение модели для SQL Server, а также использование модели для прогнозной аналитики. |
| [Учебник. Изучение аналитических функций в базе данных R для разработчиков SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Описывается создание и развертывание полноценного решения R с помощью инструментов [!INCLUDE[tsql](../../includes/tsql-md.md)]. Основное внимание уделено переносу решения в рабочую среду. Вы узнаете, как включить код на языке R в хранимую процедуру, сохранить модель R в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выполнять параметризованные вызовы модели R для составления прогнозов. |
| [Учебник. Глубокое погружение в RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) | Сведения об использовании функций из пакетов RevoScaleR. Перемещение данных между R и SQL Server и переключение контекстов вычисления в соответствии с конкретной задачей. Создание моделей и диаграмм и их перемещение между средой разработки и сервером базы данных. |

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>Примеры кода

| Ссылка | Описание |
|------|-------------|
| [Создание модели прогнозирования с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Сведения об использовании машинного обучения для прогнозирования будущих заказов в компании проката лыж, что позволяет создать бизнес-план и организовать работу с учетом будущего спроса. |
| [Выполнение кластеризации клиентов с помощью R и SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Использование неконтролируемого обучения для сегментирования клиентов на основе данных о продажах. |

## <a name="see-also"></a>См. также раздел

+ [Расширение R в SQL Server](../concepts/extension-r.md)
+ [Учебники по Службам машинного обучения SQL Server](machine-learning-services-tutorials.md)

