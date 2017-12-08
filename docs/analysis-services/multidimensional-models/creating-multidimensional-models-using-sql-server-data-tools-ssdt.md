---
title: "Создание многомерных моделей с помощью SQL Server Data Tools (SSDT) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSAS, environments
- Analysis Services, development
- SQL Server Analysis Services, environments
- projects [Analysis Services]
- solutions [Analysis Services]
ms.assetid: 132ed779-3ec8-4734-9698-802116d1b017
caps.latest.revision: "63"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 8069e4cb513ca83cd161564c6d9a0b2284890fdc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="creating-multidimensional-models-using-sql-server-data-tools-ssdt"></a>Создание многомерных моделей с помощью SQL Server Data Tools (SSDT)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предусмотрены две различные среды для построения и развертывания решений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , а также для управления ими: [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] и [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Обе эти среды реализуют систему проектов. Дополнительные сведения о проектах Visual Studio см. в разделе [Проекты как контейнеры](http://go.microsoft.com/fwlink/?LinkId=63960) в библиотеке сети MSDN.  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] является средой разработки на базе среды [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 2010, используемой для создания и изменения решений бизнес-аналитики. При помощи среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]можно создавать проекты служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , содержащие определения объектов (кубов, измерений и т. д.) служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , которые хранятся в XML-файлах, содержащих элементы языка сценариев служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (ASSL). Эти проекты содержатся в решениях, где также содержатся проекты из других компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , включая службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]можно разрабатывать проекты служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] как часть решения, которое не зависит от какого-либо конкретного экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Во время разработки объекты могут быть развернуты на экземпляре на тестовом сервере с целью проверки, после чего этот же проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может быть использован для развертывания объектов в экземплярах на одном или нескольких промежуточных или рабочих серверах. Проекты и элементы в решении, которое включает в себя службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , могут интегрироваться с системой управления версиями исходного кода, например [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe. Дополнительные сведения о создании проекта [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] с использованием служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]см. в разделе [Создание проекта служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md). Средой [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] можно также воспользоваться, чтобы напрямую подсоединиться к существующему экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для создания и изменения объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , без работы с проектом и без хранения определений объекта в XML-файлах. Дополнительные сведения см. в разделах [Базы данных многомерных моделей (службы SSAS)](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md)и [Подключение в режиме "в сети" к базе данных служб Analysis Services](../../analysis-services/multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] представляет собой среду управления и администрирования, которая используется главным образом для администрирования экземпляров служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]позволяет управлять объектами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (создавать резервные копии, выполнять обработку и т. д.), а также создавать новые объекты напрямую в существующем экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с помощью скриптов XMLA. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] предоставляет проект скриптов сервера анализа данных, в котором можно выполнять разработку и сохранение скриптов, созданных с использованием многомерных выражений (MDX), расширений интеллектуального анализа данных (DMX) и XML для аналитики (XMLA). Обычно проекты скриптов сервера анализа данных используются для выполнения задач по управлению или для повторного создания объектов, например баз данных или кубов, в экземплярах служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Подобные проекты могут сохраняться как часть решения и интегрироваться с контролем исходного кода. Дополнительные сведения о создании проекта скриптов сервера анализа данных в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] с помощью [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]см. в разделе [Проект скриптов служб Analysis Services в среде SQL Server Management Studio](../../analysis-services/instances/analysis-services-scripts-project-in-sql-server-management-studio.md).  
  
## <a name="introducing-solutions-projects-and-items"></a>Знакомство с решениями, проектами и элементами  
 И среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , и среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] предоставляют проекты, которые, в свою очередь, организованы в решения. Решение может содержать несколько проектов, а проект обычно содержит несколько элементов. При создании проекта автоматически создается новое решение, а в существующее решение при необходимости можно добавлять проекты. Объекты, которые содержатся в проекте, зависят от его типа. Элементы в каждом контейнере проекта хранятся в виде файлов, расположенных в папках проекта в файловой системе.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] содержит следующие проекты в типе «Проекты бизнес-аналитики».  
  
|Проект|Description|  
|-------------|-----------------|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Проект|Содержит определения объектов для одиночной базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения о создании проекта [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] см. в разделе [Создание проекта служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md).|  
|Импорт базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 2008|Предоставляет мастер, который можно использовать для создания нового проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] путем импортирования определений объектов из существующей базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Проект|Содержит определения объектов для набора пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Дополнительные сведения см. в разделе [Службы SQL Server Integration Services](../../integration-services/sql-server-integration-services.md).|  
|Мастер проектов отчетов|Предоставляет мастер, который помогает выполнить процесс создания проекта отчета с помощью служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Дополнительные сведения см. в разделе [Службы Reporting Services (SSRS)](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md).|  
|Проект модели отчета.|Содержит определения объектов для модели отчета служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в разделе [Службы Reporting Services (SSRS)](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md).|  
|Проект сервера отчетов|Содержит определения объектов для одного или нескольких отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в разделе [Службы Reporting Services (SSRS)](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md).|  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] также содержит несколько типов проектов, предназначенных для различных типов запросов или скриптов, как показано в следующей таблице.  
  
|Проект|Description|  
|-------------|-----------------|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Сценарии|Содержит скрипты расширений интеллектуального анализа данных, многомерных выражений и XML для аналитики для служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], а также соединения с экземплярами служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , в которых эти скрипты могут выполняться. Дополнительные сведения см. в разделе [Проект скриптов служб Analysis Services в среде SQL Server Management Studio](../../analysis-services/instances/analysis-services-scripts-project-in-sql-server-management-studio.md).|  
|Скрипты SQL Server Compact|Содержит скрипты SQL для SQL Server Compact, а также соединения с экземплярами SQL Server Compact, в которых могут выполняться эти скрипты.|  
|Скрипты SQL Server|Содержит скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] и XQuery для экземпляра компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , а также соединения с экземплярами компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , в которых эти скрипты могут выполняться. Дополнительные сведения см. в статье [SQL Server Database Engine](../../database-engine/configure-windows/sql-server-database-engine.md).|  
  
 Дополнительные сведения по решениям и проектам см. в разделе «Управление решениями, проектами и файлами» документации по среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .NET или в библиотеке MSDN.  
  
## <a name="choosing-between-sql-server-management-studio-and-sql-server-data-tools"></a>Выбор среды SQL Server Management Studio или SQL Server Data Tools  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] предназначена для администрирования и настройки существующих объектов в компоненте [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] предназначена для разработки решений в области бизнес-аналитики, которые включают функции [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Ниже приведены некоторые различия между средами [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] предоставляет интегрированную среду для соединения с экземплярами служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to configure, manageи administer objects within an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. С использованием этих скриптов можно также использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для создания или изменения объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , но среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] не предоставляет графический интерфейс для конструирования и определения объектов.  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] предоставляет интегрированную среду разработки для разработки решений бизнес-аналитики. Среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] можно использовать в проектном режиме, использующем определения на основе XML объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , содержащихся в проектах и решениях. Использование среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в проектном режиме означает, что изменения объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] применяются к определениям объектов на основе XML, но не применяются непосредственно к объекту в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] до тех пор, пока решение не будет развернуто. Среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] можно также использовать в режиме в сети, т. е. напрямую подключаться к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и работать с объектами существующей базы данных.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] расширяет возможности разработки приложений бизнес-аналитики, так как позволяет работать с проектами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в многопользовательской среде с управлением версиями без необходимости наличия активного соединения с экземпляром [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] предоставляет прямой доступ к существующим объектам для опроса и тестирования и может использоваться для более быстрой реализации предварительно внесенных в сценарий баз данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Однако после того, как проект был развернут в производственной среде, необходимо проявлять осторожность при работе с базой данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и ее объектами в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Это нужно, чтобы не перезаписать изменения, внесенные в объекты непосредственно в существующей базе данных, и изменения, сделанные в проекте служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , в котором было первоначально сформировано развернутое решение. Дополнительные сведения см. в разделах [Работа с проектами и базами данных служб Analysis Services на этапе разработки](../../analysis-services/multidimensional-models/work-with-analysis-services-projects-and-databases-in-development.md)и [Работа с проектами и базами данных служб Analysis Services в рабочей среде](../../analysis-services/multidimensional-models/work-with-analysis-services-projects-and-databases-in-production.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Создание проекта служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
-   [Настройка свойств проекта служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)  
  
-   [Построение проектов служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)  
  
-   [Развертывание проектов служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
-   [Работа с проектами и базами данных служб Analysis Services на этапе разработки](../../analysis-services/multidimensional-models/work-with-analysis-services-projects-and-databases-in-development.md)  
  
-   [Работа с проектами и базами данных служб Analysis Services в рабочей среде](../../analysis-services/multidimensional-models/work-with-analysis-services-projects-and-databases-in-production.md)  
  
## <a name="see-also"></a>См. также  
 [Создание проекта служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)   
 [Проекта скриптов служб Analysis Services в SQL Server Management Studio](../../analysis-services/instances/analysis-services-scripts-project-in-sql-server-management-studio.md)   
 [Базы данных многомерных моделей (службы SSAS)](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md)  
  
  
