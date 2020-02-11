---
title: Основные принципы создания скриптов многомерных выражений (Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], scripts
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [MDX]
- cubes [Analysis Services], calculations
- Multidimensional Expressions [Analysis Services], scripts
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 17cb2b326ed510a952249da6a73693b6be6ab252
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66073854"
---
# <a name="mdx-scripting-fundamentals-analysis-services"></a>Основные принципы создания скриптов многомерных выражений (службы Analysis Services)
  В службах [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]скрипты многомерных выражений состоят из одного или нескольких многомерных выражений или инструкций, заполняющих куб вычислениями.  
  
 Скрипт многомерных выражений определяет процесс вычислений для куба. Скрипт многомерных выражений также считается частью самого куба. Поэтому изменение скрипта многомерных выражений, связанного с кубом, сразу изменяет процесс вычислений для куба.  
  
 Для создания скриптов многомерных выражений можно воспользоваться конструктором кубов в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения см. в разделах [Определение назначений и других команд скриптов](../define-assignments-and-other-script-commands.md) и [Введение в сценарии многомерных выражений в Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892).  
  
 Сведения о проблемах безопасности, связанных с запросами и вычислениями MDX см. в разделе по оптимизации MDX в [SQL Server Analysis Services Performance Guide (руководстве по производительности служб SQL Server Analysis Services)](https://go.microsoft.com/fwlink/p/?LinkId=399050).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Базовый скрипт многомерных выражений &#40;многомерные выражения&#41;](the-basic-mdx-script-mdx.md)|Подробные сведения о базовых скриптах многомерных выражений, включая описание скрипта многомерных выражений по умолчанию, предусмотренного в каждом кубе, а также описание общих принципов функционирования скриптов многомерных выражений в кубах служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Управление областью и контекстом &#40;многомерные выражения&#41;](managing-scope-and-context-mdx.md)|Использование инструкций [CALCULATE](/sql/mdx/mdx-scripting-calculate) и [SCOPE](/sql/mdx/mdx-scripting-scope) и функции [This](/sql/mdx/this-mdx) для управления контекстом и областью действия в скриптах многомерных выражений.|  
|[Использование переменных и параметров &#40;&#41;многомерных выражений](using-variables-and-parameters-mdx.md)|Использование переменных и параметров в скриптах многомерных выражений.|  
|[Обработка ошибок &#40;&#41;многомерных выражений](error-handling-mdx.md)|Обработка ошибок в скриптах многомерных выражений.|  
|[Поддерживаемые многомерные выражения &#40;МНОГОМЕРные выражения&#41;](supported-mdx-mdx.md)|Перечень операторов, инструкций и функций многомерных выражений, поддерживаемых в скриптах многомерных выражений.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку многомерных выражений &#40;&#41;многомерных выражений](/sql/mdx/mdx-language-reference-mdx)  
  
  
