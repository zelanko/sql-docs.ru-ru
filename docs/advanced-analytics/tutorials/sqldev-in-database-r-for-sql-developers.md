---
title: Руководство по аналитике в базе данных с помощью языка R
description: Узнайте, как внедрять код языка программирования R в SQL Server хранимых процедур и функций T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e15e56dfb4a27f0a99262ff1f105ceb0a1fbc294
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715379"
---
# <a name="tutorial-r-data-analytics-for-sql-developers"></a>Учебник. Аналитика данных R для разработчиков SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом руководстве для программистов SQL вы узнаете о интеграции R, создав и развернув решение для машинного обучения на базе R, используя базу данных [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) на SQL Server. Вы будете использовать T-SQL, SQL Server Management Studio и экземпляр ядра СУБД с [Службы машинного обучения] ([службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) и поддержкой языка R

В этом учебнике описываются функции R, используемые в рабочем процессе моделирования данных. Шаги включают исследование данных, сборку и обучение модели двоичной классификации и развертывание модели. Модель, которую вы создаете, прогнозирует, может ли поездка повлечь на себя подсказку на основе времени суток, расстояния поездок и выбора расположения. 

Весь код R, используемый в этом руководстве, упаковывается в хранимые процедуры, создаваемые и выполняемые в Management Studio.

## <a name="background-for-sql-developers"></a>Общие сведения для разработчиков SQL

Процесс создания решения машинного обучения — это сложная задача, которая может содержать несколько средств, а также координацию экспертов в зависимости от нескольких этапов:

+ получение и очистка данных
+ изучение данных и создание функций, полезных для моделирования
+ обучение и Настройка модели
+ развертывание в рабочей среде

Разработка и тестирование фактического кода лучше выполнять с помощью выделенной среды разработки R. Однако после полного тестирования скрипта его [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно легко развернуть с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимых процедур [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]в знакомой среде.

Цель этого многофакторного учебника — Введение в типичный рабочий процесс переноса "готового кода R" в SQL Server. 

- [Занятие 1. Просмотр и Визуализация формы данных и распределение путем вызова функций R в хранимых процедурах](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Занятие 2. Создание функций данных с помощью R в функциях T-SQL](sqldev-create-data-features-using-t-sql.md)
  
- [Занятие 3. Обучение и сохранение модели R с помощью функций и хранимых процедур](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Занятие 4. Прогнозирование возможных результатов с помощью модели R в хранимой процедуре](../tutorials/sqldev-operationalize-the-model.md)

После сохранения модели в базе данных вызовите модель для прогнозов из [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью хранимых процедур.

## <a name="prerequisites"></a>предварительные требования

Все задачи можно выполнять с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимых процедур [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]в.

В этом учебнике предполагается, что вы знакомы с основными операциями с базой данных, такими как создание баз данных и таблиц, импорт данных и написание запросов SQL. Это не предполагает знание R. Таким образом, предоставляется весь код R. 

+ [SQL Server 2016 служб r](../install/sql-r-services-windows-install.md#verify-installation) или [SQL Server службы машинного обучения с поддержкой r](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Библиотеки R](../package-management/installed-package-information.md)

+ [Разрешения](../security/user-permission.md)

+ [Демонстрационная база данных такси Нью](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Просмотр и визуализация данных с помощью функций R в хранимых процедурах](../tutorials/sqldev-explore-and-visualize-the-data.md)
