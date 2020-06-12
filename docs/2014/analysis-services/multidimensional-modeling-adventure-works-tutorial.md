---
title: Многомерное моделирование (учебник по Adventure Works) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tutorials [Analysis Services]
- Analysis Services, tutorials
ms.assetid: db55e226-601a-4026-8651-573195555a59
author: minewiskan
ms.author: owend
ms.openlocfilehash: 634ad200cc8c46282eeb6146a8a590811e6d69a3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84537376"
---
# <a name="multidimensional-modeling-adventure-works-tutorial"></a>Многомерное моделирование (учебник по Adventure Works)
  Добро пожаловать в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial. В этом учебнике рассматривается, как использовать среду [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] при разработке и развертывании проекта служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] на примере вымышленной компании [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] .  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
 В этом учебнике рассматриваются следующие темы:  
  
-   Определение источников данных, представлений источников данных, измерений, атрибутов, связей атрибутов, иерархий и кубов в проекте служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] с помощью среды [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
-   Просмотр данных куба и измерения посредством развертывания проекта служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] на экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]и последующее заполнение развернутых объектов данными из базового источника данных.  
  
-   Изменение мер, измерений, иерархий, атрибутов и групп мер в проекте служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и последующее развертывание добавочных изменений в развернутый куб на сервере разработки.  
  
-   Определение в кубе вычислений, ключевых показателей эффективности, действий, перспектив, переводов и ролей безопасности.  
  
 В этом учебнике приводится описание сценария работы, что позволит лучше понять контекст для этих занятий. Дополнительные сведения см. в разделе [Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения всех занятий этого учебника потребуются образцы данных, файлов проекта и программное обеспечение. Инструкции по поиску и установке необходимых компонентов для этого учебника см. в разделе [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).  
  
 Кроме того, для успешного завершения этого учебника необходимо иметь следующие разрешения.  
  
-   Необходимо быть членом локальной группы «Администраторы» на компьютере с установленными службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или членом административной роли сервера в экземпляре [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   Для образца базы данных **AdventureWorksDW2012** нужно иметь право на чтение. Этот образец базы данных является допустимым для выпуска [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] .  
  
## <a name="lessons"></a>Занятия  
 Этот учебник включает следующие занятия.  
  
|Занятие|Предполагаемое время выполнения|  
|------------|--------------------------------|  
|[Урок 1. Определение представления источника данных в проекте Analysis Services](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)|15 минут|  
|[Урок 2. Определение и развертывание куба](lesson-2-defining-and-deploying-a-cube.md)|30 минут|  
|[Урок 3. Изменение мер, атрибутов и иерархий](lesson-3-modifying-measures-attributes-and-hierarchies.md)|45 минут|  
|[Занятие 4: Определение расширенных свойств атрибутов и измерений](lesson-4-defining-advanced-attribute-and-dimension-properties.md)|120 минут|  
|[Занятие 5.: Определение связей между измерениями и группами мер](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)|45 минут|  
|[Занятие 6: Определение вычислений](lesson-6-defining-calculations.md)|45 минут|  
|[Занятие 7. Определение ключевых показателей эффективности](lesson-7-defining-key-performance-indicators-kpis.md)|30 минут|  
|[Урок 8. Определение действий](lesson-8-defining-actions.md)|30 минут|  
|[Урок 9. Определение перспектив и преобразований](lesson-9-defining-perspectives-and-translations.md)|30 минут|  
|[Урок 10. Определение административных ролей](lesson-10-defining-administrative-roles.md)|15 минут|  
  
> [!NOTE]  
>  База данных куба, которая будет создана в этом учебнике, представляет собой упрощенную версию проекта многомерной модели служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , который входит в состав образцов баз данных Adventure Works, доступных для загрузки на сайте CodePlex. Учебная версия многомерной базы данных Adventure Works была упрощена с целью обеспечить ускоренное овладение рядом основных навыков. После завершения работы с учебником попробуйте поработать с проектом многомерной модели самостоятельно, чтобы более детально ознакомиться с многомерным моделированием в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## <a name="next-step"></a>Следующий шаг  
 Чтобы приступить к изучению этого учебника, перейдите к первому занятию: [Lesson 1: Defining a Data Source View within an Analysis Services Project](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md).  
  
  
