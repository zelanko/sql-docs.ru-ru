---
title: Руководства для аналитики в базе данных, с помощью R и машинного обучения SQL Server | Документация Майкрософт
description: Учебник, в котором показано, как внедрить R в SQL Server хранимых процедур и функций T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 651e529bf0aa4cd4b4fab7e292e570dbb78e89d5
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461890"
---
# <a name="tutorial-learn-in-database-analytics-using-r-in-sql-server"></a>Учебник: Дополнительные аналитические функции в базе данных с помощью языка R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом руководстве для программистов SQL вы получите практический опыт работы, используя язык R для создания и развертывания решения машинного обучения, заключив код R в хранимые процедуры.

В этом учебнике используется хорошо известного общедоступного набора данных, в зависимости от поездок в такси Нью-Йорке. Чтобы пример кода выполнялось быстрее, мы создали представительную выборку из данных 1%. Эти данные будут использоваться для создания модели двоичной классификации, прогнозирующей ли определенной поездке скорее всего получить совет или нет, на основе столбцов, таких как время дня, расстояние и место посадки.

> [!NOTE]
> 
> То же решение доступен в Python. SQL Server 2017 является обязательным. См. в разделе [в базе данных аналитики для разработчиков Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="overview"></a>Обзор

Процесс создания решений end-to-end обычно состоит получения и очистки данных, просмотр данных и проектирование признаков, обучение модели и помощник по настройке и наконец развертывания модели в рабочей среде. Разработка и тестирование фактический код, лучше всего выполнять в среде разработки в выделенной. Для R, который может означать RStudio или [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)].

Однако после создания решения его можно легко развернуть в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] в знакомой среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

- [Настройка базы данных о такси Нью-ЙОРКА](demo-data-nyctaxi-in-sql.md)

- [Занятие 1., Анализ и визуализация данных фигуры и распространения посредством вызова функций R в хранимые процедуры](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Занятие 2: Создание функций данных с помощью R в T-SQL функции](sqldev-create-data-features-using-t-sql.md)
  
- [Занятие 3: Обучение и сохранение модели R с помощью функций и хранимых процедур](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Занятие 4: Код Wrap R в хранимой процедуре для ввода в эксплуатацию](../tutorials/sqldev-operationalize-the-model.md). 
  Сохранив модель в базе данных, вызовите ее для прогнозирования из [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью хранимых процедур.

## <a name="prerequisites"></a>предварительные требования

Это руководство предполагает знакомство с основных операций базы данных, таких как создание баз данных и таблиц, импорт данных и написания SQL-запросов. Он не предполагается, что вы знаете R. Таким образом предоставляется весь код R. Опытный программист SQL можно использовать предоставленный скрипт PowerShell, образец данных на сайте GitHub, и [!INCLUDE[tsql](../../includes/tsql-md.md)] в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Чтобы выполнить этот пример. 

Перед началом работы с учебником:

- Убедитесь, что у вас есть настроенный экземпляр [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) или [служб SQL Server 2017 машинного обучения с поддержкой R](../install/sql-machine-learning-services-windows-install.md#verify-installation). Кроме того [убедитесь, что у вас есть библиотеки R](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).
- Пользователь, который используется в этом руководстве необходимы разрешения на создание баз данных и другие объекты, чтобы передать данные, выберите данные, а также выполнение хранимых процедур.

> [!NOTE]
> Мы рекомендуем выполнить **не** использовать [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для написания или тестирования кода R. Если код, который необходимо внедрить в хранимой процедуре есть проблемы, сведения, который возвращается из хранимой процедуры обычно не позволяют установить причину ошибки.
> 
> Для отладки, мы рекомендуем использовать это средство, например [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)], или RStudio. Скрипты R, предоставленные в этом учебнике, были разработаны и отлажены с помощью традиционных средств R.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Настройка базы данных о такси Нью-ЙОРКА](demo-data-nyctaxi-in-sql.md)