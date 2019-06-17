---
title: Руководство для аналитики в базе данных, с помощью R - машинного обучения SQL Server
description: Узнайте, как внедрить R, программный код языка в хранимых процедурах SQL Server и функций T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 4f0930e3f7f9d037ebb3033cc947f243657a1480
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67140759"
---
# <a name="tutorial-r-data-analytics-for-sql-developers"></a>Учебник. Анализ данных R для разработчиков SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом руководстве для программистов SQL, узнайте об интеграции R путем создания и развертывания на основе R в машинном обучении решения с помощью [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) базы данных на сервере SQL Server. Вы будете использовать T-SQL, SQL Server Management Studio и экземпляр ядра СУБД с [служб машинного обучения] ([служб машинного обучения](../install/sql-machine-learning-services-windows-install.md) и поддержка языка R

В этом руководстве описываются функций R, используемых в данных, моделирование рабочего процесса. Шаги включают Просмотр данных, построения и обучения модели двоичной классификации и развертыванию модели. Модель, которую вы создадите прогнозирует, является ли поездку может привести tip, на основе времени дня, расстояние и место посадки. 

Весь код R, используемый в этом руководстве упаковывается в хранимых процедурах, создания и выполнения в среде Management Studio.

## <a name="background-for-sql-developers"></a>Фон для разработчиков SQL

Процесс создания решения машинного обучения является довольно сложна, который может включать в себя несколько средств и координации профильные специалисты по различным этапам:

+ Получение и очистка данных
+ Изучение данных и создание функции, полезные для моделирования
+ обучение и Настройка модели
+ развертывание в рабочей среде

Разработка и тестирование фактический код, лучше всего выполнять с помощью выделенную среду разработки R. Тем не менее, после его полной проверки, вы можете легко развернуть его, чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимые процедуры в знакомой среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Цель этого руководства в нескольких частях — введение в типичный рабочий процесс для миграции «завершения работы кода R» для SQL Server. 

- [Занятие 1. Анализ и визуализация данных фигуры и распространения посредством вызова функций R в хранимые процедуры](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Занятие 2. Создание функций данных с помощью языка R в T-SQL функции](sqldev-create-data-features-using-t-sql.md)
  
- [Занятие 3. Обучение и сохранение модели R с помощью функций и хранимых процедур](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Занятие 4. Предсказания возможных результатов, с помощью модели R в хранимой процедуре](../tutorials/sqldev-operationalize-the-model.md)

После сохранения модели в базу данных, вызовите ее для прогнозов из [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью хранимых процедур.

## <a name="prerequisites"></a>предварительные требования

Вы можете выполнять все задачи с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимые процедуры в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Это руководство предполагает знакомство с основных операций базы данных, таких как создание баз данных и таблиц, импорт данных и написания SQL-запросов. Он не предполагается, что вы знаете R. Таким образом предоставляется весь код R. 

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) или [служб SQL Server 2017 машинного обучения с поддержкой R](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Библиотеки R](../package-management/installed-package-information.md)

+ [Разрешения](../security/user-permission.md)

+ [Демонстрационная база данных о такси Нью-ЙОРКА](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Анализ и визуализация данных с помощью функций R в хранимые процедуры](../tutorials/sqldev-explore-and-visualize-the-data.md)
