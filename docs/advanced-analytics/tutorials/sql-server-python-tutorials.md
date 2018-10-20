---
title: Учебники по SQL Server Python | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5cafb253cea118148bd654ea770234843f742838
ms.sourcegitcommit: b1990ec4491b5a8097c3675334009cb2876673ef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2018
ms.locfileid: "49383339"
---
# <a name="sql-server-python-tutorials"></a>Учебники по SQL Server Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье список руководств и примеров, демонстрирующих использование Python с SQL Server 2017. Через эти примеры и образцы вы узнаете:

+ Как запустить Python из T-SQL
+ Что такое удаленных и локальных вычислительных контекстов и как могут выполнять код Python, с помощью имени компьютера SQL Server
+ Создание программы-оболочки кода Python в хранимой процедуре
+ Оптимизация кода Python для рабочей среды SQL
+ Сценарии из реальной жизни для внедрения в приложения машинного обучения

Сведения о требованиях и установки, см. в разделе [предварительные требования](#bkmk_Prerequisites).

## <a name="bkmk_pythontutorials"></a>Учебники по Python

+ [С языком Python в T-SQL](run-python-using-t-sql.md)

   Основы вызова Python в T-SQL, используя механизм расширяемости, впервые введены в SQL Server 2016.

+ [Создание модели на языке Python с помощью revoscalepy машинного обучения](use-python-revoscalepy-to-create-model.md)

   На этом занятии рассматривается, как выполнить код из удаленного терминала Python, используя контекст вычислений SQL Server. Можно немного знаком с Python инструменты и среды. Образец кода находится, создающий модель с помощью **rxLinMod**, из новой **revoscalepy** библиотеки. 

+ [Python в базе данных аналитики для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md)

    В этом пошаговом руководстве end-to-end демонстрирует процесс создания полного решения Python с помощью T-SQL хранимой процедуры. Включается весь код Python.


## <a name="python-samples"></a>Примеры для Python

Эти примеры и образцы, предоставляемые группой разработки SQL Server особенно пристально, внедренной аналитики можно использовать в реальных приложениях.

+ [Создание прогнозной модели с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

  Узнайте, как ski использование машинного обучения для прогнозирования будущих проката, что позволяет бизнес-плана и сотрудников для удовлетворения будущего спроса.

  > [!TIP]
  > Теперь включает собственной оценки на основе моделей Python!

+ [Выполнение клиента кластеризации с помощью Python и SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Узнайте, как использовать алгоритм методом k-средних для выполнения без учителя кластеризации клиентов.

## <a name="see-also"></a>См. также

[Учебные материалы по R в SQL Server](sql-server-r-tutorials.md)
