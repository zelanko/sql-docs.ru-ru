---
title: "Управление решениями интеллектуального анализа данных и объектами | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], managing
- managing mining models
ms.assetid: 06fc61dd-925c-4347-8677-7046ee5d2f6f
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4a3f1f0dc49296c7b2b4182de5eb69abbb720f1b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="management-of-data-mining-solutions-and-objects"></a>Управление решениями и объектами интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] содержит клиентские средства, которые можно использовать для управления существующей структуры интеллектуального анализа данных и моделей интеллектуального анализа данных. В этом разделе описаны операции управления, которые могут выполняться с помощью каждой из сред.  
  
 Кроме этого, управление объектами интеллектуального анализа данных может осуществляться программно через объекты AMO или путем соединения с базами данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из других клиентов, например надстройки интеллектуального анализа данных для [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Перемещение объектов интеллектуального анализа данных](../../analysis-services/data-mining/moving-data-mining-objects.md)  
  
 [Требования к обработке и связанные замечания (интеллектуальный анализ данных)](../../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
 [Наблюдение за интеллектуальным анализом данных с помощью приложения SQL Server Profiler (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/using-sql-server-profiler-to-monitor-data-mining-analysis-services-data-mining.md)  
  
## <a name="location-of-data-mining-objects"></a>Обнаружение объектов интеллектуального анализа данных  
 Обработанные структуры и модели интеллектуального анализа данных хранятся в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Если при разработке объектов интеллектуального анализа данных было создано соединение с базой данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в **немедленном** режиме, то все создаваемые объекты по мере работы незамедлительно добавляются на сервер. Однако если объекты интеллектуального анализа данных проектируются в режиме **«в сети»** , который в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]используется по умолчанию, то создаваемые объекты интеллектуального анализа данных представляют собой только контейнеры метаданных до тех пор, пока не будет выполнено их развертывание в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Поэтому после каждого изменения объекта необходимо выполнить его повторное развертывание на сервере служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения об архитектуре интеллектуального анализа данных см. в разделе [Физическая архитектура (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/physical-architecture-analysis-services-data-mining.md).  
  
> [!NOTE]  
>  Некоторые клиенты, например надстройки интеллектуального анализа данных для [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007, также позволяют создавать модели интеллектуального анализа данных сеанса и структуры интеллектуального анализа данных; в них используются соединения с экземплярами, но создаваемые структуры и модели интеллектуального анализа данных при этом сохраняются только на протяжении сеанса. Этими моделями можно управлять через клиент точно так же, как структурами и моделями, сохраненными в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , но после отключения от экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]объекты удаляются.  
  
## <a name="managing-data-mining-objects-in-sql-server-data-tools"></a>Управление объектами интеллектуального анализа данных в среде SQL Server Data Tools.  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , упрощают создание, просмотр и изменение объектов интеллектуального анализа данных.  
  
 По следующим ссылкам можно получить полезные сведения об изменении объектов интеллектуального анализа данных в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
-   [Изменение представления источников данных, используемого для структуры интеллектуального анализа данных](../../analysis-services/data-mining/edit-the-data-source-view-used-for-a-mining-structure.md)  
  
-   [изменить свойства структуры интеллектуального анализа данных](../../analysis-services/data-mining/change-the-properties-of-a-mining-structure.md)  
  
-   [Изменение свойств модели интеллектуального анализа данных](../../analysis-services/data-mining/change-the-properties-of-a-mining-model.md)  
  
-   [Просмотр или изменение флагов моделирования (интеллектуальный анализ данных)](../../analysis-services/data-mining/view-or-change-modeling-flags-data-mining.md)  
  
-   [Просмотр или изменение параметров алгоритма](../../analysis-services/data-mining/view-or-change-algorithm-parameters.md)  
  
 Обычно в качестве средства разработки новых проектов и добавления существующих будет использоваться среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , а затем для управление проектами и объектами — среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Однако уже развернутые объекты экземпляра служб Analysis Services можно изменить и напрямую с помощью параметра **Immediate** с соединением с сервером в режиме «в сети». Дополнительные сведения см. в разделе [Connect in Online Mode to an Analysis Services Database](../../analysis-services/multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md).  
  
> [!WARNING]  
>  Все изменения структуры или модели интеллектуального анализа данных, включая изменения таких метаданных, как имена или описания, требуют повторной обработки соответствующей модели или структуры.  
  
 Если нет возможности использовать файл решения, который использовался для создания проекта или объектов интеллектуального анализа данных, то можно импортировать существующий проект с сервера с помощью мастера импорта служб Analysis Services, внести необходимые изменения в объекты, а затем выполнить повторное развертывание с параметром **Incremental** . Дополнительные сведения см. в разделе [Импорт проекта интеллектуального анализа данных с помощью мастера импорта служб Analysis Services](../../analysis-services/data-mining/import-a-data-mining-project-using-the-analysis-services-import-wizard.md).  
  
## <a name="managing-data-mining-objects-in-sql-server-management-studio"></a>Управление объектами интеллектуального анализа данных в среде SQL Server Management Studio  
 Среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]позволяет создавать скрипты со структурами и моделями интеллектуального анализа данных, обрабатывать эти структуры и модели и удалять их. В обозревателе объектов можно просмотреть лишь ограниченный набор свойств, однако дополнительные метаданные о моделях интеллектуального анализа данных доступны в окне редактора **DMX-запрос** , где нужно выбрать соответствующую структуру интеллектуального анализа данных.  
  
-   [Создание DMX-запроса в среде SQL Server Management Studio](../../analysis-services/data-mining/create-a-dmx-query-in-sql-server-management-studio.md)  
  
## <a name="managing-data-mining-objects-programmatically"></a>Программное управление объектами интеллектуального анализа данных  
 Создание, изменение, обработка и удаление объектов интеллектуального анализа данных реализуются при помощи следующих языков программирования. Разные языки предназначены для выполнения разных задач. Результатом могут стать ограничения на типы операций, доступных для выполнения. Например, некоторые свойства объектов интеллектуального анализа данных нельзя изменить с помощью расширений интеллектуального анализа данных, для этого придется использовать язык XMLA или объекты AMO.  
  
### <a name="analysis-management-objects-amo"></a>Объекты AMO  
 Объекты AMO — это объектная модель, построенная на основе XMLA, которая обеспечивает полный доступ к объектам интеллектуального анализа данных. Объекты AMO позволяют создавать, развертывать и отслеживать структуры и модели интеллектуального анализа данных.  
  
-   [Основные понятия и модель объектов AMO](../../analysis-services/multidimensional-models/analysis-management-objects/amo-concepts-and-object-model.md)  
  
-   <xref:Microsoft.AnalysisServices>  
  
 **Ограничения.** Нет.  
  
### <a name="data-mining-extensions-dmx"></a>Расширения интеллектуального анализа данных  
 Расширения интеллектуального анализа данных могут быть использованы вместе с другими интерфейсами команд, например с [!INCLUDE[vstecado](../../includes/vstecado-md.md)] или ADOMD.Net, для создания и удаления структур и моделей интеллектуального анализа данных, а также создания запросов к ним.  
  
-   [Инструкции определения расширений интеллектуального анализа данных](../../dmx/dmx-statements-data-definition.md)  
  
 **Ограничения.** Некоторые свойства нельзя изменять с помощью расширения интеллектуального анализа данных.  
  
### <a name="xml-for-analysis-xmla"></a>XML для аналитики (XMLA)  
 XML для аналитики, или XMLA, — это язык описания данных DDL для всех служб Analysis Services. XMLA позволяет управлять большинством объектов интеллектуального анализа данных и операциями на сервере. Все операции управления между клиентом и сервером можно выполнять с помощью XMLA. Для удобства при создании оболочки для XML можно использовать язык скриптов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (ASSL).  
  
 **Ограничения.** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] формируются некоторые XMLA-инструкции, поддерживаемые только для внутреннего использования. Их использование в скриптах XML DDL невозможно.  
  
## <a name="see-also"></a>См. также  
 [Документация для разработчика служб Analysis Services](../../analysis-services/analysis-services-developer-documentation.md)  
  
  
