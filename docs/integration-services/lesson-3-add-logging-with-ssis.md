---
title: "Занятие&#160;3. Добавление журналов с помощью служб SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Занятие&#160;3. Добавление журналов с помощью служб SSIS
[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] возможно ведение журналов, что позволяет отслеживать и устранять неполадки при выполнении пакетов, обеспечивая трассировку задач и событий контейнеров. Эти возможности очень гибки. Они могут активироваться как на уровне пакетов, так и на уровне отдельных задач или контейнеров в пакете. Можно выбрать события, которые будут заноситься в журнал, а также создать несколько журналов для одного пакета.  
  
Ведение журнала обеспечивается регистратором. Каждый регистратор может сохранять данные журналов в разных форматах и на разных типах носителей. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предоставляют следующие регистраторы:  
  
-   текстовый файл  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Журнал событий Windows  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   XML-файл  
  
На этом занятии будет создана копия пакета, созданного на [занятии 2: добавление циклов с помощью служб SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md). При работе с новым пакетом будет добавлено и настроено ведение журнала, позволяющее отслеживать отдельные события при выполнении пакета. Если вы не выполняли ни одно из предыдущих занятий, можно воспользоваться копией пакета из занятия 2, которая включена в учебник.  
  
> [!IMPORTANT]  
> Для выполнения упражнений этого учебника потребуется образец базы данных **AdventureWorksDW2012** . Дополнительные сведения об установке и развертывании **AdventureWorksDW2012** см. в разделе [Образцы продуктов службы Reporting Services на сайте CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Копирование пакета занятия 2](../integration-services/step-1-copying-the-lesson-2-package.md)  
  
-   [Шаг 2. Добавление и настройка ведения журнала](../integration-services/step-2-adding-and-configuring-logging.md)  
  
-   [Шаг 3. Проверка учебного пакета, созданного на занятии 3](../integration-services/step-3-testing-the-lesson-3-tutorial-package.md)  
  
## Начало занятия  
[Шаг 1. Копирование пакета занятия 2](../integration-services/step-1-copying-the-lesson-2-package.md)  
  
  
  
