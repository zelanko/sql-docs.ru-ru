---
title: Руководства для аналитики в базе данных, с помощью R и машинного обучения SQL Server | Документация Майкрософт
description: Узнайте, как внедрить R, программный код языка в хранимых процедурах SQL Server и функций T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 80c4d39e87984b022340079be4d944ed6ad963e3
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030651"
---
# <a name="tutorial-in-database-r-analytics-for-sql-developers"></a>Учебник: Анализ R в базе данных для разработчиков SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом руководстве для программистов SQL, узнайте об интеграции R путем создания и развертывания на основе R в машинном обучении решения с помощью [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) базы данных на сервере SQL Server. 

В этом руководстве описываются функций R, используемых в данных, моделирование рабочего процесса. Шаги включают Просмотр данных, построения и обучения модели двоичной классификации и развертыванию модели. Вы будете использовать пример данных такси Нью-Йорке и Limosine комиссии, и модель, которую вы создадите прогнозирует ли поездку, вероятнее всего приведет к tip, на основе времени дня, пройденное расстояние и место посадки. Весь код R, используемый в этом руководстве упаковывается в хранимых процедурах, создания и выполнения в среде Management Studio.


> [!NOTE]
> 
> Это руководство доступно в R и Python. Версия Python, см. в разделе [в базе данных аналитики для разработчиков Python](../tutorials/sqldev-in-database-python-for-sql-developers.md).

## <a name="overview"></a>Обзор

Процесс создания решения машинного обучения является довольно сложна, который может включать в себя несколько средств и координации профильные специалисты по различным этапам:

+ Получение и очистка данных
+ Изучение данных и создание функции, полезные для моделирования
+ обучение и Настройка модели
+ развертывание в рабочей среде

Разработка и тестирование фактический код, лучше всего выполнять в среде разработки в выделенной. Тем не менее, после его полной проверки, вы можете легко развернуть его, чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимые процедуры в знакомой среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Ли вы программист на SQL, которые не знакомы с R или разработчик R, знакомы с SQL, этого руководства в нескольких частях представляет типичный рабочий процесс для проведения анализа в базе данных с R и SQL Server. 

- [Занятие 1., Анализ и визуализация данных фигуры и распространения посредством вызова функций R в хранимые процедуры](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Занятие 2: Создание функций данных с помощью R в T-SQL функции](sqldev-create-data-features-using-t-sql.md)
  
- [Занятие 3: Обучение и сохранение модели R с помощью функций и хранимых процедур](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Занятие 4: Прогнозирование возможных результатов, с помощью модели R в хранимой процедуре](../tutorials/sqldev-operationalize-the-model.md)

После сохранения модели в базу данных, вызовите ее для прогнозов из [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью хранимых процедур.

## <a name="prerequisites"></a>предварительные требования

Вы можете выполнять все задачи с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимые процедуры в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Это руководство предполагает знакомство с основных операций базы данных, таких как создание баз данных и таблиц, импорт данных и написания SQL-запросов. Он не предполагается, что вы знаете R. Таким образом предоставляется весь код R. 

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) или [служб SQL Server 2017 машинного обучения с поддержкой R](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Библиотеки R](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location)

+ [Разрешения](../security/user-permission.md)

+ [Демонстрационная база данных о такси Нью-ЙОРКА](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Настройка базы данных о такси Нью-ЙОРКА](demo-data-nyctaxi-in-sql.md)