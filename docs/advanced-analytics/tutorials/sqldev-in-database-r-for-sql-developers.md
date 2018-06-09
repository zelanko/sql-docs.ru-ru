---
title: Внедренные учебника analytics R для SQL Server машинного обучения для разработчиков | Документы Microsoft
description: Руководство для внедрения в SQL Server R хранимые процедуры и функции T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3d2b77d73bb1b8f5d4c507b884d0a09f4647012b
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2018
ms.locfileid: "35250027"
---
# <a name="tutorial-embedded-r-in-stored-procedures-and-t-sql-functions"></a>Учебник: Внедренных R в хранимые процедуры и функции T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Цель данного руководства — предоставить программисты SQL практический опыт создания машинного обучения решения в SQL Server. В этом учебнике вы узнаете, как включить R в приложение или решение бизнес-Аналитики, заключив код R в хранимые процедуры.

> [!NOTE]
> 
> То же решение доступен в Python. SQL Server 2017 г. является обязательным. В разделе [в базе данных анализа для разработчиков Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="overview"></a>Обзор

Процесс построения законченного решения обычно состоит получения и очистки данных, изучения данных и формирования характеристик, обучения и настройки модели и, наконец, развертывания модели в рабочей среде. Разработка и тестирование фактический код лучше всего выполняется в среде разработки выделенный. Для R, который может означать RStudio или [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)].

Однако после создания решения его можно легко развернуть в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] в знакомой среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

В этом учебнике предполагается, что был предоставлен код R, необходимых для решения и сосредоточиться на построение и развертывание решения с помощью SQL Server.

- [Урок 1: Загрузите образцы данных и сценариев](../tutorials/sqldev-download-the-sample-data.md)

- [Занятие 2: Настройка учебника среды](../r/sqldev-import-data-to-sql-server-using-powershell.md)

- [Занятие 3: Анализ и визуализация данных фигуры и распространение путем вызова функций R в хранимые процедуры](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Занятие 4: Создание компонентов данных, с использованием R в функции T-SQL](../tutorials/sqldev-create-data-features-using-t-sql.md)
  
- [Занятие 5: Обучения и сохранить модель R с помощью функций и хранимых процедур](../r/sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Урок 6: Wrap R код в хранимую процедуру для ввода в эксплуатацию](../tutorials/sqldev-operationalize-the-model.md). 
  Сохранив модель в базе данных, вызовите ее для прогнозирования из [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью хранимых процедур.

## <a name="scenario"></a>Сценарий

В этом учебнике используется хорошо известных открытый набор данных, на приема-передачи в Нью-Йорк такси основе. Для запуска образца кода быстрее, мы создали репрезентативной выборки данных 1%. Эти данные будут использоваться для создания модели двоичной классификации, прогнозирующей ли определенный trip шансов получить совет или нет, на основе столбцов, таких как время дня, расстояние и место сбора.

## <a name="requirements"></a>Требования

В этом учебнике предполагается Знакомство с основных операций базы данных, таких как создание баз данных и таблиц, импорт данных и подготавливая SQL-запросы. Он не предполагается, что вы знаете R. Таким образом весь код R предоставляется. Опытный программист SQL можно использовать предоставленный скрипт PowerShell, образцы данных на GitHub, и [!INCLUDE[tsql](../../includes/tsql-md.md)] в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для завершения этого примера. 

Перед началом работы с учебником:

- Проверьте, имеется настроенный экземпляр [служб R SQL Server 2016](../install/sql-r-services-windows-install.md#verify-installation) или [служб SQL Server 2017 г машины обучения с помощью R включены](../install/sql-machine-learning-services-windows-install.md#verify-installation). Кроме того [убедитесь, что вы установили библиотек R](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).
- Пользователь, который используется для этого учебника необходимо иметь разрешения на создание баз данных и других объектов для передачи данных, выбора данных и выполнения хранимых процедур.

> [!NOTE]
> Мы рекомендуем сделать **не** использовать [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для записи или тестирование кода R. Если код, который необходимо внедрить в хранимой процедуре все проблемы, данные, возвращенные хранимой процедуры обычно недостаточно понять причину ошибки.
> 
> Для отладки, корпорация Майкрософт рекомендует использовать это средство, например [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)], или RStudio. Скрипты R, предоставленные в этом учебнике, были разработаны и отлажены с помощью традиционных средств R.

## <a name="next-lesson"></a>Следующее занятие

[Урок 1: Загрузите образец данных](../tutorials/sqldev-download-the-sample-data.md)
