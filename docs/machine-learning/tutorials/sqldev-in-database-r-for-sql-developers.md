---
title: Учебник по R и T-SQL. Разработка модели
description: Узнайте, как внедрять код на языке программирования R в хранимые процедуры SQL Server и функции T-SQL.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 06/13/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a27bd044dbdca7a05663080be08ebaff1acb86d9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785605"
---
# <a name="tutorial-r-data-analytics-for-sql-developers"></a>Руководство по Аналитика данных R для разработчиков SQL
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

В этом руководстве для программистов на SQL вы узнаете об интеграции R путем создания и развертывания решения машинного обучения на основе R с использованием базы данных [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) в SQL Server. Вы будете использовать T-SQL, SQL Server Management Studio и экземпляр ядра СУБД со [Службами машинного обучения](../install/sql-machine-learning-services-windows-install.md) и поддержкой языка R.

В этом руководстве описываются функции R, используемые в рабочем процессе моделирования данных. Обучение включает следующие этапы: исследование данных, сборка и обучение модели двоичной классификации и развертывание модели. Модель, которую вы создадите, будет предсказывать вероятность получения чаевых в зависимости от времени суток, пройденного расстояния и места посадки пассажира. 

Весь код R, используемый в этом руководстве, упаковывается в хранимые процедуры, создаваемые и выполняемые в Management Studio.

## <a name="background-for-sql-developers"></a>Пояснения для разработчиков на SQL

Процесс создания решения машинного обучения — это сложная задача, для которой может потребоваться использование нескольких средств, а также координация работы экспертов в различных областях, и которая состоит из нескольких этапов:

+ получение и очистка данных;
+ изучение данных и выявление характеристик, полезных для моделирования;
+ обучение и настройка модели;
+ развертывание в рабочей среде.

Разработку и тестирование написанного кода лучше выполнять в выделенной среде разработки R. Однако после полного тестирования сценария его можно легко развернуть в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] в знакомой среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Цель этого руководства, состоящего из нескольких частей, — ознакомление с типичным рабочим процессом для переноса готового кода R в SQL Server. 

- [Занятие 1. Изучение и визуализация формы и распределения данных путем вызова функций R в хранимых процедурах](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Занятие 2. Создание признаков данных с помощью скрипта R в функциях T-SQL](sqldev-create-data-features-using-t-sql.md)
  
- [Урок 3. Обучение и сохранение модели R с помощью функций и хранимых процедур](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Занятие 4. Прогнозирование возможных результатов с помощью модели R в хранимой процедуре](../tutorials/sqldev-operationalize-the-model.md)

Сохранив модель в базе данных, вызовите ее для прогнозирования из [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью хранимых процедур.

## <a name="prerequisites"></a>Предварительные требования

Все задачи можно выполнить с помощью хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

В этом руководстве предполагается, что вы уже знакомы с основными операциями с базой данных, такими как создание баз данных и таблиц, импорт данных и написание запросов SQL. Знание языка R не требуется. Поэтому весь код на R предоставляется. 

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) или [Службы машинного обучения SQL Server с включенной поддержкой языка R](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Библиотеки R](../package-management/r-package-information.md)

+ [Разрешения](../security/user-permission.md)

+ [Демонстрационная база данных такси Нью-Йорка](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Изучение и визуализация данных с помощью функций R в хранимых процедурах](../tutorials/sqldev-explore-and-visualize-the-data.md)
