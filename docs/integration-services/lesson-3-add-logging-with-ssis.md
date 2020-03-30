---
title: Урок 3. Добавление журналов с помощью служб SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 01/04/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6ebbc82f5570fb97d7b1169563bfde7c67f5be0d
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71296015"
---
# <a name="lesson-3-add-logging-with-ssis"></a>Урок 3. Добавление журналов с помощью служб SSIS

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



В [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] возможно ведение журналов, что позволяет отслеживать и устранять неполадки при выполнении пакетов, обеспечивая трассировку задач и событий контейнеров. Эти возможности очень гибки. Они могут активироваться как на уровне пакетов, так и на уровне отдельных задач или контейнеров в пакете. Можно выбрать события, которые будут заноситься в журнал, а также создать несколько журналов для одного пакета.  
  
Регистраторы создают журналы. Каждый регистратор может сохранять данные журналов в разных форматах и на разных типах носителей. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предоставляют следующие регистраторы:  
  
-   текстовый файл  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Журнал событий Windows  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   XML-файл  
  
На этом занятии будет создана копия пакета, созданного на [занятии 2: добавление циклов с помощью служб SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md). При работе с новым пакетом будет добавлено и настроено ведение журнала, позволяющее отслеживать отдельные события при выполнении пакета. Если вы не выполняли ни одно из предыдущих занятий, можно воспользоваться копией пакета из занятия 2, которая включена в учебник.  

> [!NOTE]
> Ознакомьтесь с [предварительными требованиями для урока 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites), если вы еще не сделали этого.

## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Копирование пакета занятия 2](../integration-services/lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [Шаг 2. Добавление и настройка ведения журнала](../integration-services/lesson-3-2-adding-and-configuring-logging.md)  
  
-   [Шаг 3. Тестирование пакета занятия 3](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Копирование пакета занятия 2](../integration-services/lesson-3-1-copying-the-lesson-2-package.md)  
  
