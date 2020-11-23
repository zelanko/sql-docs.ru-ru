---
title: Учебник по R. Прогнозирование стоимости поездки в нью-йоркском такси с использованием двоичной классификации
titleSuffix: SQL machine learning
description: В этой серии руководств, состоящий из пяти частей, вы узнаете, как внедрять код R в хранимые процедуры SQL Server и функции T-SQL с использованием машинного обучения SQL для прогнозирования стоимости поездки в нью-йоркском такси с помощью двоичной классификации.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/15/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||>=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: db8a0c073821df46e6d9d5bda43e74aae19a2501
ms.sourcegitcommit: 54cd97a33f417432aa26b948b3fc4b71a5e9162b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2020
ms.locfileid: "94585066"
---
# <a name="r-tutorial-predict-nyc-taxi-fares-with-binary-classification"></a>Учебник по R. Прогнозирование стоимости поездки в нью-йоркском такси с использованием двоичной классификации
[!INCLUDE [SQL Server 2016 SQL MI](../../includes/applies-to-version/sqlserver2016-asdbmi.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
В этой серии руководств для программистов SQL вы узнаете об интеграции R в [Службах машинного обучения SQL Server](../sql-server-machine-learning-services.md) или в [кластерах больших данных](../../big-data-cluster/machine-learning-services.md).
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
В этой серии (из пяти частей) руководств для программистов SQL вы узнаете об интеграции R в [Службах машинного обучения SQL Server](../sql-server-machine-learning-services.md).
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
В этой серии руководств для программистов SQL вы узнаете об интеграции R в [Службы R для SQL Server 2016](../sql-server-machine-learning-services.md).
::: moniker-end

::: moniker range=">=azuresqldb-mi-current||=sqlallproducts-allversions"
В этой серии (из пяти частей) руководств для программистов SQL вы узнаете об интеграции R в [службы машинного обучения в управляемом экземпляре SQL Azure](/azure/azure-sql/managed-instance/machine-learning-services-overview).
::: moniker-end

Вы создадите и развернете решение для машинного обучения на базе R, используя образец базы данных на SQL Server. Вы будете использовать T-SQL, Azure Data Studio или SQL Server Management Studio, а также экземпляр ядра СУБД с поддержкой машинного обучения SQL и языка R.

В этой серии руководств описываются функции R, используемые в рабочем процессе моделирования данных. Серия содержит следующие этапы: исследование данных, сборка и обучение модели двоичной классификации и развертывание модели. Вы будете использовать образец данных Комиссии по такси и лимузинам Нью‑Йорка. Модель, которую вы создадите, будет предсказывать вероятность получения чаевых в зависимости от времени суток, пройденного расстояния и места посадки пассажира.

В первой части этой серии вы установите необходимые компоненты и восстановите образец базы данных. Во второй и третьей частях вы создадите сценарии R для подготовки данных и обучения модели машинного обучения. Затем в четвертой и пятой частях вы запустите эти скрипты R в базе данных с помощью хранимых процедур T-SQL.

Работая с этой статьей, вы узнаете о следующем.

> [!div class="checklist"]
> + Установка необходимых компонентов
> + Восстановление примера базы данных

Во [второй части](r-taxi-classification-explore-data.md) вы ознакомитесь с образцом данных и создадите несколько графиков.

В [третьей части](r-taxi-classification-create-features.md) вы узнаете, как создавать функции из необработанных данных с помощью функции Transact-SQL. Затем вы вызовите эту функцию из хранимой процедуры, чтобы создать таблицу, содержащую значения характеристик.

В [четвертой части](r-taxi-classification-train-model.md) вы научитесь загружать модули и вызывать необходимые функции для создания и обучения модели с помощью хранимой процедуры SQL Server.

Из [пятой части](r-taxi-classification-deploy-model.md) вы узнаете, как ввести в эксплуатацию модели, которые были обучены и сохранены в соответствии с инструкциями в четвертой части.

> [!NOTE]
> Это руководство доступно как для языка R, так и для Python. Сведения о версии Python см. в разделе [Учебник по Python. Прогнозирование стоимости поездки в нью-йоркском такси с использованием двоичной классификации](r-taxi-classification-introduction.md).

## <a name="prerequisites"></a>Предварительные условия

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
+ Установка [Служб R в SQL Server 2016](../install/sql-r-services-windows-install.md#verify-installation)
::: moniker-end

::: moniker range=">=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions"
+ Установка [Служб машинного обучения SQL Server с поддержкой R](../install/sql-machine-learning-services-windows-install.md#verify-installation)
::: moniker-end

+ Установка [библиотек R](../package-management/r-package-information.md)

+ [Предоставление разрешений на выполнение скриптов Python](../security/user-permission.md)

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
+ Начиная с SQL Server 2019, механизм изоляции требует предоставления соответствующих разрешений каталогу, в котором хранится файл графика. Дополнительные сведения о настройке этих разрешений см. в разделе [Разрешения для файлов программы | SQL Server 2019 в Windows: изменения в изоляции в Службах машинного обучения](../install/sql-server-machine-learning-services-2019.md#file-permissions).
::: moniker-end

+ Восстановление демонстрационной базы данных [нью-йоркского такси](demo-data-nyctaxi-in-sql.md)

Все задачи можно выполнять с помощью хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] в Azure Data Studio или [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

В этом руководстве предполагается, что вы уже знакомы с основными операциями с базой данных, такими как создание баз данных и таблиц, импорт данных и написание запросов SQL. Знание языка R не требуется. Поэтому весь код на R предоставляется в готовом виде.

## <a name="background-for-sql-developers"></a>Пояснения для разработчиков на SQL

Процесс создания решения машинного обучения — это сложная задача, для которой может потребоваться использование нескольких средств, а также координация работы экспертов в различных областях, и которая состоит из нескольких этапов:

+ получение и очистка данных;
+ изучение данных и выявление характеристик, полезных для моделирования;
+ обучение и настройка модели;
+ развертывание в рабочей среде.

Разработку и тестирование написанного кода лучше выполнять в выделенной среде разработки R. Однако после полного тестирования сценария его можно легко развернуть в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] в знакомой среде Azure Data Studio или [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Упаковка внешнего кода в хранимые процедуры является основным механизмом для эксплуатации кода в SQL Server.

После сохранения модели в базе данных, можно вызвать ее для получения прогноза из [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью хранимых процедур.

Если вы программист SQL, который малознаком с R, или разработчиком на R, малознакомым с SQL, в этой серии руководств можно увидеть типичный рабочий процесс для реализации аналитики в базе данных с помощью R и SQL Server.

## <a name="next-steps"></a>Дальнейшие шаги

Работая с этой статьей, вы выполните следующие задачи:

> [!div class="checklist"]
> + Установленные компоненты
> + Восстановлена демонстрационная база данных

> [!div class="nextstepaction"]
> [Учебник по R. Изучение и визуализация данных](r-taxi-classification-explore-data.md)