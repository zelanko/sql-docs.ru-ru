---
title: "Программирование интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016 Preview
helpviewer_keywords: data mining [Analysis Services], developer's guide
ms.assetid: 9fd77b16-0b89-44ce-bcf1-7c04b62499da
caps.latest.revision: "20"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 93e263ee6ed7e8b3eb5bdf0f6596f5ddf636f199
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="data-mining-programming"></a>Программирование интеллектуального анализа данных
  Если встроенные инструменты и средства просмотра служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] не соответствуют требованиям, их можно расширить, создав собственные программные расширения служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. При таком подходе имеются два варианта.  
  
-   **XML для аналитики**  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]поддерживает XML для аналитики (XMLA) в качестве протокола для связи с клиентскими приложениями. Службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживаются дополнительные команды, расширяющие спецификацию XML для аналитики.  
  
     Поскольку службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] используют XMLA для определения данных, управления данными и поддержки управления данными, можно создавать структуры интеллектуального анализа и модели интеллектуального анализа данных, используя визуальные средства среды [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], а затем расширяя объекты интеллектуального анализа данных, созданные с помощью скриптов DMX и ASSL.  
  
     В скриптах XMLA можно создавать и полностью изменять объекты интеллектуального анализа данных, а также программно выполнять из приложений прогнозирующие запросы к моделям.  
  
-   **Объекты AMO (AMO)**  
  
     Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] также обеспечивают полноценную платформу, позволяющую сторонним поставщикам интеллектуального анализа данных интегрировать в службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] объекты интеллектуального анализа данных.  
  
     Объекты AMO позволяют создавать структуры и модели интеллектуального анализа данных. См. следующие примеры на CodePlex.  
  
    -   Браузер объектов AMO  
  
         Подключается к указанному вами экземпляру служб SSAS и перечисляет все объекты сервера и их свойства, включая структуру и модели интеллектуального анализа данных.  
  
    -   Простой образец объектов AMO  
  
         В простом образце AS описывается программный доступ к большинству основных объектов, а также демонстрируется обзор метаданных и доступ к значениям из объектов.  
  
         В образце также показано создание и обработка структуры и модели интеллектуального анализа данных, а также обзор существующей модели интеллектуального анализа данных.  
  
-   **Расширение интеллектуального анализа данных**  
  
     С помощью расширений интеллектуального анализа данных можно инкапсулировать инструкции команд, прогнозирующие запросы и запросы метаданных и возвращать результаты в табличном формате при условии, что было создано соединение с сервером служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
 [OLE DB для интеллектуального анализа данных](../analysis-services/data-mining-programming-ole-db.md)  
 Приводит описание добавлений в спецификации, предназначенных для поддержки интеллектуального анализа данных и многомерных данных: новые наборы строк схемы и столбцы, язык расширений интеллектуального анализа данных (DMX) для создания и управления структур интеллектуального анализа данных.  
  
## <a name="related-reference"></a>Связанные справочники  
 [Разработка с использованием ADOMD.NET](../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
 Знакомит с клиентом ADOMD.NET и программными объектами сервера.  
  
 [Разработка с использованием объектов AMO &#40; Объекты AMO &#41;](../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
 Представляет библиотеку программирования объектов AMO.  
  
 [Разработка с использованием служб Analysis Services Scripting Language &#40; ASSL &#41;](../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 Знакомит с XML для аналитики (XMLA) и его расширениями.  
  
## <a name="see-also"></a>См. также:  
 [Документация для разработчика служб Analysis Services](../analysis-services/analysis-services-developer-documentation.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Ссылка](../dmx/data-mining-extensions-dmx-reference.md)  
  
  
