---
title: Руководство по аналитике Python в базе данных для разработчиков SQL
description: Узнайте, как внедрять код Python в SQL Server хранимых процедур и функций T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 6147c4670dace104c2c33c19e1fd29cbf2d4f2ee
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68468853"
---
# <a name="tutorial-python-data-analytics-for-sql-developers"></a>Учебник. Анализ данных Python для разработчиков SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом руководстве для программистов SQL вы узнаете об интеграции Python, создав и развернув решение машинного обучения на основе Python с помощью базы данных [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) на SQL Server. Вы будете использовать T-SQL, SQL Server Management Studio и экземпляр ядра СУБД с [службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) и поддержкой языка Python.

В этом учебнике описываются функции Python, используемые в рабочем процессе моделирования данных. Шаги включают исследование данных, сборку и обучение модели двоичной классификации и развертывание модели. Вы будете использовать демонстрационные данные из Комиссии "Нью-Йорк" и "Лимосине", а модель, которую вы будете создавать, прогнозирует, что в результате поездки будет получен Совет на основе времени суток, расстояния объездили и расположения для выбора. 

Весь код Python, используемый в этом руководстве, упаковывается в хранимые процедуры, создаваемые и выполняемые в Management Studio.

> [!NOTE]
> Этот учебник доступен как в R, так и в Python. Сведения о версии R см. [в статье аналитика в базе данных для разработчиков R](sqldev-in-database-r-for-sql-developers.md).

## <a name="overview"></a>Обзор

Процесс создания решения машинного обучения — это сложная задача, которая может содержать несколько средств, а также координацию экспертов в зависимости от нескольких этапов:

+ получение и очистка данных
+ изучение данных и создание функций, полезных для моделирования
+ обучение и Настройка модели
+ развертывание в рабочей среде

Разработка и тестирование фактического кода лучше выполнять с помощью выделенной среды разработки. Однако после полного тестирования скрипта его [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно легко развернуть с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимых процедур [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]в знакомой среде. Создание оболочки для внешнего кода в хранимых процедурах является основным механизмом для эксплуатацию кода в SQL Server.

Если вы являетесь программистом SQL, новым для Python, или разработчиком Python, новым для SQL, в этом многокомпонентном учебнике представлен типичный рабочий процесс для ведения аналитики в базе данных с помощью Python и SQL Server. 

+ [Занятие 1. Просмотр и визуализация данных с помощью Python](sqldev-py3-explore-and-visualize-the-data.md)

+ [Занятие 2. Создание функций данных с помощью пользовательских функций SQL](sqldev-py4-create-data-features-using-t-sql.md)

+ [Занятие 3. Обучение и сохранение модели Python с помощью T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

+ [Занятие 4. Прогнозирование возможных результатов с помощью модели Python в хранимой процедуре](sqldev-py6-operationalize-the-model.md)

После сохранения модели в базе данных можно вызвать модель для прогнозов из [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью хранимых процедур.

## <a name="prerequisites"></a>Предварительные требования

+ [SQL Server 2017 Службы машинного обучения с Python](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Разрешения](../security/user-permission.md)

+ [Демонстрационная база данных такси Нью](demo-data-nyctaxi-in-sql.md)

Все задачи можно выполнять с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимых процедур [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]в.

В этом учебнике предполагается, что вы знакомы с основными операциями с базой данных, такими как создание баз данных и таблиц, импорт данных и написание запросов SQL. Это не предполагает знание Python. Таким образом, предоставляется весь код Python. 

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Просмотр и визуализация данных с помощью Python](sqldev-py3-explore-and-visualize-the-data.md)
