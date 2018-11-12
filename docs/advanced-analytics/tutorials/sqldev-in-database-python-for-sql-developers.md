---
title: В базе данных аналитики Python для разработчиков SQL | Документация Майкрософт
description: Узнайте, как внедрять код Python в хранимые процедуры SQL Server и функций T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8c992cbda06d158bec0b76d6d46d71157a08cf3e
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2018
ms.locfileid: "51032991"
---
# <a name="tutorial-in-database-python-analytics-for-sql-developers"></a>Учебник: Анализ Python в базе данных для разработчиков SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом руководстве для программистов SQL, Дополнительные сведения о Python интеграции путем создания и развертывания на базе Python машинного обучения с помощью решения [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) базы данных на сервере SQL Server. 

В этом руководстве описываются функции Python, которые используются в рабочий процесс моделирования данных. Шаги включают Просмотр данных, построения и обучения модели двоичной классификации и развертыванию модели. Вы будете использовать пример данных такси Нью-Йорке и Limosine комиссии, и модель, которую вы создадите прогнозирует ли поездку, вероятнее всего приведет к tip, на основе времени дня, пройденное расстояние и место посадки. Весь код Python, используемый в этом руководстве упаковывается в хранимых процедурах, создания и выполнения в среде Management Studio.

> [!NOTE]
> Это руководство доступно в R и Python. В версии R, см. в разделе [в базе данных аналитики для разработчиков R](sqldev-in-database-r-for-sql-developers.md).

## <a name="overview"></a>Обзор

Процесс создания решения машинного обучения является довольно сложна, который может включать в себя несколько средств и координации профильные специалисты по различным этапам:

+ Получение и очистка данных
+ Изучение данных и создание функции, полезные для моделирования
+ обучение и Настройка модели
+ развертывание в рабочей среде

Разработка и тестирование фактический код, лучше всего выполнять в среде разработки в выделенной. Тем не менее, после его полной проверки, вы можете легко развернуть его, чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимые процедуры в знакомой среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Упаковки внешний код в хранимых процедурах, является основным механизмом для эксплуатации кода в SQL Server.

Являетесь ли вы программист на SQL, которые работали с Python или разработчика Python, знакомы с SQL, этого руководства в нескольких частях представляет типичный рабочий процесс для проведения анализа в базе данных с Python и SQL Server. 

+ [Занятие 1: Анализ и визуализация данных с помощью Python](sqldev-py3-explore-and-visualize-the-data.md)

+ [Занятие 2: Создание данных функции с помощью с помощью пользовательских функций SQL](sqldev-py4-create-data-features-using-t-sql.md)

+ [Занятие 3: Обучение и сохранение модели Python с помощью T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

+ [Занятие 4: Прогнозирование возможных результатов, с помощью модели Python в хранимой процедуре](sqldev-py6-operationalize-the-model.md)

После сохранения модели в базу данных, можно вызвать модели для создания прогнозов из [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью хранимых процедур.

## <a name="prerequisites"></a>предварительные требования

+ [Службы машинного обучения SQL Server 2017 с помощью Python](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Разрешения](../security/user-permission.md)

+ [Демонстрационная база данных о такси Нью-ЙОРКА](demo-data-nyctaxi-in-sql.md)

Вы можете выполнять все задачи с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимые процедуры в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Это руководство предполагает знакомство с основных операций базы данных, таких как создание баз данных и таблиц, импорт данных и написания SQL-запросов. Он не предполагается, что вы знаете Python. Таким образом предоставляется весь код Python. 

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Анализ и визуализация данных с помощью Python](sqldev-py3-explore-and-visualize-the-data.md)
