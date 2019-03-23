---
title: Урок 3. Добавление ведения журнала | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1a3a32b35503ff6dae2e103f46e45a28359b948d
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58390962"
---
# <a name="lesson-3-adding-logging"></a>Урок 3. Добавление журнала
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] возможно ведение журналов, что позволяет отслеживать и устранять неполадки при выполнении пакетов, обеспечивая трассировку задач и событий контейнеров. Эти возможности очень гибки. Они могут активироваться как на уровне пакетов, так и на уровне отдельных задач или контейнеров в пакете. Можно выбрать события, которые будут заноситься в журнал, а также создать несколько журналов для одного пакета.  
  
 Ведение журнала обеспечивается регистратором. Каждый регистратор может сохранять данные журналов в разных форматах и на разных типах носителей. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предоставляют следующие регистраторы:  
  
-   текстовый файл  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Журнал событий Windows  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   XML-файл  
  
 На этом занятии вы создадите копию пакета, созданного на [занятии 2: Добавление циклов](lesson-2-adding-looping-with-ssis.md). При работе с новым пакетом будет добавлено и настроено ведение журнала, позволяющее отслеживать отдельные события при выполнении пакета. Если вы не выполняли ни одно из предыдущих занятий, можно воспользоваться копией пакета из занятия 2, которая включена в учебник.  
  
> [!IMPORTANT]  
>  Для выполнения упражнений этого учебника потребуется образец базы данных **AdventureWorksDW2012** . Дополнительные сведения об установке и развертывании **AdventureWorksDW2012**см. в разделе [Образцы продуктов службы Reporting Services на сайте CodePlex](https://go.microsoft.com/fwlink/p/?LinkID=52691).  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Копирование пакета занятия 2](lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [Шаг 2. Добавление и настройка ведения журнала](lesson-3-2-adding-and-configuring-logging.md)  
  
-   [Шаг 3. Проверка учебного пакета занятия 3](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
 [Шаг 1. Копирование пакета занятия 2](lesson-3-1-copying-the-lesson-2-package.md)  
  
  
