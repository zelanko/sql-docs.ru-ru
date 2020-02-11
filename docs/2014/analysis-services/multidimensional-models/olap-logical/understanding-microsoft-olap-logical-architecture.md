---
title: Логическая архитектура (Analysis Services-многомерные данные) | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62725488"
---
# <a name="logical-architecture-analysis-services---multidimensional-data"></a>Логическая архитектура (службы Analysis Services — многомерные данные)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует как серверные, так и клиентские компоненты для предоставления функциональных возможностей OLAP и интеллектуального анализа данных для приложений бизнес- [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] аналитики:  
  
-   Серверный компонент служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] реализован в виде службы Microsoft Windows. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживает несколько экземпляров на одном компьютере, при этом каждый экземпляр [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] реализуется как отдельный экземпляр службы Windows.  
  
-   Клиенты обмениваются данными со службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] с помощью общедоступного стандарта XML для аналитики (XMLA), который представляет собой протокол на базе SOAP для выполнения команд и получения ответов и предоставляется в виде веб-службы. Клиентские модели объектов также предоставляются через XML для аналитики, и доступ к ним производится через управляемый поставщик, например ADOMD.NET, или через собственный поставщик данных OLE DB.  
  
-   Команды запроса могут выдаваться с помощью следующих языков: SQL; МНОГОМЕРные выражения, язык запросов отраслевого стандарта для анализа; или расширения интеллектуального анализа данных (DMX) — язык запросов отраслевого стандарта, ориентированный на интеллектуальный анализ данных. Язык сценариев служб Analysis Services (ASSL) также может использоваться для управления объектами базы данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 Также службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживают ядро локального куба, которое позволяет приложениям на отключенных клиентах просматривать локально хранимые многомерные данные. Дополнительные сведения см. в статье [требования к архитектуре клиента для разработки Analysis Services](../olap-physical/client-architecture-requirements-for-analysis-services-development.md) .  
  
## <a name="in-this-section"></a>в этом разделе  
 **Обзор логической архитектуры**  
 [Общие сведения об логической архитектуре &#40;Analysis Services многомерных данных&#41;](logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Объекты сервера**  
 [Серверные объекты &#40;Analysis Services многомерных данных&#41;](server-objects-analysis-services-multidimensional-data.md)  
  
 **Объекты базы данных**  
 [Объекты базы данных &#40;Analysis Services многомерных данных&#41;](database-objects-analysis-services-multidimensional-data.md)  
  
 **Объекты измерений**  
 [Объекты измерения &#40;Analysis Services многомерных данных&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **Объекты куба**  
 [Объекты куба &#40;Analysis Services многомерных данных&#41;](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **Безопасность доступа пользователей**  
 [Архитектура безопасности доступа пользователей](understanding-microsoft-olap-logical-architecture.md)  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения об архитектуре Microsoft OLAP](../olap-physical/understanding-microsoft-olap-architecture.md)   
 [Физическая архитектура &#40;Analysis Services многомерных данных&#41;](../olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
