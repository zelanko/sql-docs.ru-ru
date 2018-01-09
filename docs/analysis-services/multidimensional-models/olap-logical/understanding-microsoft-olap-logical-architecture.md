---
title: "Логическая архитектура (службы Analysis Services — многомерные данные) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 85b98af5dc33f21da4b54f14e60179594382c934
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="understanding-microsoft-olap-logical-architecture"></a>Основные сведения о логической архитектуре Microsoft OLAP
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] использует серверные и клиентские компоненты для предоставления оперативной аналитической обработки (OLAP) и средства интеллектуального анализа данных для приложений бизнес-аналитики:  
  
-   Серверный компонент служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] реализован в виде службы Microsoft Windows. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживает несколько экземпляров на одном компьютере, с каждым экземпляром [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] реализован как отдельный экземпляр службы Windows.  
  
-   Клиенты обмениваются данными со службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] с помощью общедоступного стандарта XML для аналитики (XMLA), который представляет собой протокол на базе SOAP для выполнения команд и получения ответов и предоставляется в виде веб-службы. Клиентские модели объектов также предоставляются через XML для аналитики, и доступ к ним производится через управляемый поставщик, например ADOMD.NET, или через собственный поставщик данных OLE DB.  
  
-   Команды запросов могут быть выражены на следующих языках: SQL; Многомерных выражений (MDX), языка запросов отраслевого стандарта для анализа; или данных расширений Интеллектуального анализа, языка запросов отраслевого стандарта ориентирован на интеллектуальный анализ данных. Язык сценариев служб Analysis Services (ASSL) также может использоваться для управления объектами базы данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 Также службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживают ядро локального куба, которое позволяет приложениям на отключенных клиентах просматривать локально хранимые многомерные данные. Дополнительные сведения см. в разделе [требования к архитектуре клиента для разработки служб Analysis Services](../../../analysis-services/multidimensional-models/olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>в этом разделе  
 **Обзор логической архитектуры**  
 [Обзор логической архитектуры &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-logical/logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Объекты сервера**  
 [Объекты сервера &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-logical/server-objects-analysis-services-multidimensional-data.md)  
  
 **Объекты базы данных**  
 [Объекты базы данных &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
 **Объекты измерений**  
 [Объекты измерений &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **Объекты куба**  
 [Объекты куба &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **Безопасность доступа пользователей**  
 [Архитектура безопасности доступа пользователей](http://msdn.microsoft.com/library/71b44e10-2bd0-44f7-8de9-7c8f5b7ac082)  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения об архитектуре Microsoft OLAP](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)   
 [Физическая архитектура &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
