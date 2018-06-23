---
title: Логическая архитектура (службы Analysis Services — многомерные данные) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 468ad4b5f7456524b4d44552bd18cf80406bee07
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188559"
---
# <a name="logical-architecture-analysis-services---multidimensional-data"></a>Логическая архитектура (службы Analysis Services — многомерные данные)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] использует серверные и клиентские компоненты для предоставления оперативной аналитической обработки (OLAP) и средства интеллектуального анализа данных для приложений бизнес-аналитики:  
  
-   Серверный компонент служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] реализован в виде службы Microsoft Windows. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживает несколько экземпляров на одном компьютере, с каждым экземпляром [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] реализован как отдельный экземпляр службы Windows.  
  
-   Клиенты обмениваются данными со службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] с помощью общедоступного стандарта XML для аналитики (XMLA), который представляет собой протокол на базе SOAP для выполнения команд и получения ответов и предоставляется в виде веб-службы. Клиентские модели объектов также предоставляются через XML для аналитики, и доступ к ним производится через управляемый поставщик, например ADOMD.NET, или через собственный поставщик данных OLE DB.  
  
-   Команды запросов могут быть выражены на следующих языках: SQL; Многомерных выражений (MDX), языка запросов отраслевого стандарта для анализа; или данных расширений Интеллектуального анализа, языка запросов отраслевого стандарта ориентирован на интеллектуальный анализ данных. Язык сценариев служб Analysis Services (ASSL) также может использоваться для управления объектами базы данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 Также службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживают ядро локального куба, которое позволяет приложениям на отключенных клиентах просматривать локально хранимые многомерные данные. Дополнительные сведения см. в разделе [требования к архитектуре клиента для разработки служб Analysis Services](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>в этом разделе  
 **Обзор логической архитектуры**  
 [Обзор логической архитектуры &#40;службы Analysis Services — многомерные данные&#41;](logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Объекты серверов**  
 [Объекты сервера &#40;службы Analysis Services — многомерные данные&#41;](server-objects-analysis-services-multidimensional-data.md)  
  
 **Объекты баз данных**  
 [Объекты базы данных &#40;службы Analysis Services — многомерные данные&#41;](database-objects-analysis-services-multidimensional-data.md)  
  
 **Объекты измерений**  
 [Измерение объектов &#40;службы Analysis Services — многомерные данные&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **Объекты кубов**  
 [Объекты куба &#40;службы Analysis Services — многомерные данные&#41;](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **Безопасность доступа пользователей**  
 [Архитектура безопасности доступа пользователей](https://msdn.microsoft.com/library/bb522595(SQL.120).aspx)  
  
## <a name="see-also"></a>См. также  
 [Основные сведения об архитектуре Microsoft OLAP](../olap-physical/understanding-microsoft-olap-architecture.md)   
 [Физическая архитектура &#40;службы Analysis Services — многомерные данные&#41;](../olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  