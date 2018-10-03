---
title: Программирование интеллектуального анализа данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- data mining [Analysis Services], developer's guide
ms.assetid: 9fd77b16-0b89-44ce-bcf1-7c04b62499da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8aa16d708683a33281ee0836321e11f0a16e3211
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48047704"
---
# <a name="data-mining-programming"></a>Программирование интеллектуального анализа данных
  Если встроенные инструменты и средства просмотра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не соответствуют требованиям, их можно расширить, создав собственные программные расширения служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. При таком подходе имеются два варианта.  
  
-   **XML для аналитики**  
  
     [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] поддерживают XML для аналитики (XMLA) в качестве протокола для связи с клиентскими приложениями. Службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживаются дополнительные команды, расширяющие спецификацию XML для аналитики.  
  
     Поскольку службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют XMLA для определения данных, управления данными и поддержки управления данными, можно создавать структуры интеллектуального анализа и модели интеллектуального анализа данных, используя визуальные средства среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], а затем расширяя объекты интеллектуального анализа данных, созданные с помощью скриптов DMX и ASSL.  
  
     В скриптах XMLA можно создавать и полностью изменять объекты интеллектуального анализа данных, а также программно выполнять из приложений прогнозирующие запросы к моделям.  
  
-   **Объекты AMO (AMO)**  
  
     Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] также обеспечивают полноценную платформу, позволяющую сторонним поставщикам интеллектуального анализа данных интегрировать в службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объекты интеллектуального анализа данных.  
  
     Объекты AMO позволяют создавать структуры и модели интеллектуального анализа данных. См. следующие примеры на CodePlex.  
  
    -   Браузер объектов AMO  
  
         Подключается к указанному вами экземпляру служб SSAS и перечисляет все объекты сервера и их свойства, включая структуру и модели интеллектуального анализа данных.  
  
    -   Простой образец объектов AMO  
  
         В простом образце AS описывается программный доступ к большинству основных объектов, а также демонстрируется обзор метаданных и доступ к значениям из объектов.  
  
         В образце также показано создание и обработка структуры и модели интеллектуального анализа данных, а также обзор существующей модели интеллектуального анализа данных.  
  
-   **Расширение интеллектуального анализа данных**  
  
     С помощью расширений интеллектуального анализа данных можно инкапсулировать инструкции команд, прогнозирующие запросы и запросы метаданных и возвращать результаты в табличном формате при условии, что было создано соединение с сервером служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
 [OLE DB для интеллектуального анализа данных](../../../2014/analysis-services/dev-guide/ole-db-for-data-mining.md)  
 Описываются дополнения к спецификации для поддержки интеллектуального анализа данных и многомерных данных: новые наборы строк схемы и столбцы, язык расширений интеллектуального анализа данных (DMX) для создания и управления ими структур интеллектуального анализа данных.  
  
## <a name="related-reference"></a>Связанные справочники  
 [Разработка с использованием ADOMD.NET](../multidimensional-models/adomd-net/developing-with-adomd-net.md)  
 Знакомит с клиентом ADOMD.NET и программными объектами сервера.  
  
 [Разработка объектов управления аналитикой &#40;объектов AMO&#41;](../multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
 Представляет библиотеку программирования объектов AMO.  
  
 [Язык сценариев разработки с использованием Analysis Services &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 Знакомит с XML для аналитики (XMLA) и его расширениями.  
  
## <a name="see-also"></a>См. также  
 [Руководство разработчика &#40;служб Analysis Services&#41;](../analysis-services-developer-documentation.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; ссылки](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
