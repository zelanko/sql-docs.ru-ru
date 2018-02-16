---
title: "(Службы Analysis Services) основные принципы создания скриптов многомерных Выражений | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cubes [Analysis Services], scripts
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [MDX]
- cubes [Analysis Services], calculations
- Multidimensional Expressions [Analysis Services], scripts
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bba357ff7e84870c9b734591b80712c25de2b750
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="mdx-scripting-fundamentals-analysis-services"></a>Основные принципы создания скриптов многомерных выражений (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
В службах [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] скрипты многомерных выражений состоят из одного или нескольких многомерных выражений или инструкций, заполняющих куб вычислениями.  
  
 Скрипт многомерных выражений определяет процесс вычислений для куба. Скрипт многомерных выражений также считается частью самого куба. Поэтому изменение скрипта многомерных выражений, связанного с кубом, сразу изменяет процесс вычислений для куба.  
  
 Для создания скриптов многомерных выражений можно воспользоваться конструктором кубов в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения см. в разделах [Определение назначений и других команд скриптов](../../../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md) и [Введение в сценарии многомерных выражений в Microsoft SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81892).  
  
 Сведения о проблемах безопасности, связанных с запросами и вычислениями MDX см. в разделе по оптимизации MDX в [SQL Server Analysis Services Performance Guide (руководстве по производительности служб SQL Server Analysis Services)](http://go.microsoft.com/fwlink/p/?LinkId=399050).  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Базовый скрипт многомерных Выражений &#40; Многомерные Выражения &#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md)|Подробные сведения о базовых скриптах многомерных выражений, включая описание скрипта многомерных выражений по умолчанию, предусмотренного в каждом кубе, а также описание общих принципов функционирования скриптов многомерных выражений в кубах служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Управление областью и контекстом &#40; Многомерные Выражения &#41;](../../../analysis-services/multidimensional-models/mdx/managing-scope-and-context-mdx.md)|Использование инструкций [CALCULATE](../../../mdx/mdx-scripting-calculate.md) и [SCOPE](../../../mdx/mdx-scripting-scope.md) и функции [This](../../../mdx/this-mdx.md) для управления контекстом и областью действия в скриптах многомерных выражений.|  
|[Использование переменных и параметров &#40; Многомерные Выражения &#41;](../../../analysis-services/multidimensional-models/mdx/using-variables-and-parameters-mdx.md)|Использование переменных и параметров в скриптах многомерных выражений.|  
|[Обработка ошибок &#40; Многомерные Выражения &#41;](../../../analysis-services/multidimensional-models/mdx/error-handling-mdx.md)|Обработка ошибок в скриптах многомерных выражений.|  
|[Поддержка многомерных Выражений &#40; Многомерные Выражения &#41;](../../../analysis-services/multidimensional-models/mdx/supported-mdx-mdx.md)|Перечень операторов, инструкций и функций многомерных выражений, поддерживаемых в скриптах многомерных выражений.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку многомерных Выражений &#40; Многомерные Выражения &#41;](../../../mdx/mdx-language-reference-mdx.md)  
  
  
