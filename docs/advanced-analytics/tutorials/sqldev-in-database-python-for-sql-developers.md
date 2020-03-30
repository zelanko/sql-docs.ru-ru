---
title: Python и T-SQL. Разработка модели
description: Узнайте, как внедрить код Python в хранимые процедуры SQL Server и функции T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3bafc3a524ec854dc9bf1669660827d5a6bc80f7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "74901894"
---
# <a name="tutorial-python-data-analytics-for-sql-developers"></a>Руководство по Аналитика данных Python для разработчиков SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом руководстве для программистов SQL вы узнаете об интеграции Python путем создания и развертывания решения машинного обучения на основе Python с использованием базы данных [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) на SQL Server. Вы будете использовать T-SQL, SQL Server Management Studio и экземпляр ядра СУБД со [Службами машинного обучения](../install/sql-machine-learning-services-windows-install.md) и поддержкой языка Python.

В этом руководстве описываются функции Python, используемые в рабочем процессе моделирования данных. Обучение включает следующие этапы: исследование данных, сборка и обучение модели двоичной классификации и развертывание модели. Вы будете использовать выборочные данные Комиссии по такси и лимузинам Нью-Йорка, а модель, которую вы создадите, будет предсказывать вероятность получения чаевых в зависимости от времени суток, пройденного расстояния и места посадки пассажира. 

Весь код Python, используемый в этом руководстве, упаковывается в хранимые процедуры, создаваемые и выполняемые в Management Studio.

> [!NOTE]
> Это руководство доступно как для языка R, так и для Python. Руководство для языка R см. в разделе [Аналитические функции в базе данных для разработчиков R](sqldev-in-database-r-for-sql-developers.md).

## <a name="overview"></a>Обзор

Процесс создания решения машинного обучения — это сложная задача, для которой может потребоваться использование нескольких средств, а также координация работы экспертов в различных областях, и которая состоит из нескольких этапов:

+ получение и очистка данных;
+ изучение данных и выявление характеристик, полезных для моделирования;
+ обучение и настройка модели;
+ развертывание в рабочей среде.

Разработку и тестирование написанного кода лучше выполнять в выделенной среде разработки. Однако после полного тестирования сценария его можно легко развернуть в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] в знакомой среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Упаковка внешнего кода в хранимые процедуры является основным механизмом для эксплуатации кода в SQL Server.

Независимо от того, являетесь ли вы программистом SQL, плохо знакомым с Python, или разработчиком Python, плохо знакомым с SQL, в этом учебнике, состоящем из нескольких частей, вы найдете типичный рабочий процесс для ведения аналитики в базе данных с помощью Python и SQL Server. 

+ [Занятие 1. Анализ и визуализация данных при помощи Python](sqldev-py3-explore-and-visualize-the-data.md)

+ [Занятие 2. Формирование характеристик данных с помощью пользовательских функций SQL](sqldev-py4-create-data-features-using-t-sql.md)

+ [Урок 3. Обучение и сохранение модели Python с помощью T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

+ [Занятие 4. Прогнозирование возможных результатов с помощью модели Python в хранимой процедуре](sqldev-py6-operationalize-the-model.md)

После сохранения модели в базе данных, можно вызвать ее для получения прогноза из [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью хранимых процедур.

## <a name="prerequisites"></a>Предварительные требования

+ [Службы машинного обучения SQL Server с использованием Python](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Разрешения](../security/user-permission.md)

+ [Демонстрационная база данных такси Нью-Йорка](demo-data-nyctaxi-in-sql.md)

Все задачи можно выполнить с помощью хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

В этом руководстве предполагается, что вы уже знакомы с основными операциями с базой данных, такими как создание баз данных и таблиц, импорт данных и написание запросов SQL. Это не включает знание языка Python. Поэтому весь код на Python предоставляется. 

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Анализ и визуализация данных при помощи Python](sqldev-py3-explore-and-visualize-the-data.md)
