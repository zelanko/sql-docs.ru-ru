---
title: Логическая архитектура (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 074659d42e1960c5f24cf4afa20668a3d8c823b0
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60154860"
---
# <a name="logical-architecture-analysis-services---multidimensional-data"></a>Логическая архитектура (службы Analysis Services — многомерные данные)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] использует серверные и клиентские компоненты для предоставления оперативной аналитической обработки (OLAP) и средства интеллектуального анализа данных для приложений бизнес-аналитики:  
  
-   Серверный компонент служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] реализован в виде службы Microsoft Windows. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживает наличие нескольких экземпляров на одном компьютере, с каждым экземпляром [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] реализован как отдельный экземпляр службы Windows.  
  
-   Клиенты обмениваются данными со службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] с помощью общедоступного стандарта XML для аналитики (XMLA), который представляет собой протокол на базе SOAP для выполнения команд и получения ответов и предоставляется в виде веб-службы. Клиентские модели объектов также предоставляются через XML для аналитики, и доступ к ним производится через управляемый поставщик, например ADOMD.NET, или через собственный поставщик данных OLE DB.  
  
-   Команды запросов могут быть выражены на следующих языках: SQL; Многомерных выражений (MDX), стандартный язык запросов для анализа; или данных расширений Интеллектуального анализа, языка запросов отраслевого стандарта ориентированного на интеллектуальный анализ данных. Язык сценариев служб Analysis Services (ASSL) также может использоваться для управления объектами базы данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 Также службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживают ядро локального куба, которое позволяет приложениям на отключенных клиентах просматривать локально хранимые многомерные данные. Дополнительные сведения см. в разделе [требования к архитектуре клиента для разработки служб Analysis Services](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>в этом разделе  
 **Обзор логической архитектуры**  
 [Обзор логической архитектуры &#40;службы Analysis Services — многомерные данные&#41;](logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Объекты серверов**  
 [Объекты сервера &#40;службы Analysis Services — многомерные данные&#41;](server-objects-analysis-services-multidimensional-data.md)  
  
 **Объекты баз данных**  
 [Объекты баз данных (службы Analysis Services — многомерные данные)](database-objects-analysis-services-multidimensional-data.md)  
  
 **Объекты измерений**  
 [Объектов измерений &#40;службы Analysis Services — многомерные данные&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **Объекты кубов**  
 [Объекты куба &#40;службы Analysis Services — многомерные данные&#41;](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **Безопасность доступа пользователей**  
 [Архитектура безопасности доступа пользователей](understanding-microsoft-olap-logical-architecture.md)  
  
## <a name="see-also"></a>См. также  
 [Основные сведения об архитектуре Microsoft OLAP](../olap-physical/understanding-microsoft-olap-architecture.md)   
 [Физическая архитектура &#40;службы Analysis Services — многомерные данные&#41;](../olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
