---
title: Учебники по R
titleSuffix: SQL machine learning
description: В этой статье описываются учебники по использованию R для машинного обучения SQL. Узнайте, как выполнять сценарии и создавать модели машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.topic: tutorial
author: cawrites
ms.author: chadam
ms.reviewer: garye, davidph
ms.date: 05/04/2020
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 63c271c4e1d59c9446495607b42b0b5ad13ea246
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606926"
---
# <a name="r-tutorials-for-sql-machine-learning"></a>Учебники по использованию R для машинного обучения SQL

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
В этой статье описываются учебники и краткие руководства по использованию R для работы со [Службами машинного обучения SQL Server](../sql-server-machine-learning-services.md) и [Кластерами больших данных](../../big-data-cluster/machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
В этой статье описываются учебники и краткие руководства по R для [Служб машинного обучения SQL Server](../sql-server-machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
В этой статье описываются учебники и краткие руководства по R для служб [SQL Server 2016 R Services](../r/sql-server-r-services.md).
::: moniker-end

<a name="bkmk_sqltutorials"></a>

## <a name="r-tutorials"></a>Учебники по R

| Учебник | Описание |
|------|-------------|
| [Прогнозирование проката лыж с помощью дерева принятия решений](r-predictive-model-introduction.md) | Используйте R и модель дерева принятия решений для прогнозирования числа лыж, сдаваемых напрокат. Используйте записные книжки в Azure Data Studio для подготовки данных и обучения модели, а также T-SQL для развертывания модели. |
| [Категоризация клиентов с помощью кластеризации методом k-средних](r-clustering-model-introduction.md) | Используйте R для разработки и развертывания модели кластеризации методом k-средних, чтобы классифицировать клиентов. Используйте записные книжки в Azure Data Studio для подготовки данных и обучения модели, а также T-SQL для развертывания модели. |
| [Аналитические функции R в базе данных для специалистов по анализу и обработке данных](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | В этом учебнике разработчики на R, впервые столкнувшиеся с SQL Server, узнают, как выполнять общие задачи обработки и анализа данных в SQL Server. Описывается загрузка и визуализация данных, обучение и сохранение модели для SQL Server, а также использование модели для прогнозной аналитики. |
| [Аналитические функции R в базе данных для разработчиков SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) | Описывается создание и развертывание полноценного решения R с помощью инструментов [!INCLUDE[tsql](../../includes/tsql-md.md)]. Основное внимание уделено переносу решения в рабочую среду. Вы узнаете, как включить код на языке R в хранимую процедуру, сохранить модель R в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выполнять параметризованные вызовы модели R для составления прогнозов. |

## <a name="r-quickstarts"></a>Краткие руководства по R

Если вы еще не работали с машинным обучением SQL, можете также изучить краткие руководства по R.

| Краткое руководство | Описание |
|-|-|
| [Запуск простых скриптов R](quickstart-r-create-script.md) | Изучите основы вызова R в T-SQL с помощью [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). |
| [Использование структур данных и объектов с помощью R](quickstart-r-data-types-and-objects.md) | Описывается, как SQL использует R для обработки структур данных. |
| [Создание и оценка прогнозной модели в R](quickstart-r-data-types-and-objects.md) | Объясняется, как создать, обучить и использовать модель R для создания прогнозов на основе новых данных. |

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные технические сведения об использовании R в SQL Server см. в разделе [Расширение языка R в SQL Server](../concepts/extension-r.md).
