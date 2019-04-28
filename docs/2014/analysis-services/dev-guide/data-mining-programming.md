---
title: Программирование интеллектуального анализа данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- data mining [Analysis Services], developer's guide
ms.assetid: 9fd77b16-0b89-44ce-bcf1-7c04b62499da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9d18e97a60bf1c6108b3672f40747e8b612ad6e6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62732270"
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
 [Разработка с использованием ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
 Знакомит с клиентом ADOMD.NET и программными объектами сервера.  
  
 [Разработка объектов управления аналитикой (объекты AMO)](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)  
 Представляет библиотеку программирования объектов AMO.  
  
 [Разработка на языке ASSL (язык ASSL)](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 Знакомит с XML для аналитики (XMLA) и его расширениями.  
  
## <a name="see-also"></a>См. также  
 [Руководство разработчика &#40;служб Analysis Services&#41;](../analysis-services-developer-documentation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
