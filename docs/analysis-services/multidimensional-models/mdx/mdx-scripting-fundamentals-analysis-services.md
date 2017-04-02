---
title: "Основные принципы создания скриптов многомерных выражений (службы Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "кубы [службы Analysis Services], скрипты"
  - "вычисления [службы Analysis Services], скрипты"
  - "многомерные выражения [службы Analysis Services], скрипты"
  - "скрипты [многомерные выражения]"
  - "кубы [службы Analysis Services], вычисления"
  - "многомерные выражения [службы Analysis Services], скрипты"
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 34
---
# Основные принципы создания скриптов многомерных выражений (службы Analysis Services)
  В службах [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] скрипты многомерных выражений состоят из одного или нескольких многомерных выражений или инструкций, заполняющих куб вычислениями.  
  
 Скрипт многомерных выражений определяет процесс вычислений для куба. Скрипт многомерных выражений также считается частью самого куба. Поэтому изменение скрипта многомерных выражений, связанного с кубом, сразу изменяет процесс вычислений для куба.  
  
 Для создания скриптов многомерных выражений можно воспользоваться конструктором кубов в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения см. в разделах [Определение назначений и других команд скриптов](../../../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md) и [Введение в сценарии многомерных выражений в Microsoft SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81892).  
  
 Сведения о проблемах безопасности, связанных с запросами и вычислениями MDX см. в разделе по оптимизации MDX в [SQL Server Analysis Services Performance Guide (руководстве по производительности служб SQL Server Analysis Services)](http://go.microsoft.com/fwlink/p/?LinkId=399050).  
  
## В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Базовый скрипт многомерных выражений (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md)|Подробные сведения о базовых скриптах многомерных выражений, включая описание скрипта многомерных выражений по умолчанию, предусмотренного в каждом кубе, а также описание общих принципов функционирования скриптов многомерных выражений в кубах служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Управление областью и контекстом (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/managing-scope-and-context-mdx.md)|Использование инструкций [CALCULATE](../Topic/CALCULATE%20Statement%20\(MDX\).md) и [SCOPE](../Topic/SCOPE%20Statement%20\(MDX\).md) и функции [This](../../../mdx/this-mdx.md) для управления контекстом и областью действия в скриптах многомерных выражений.|  
|[Переменные и параметры (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/using-variables-and-parameters-mdx.md)|Использование переменных и параметров в скриптах многомерных выражений.|  
|[Обработка ошибок (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/error-handling-mdx.md)|Обработка ошибок в скриптах многомерных выражений.|  
|[Поддержка многомерных выражений (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/supported-mdx-mdx.md)|Перечень операторов, инструкций и функций многомерных выражений, поддерживаемых в скриптах многомерных выражений.|  
  
## См. также  
 [Справочник по языку многомерных выражений (многомерные выражения)](../../../mdx/mdx-language-reference-mdx.md)  
  
  