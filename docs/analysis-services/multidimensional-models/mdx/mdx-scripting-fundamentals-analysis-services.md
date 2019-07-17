---
title: (Службы Analysis Services) основные принципы создания скриптов многомерных Выражений | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9ca77b9c10f1dba24127e35e5fe55d7ffcdad3dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68165847"
---
# <a name="mdx-scripting-fundamentals-analysis-services"></a>Основные принципы создания скриптов многомерных выражений (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  В службах [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]скрипты многомерных выражений состоят из одного или нескольких многомерных выражений или инструкций, заполняющих куб вычислениями.  
  
 Скрипт многомерных выражений определяет процесс вычислений для куба. Скрипт многомерных выражений также считается частью самого куба. Поэтому изменение скрипта многомерных выражений, связанного с кубом, сразу изменяет процесс вычислений для куба.  
  
 Для создания скриптов многомерных выражений можно воспользоваться конструктором кубов в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения см. в разделах [Определение назначений и других команд скриптов](../../../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md) и [Введение в сценарии многомерных выражений в Microsoft SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81892).  
  
 Сведения о проблемах безопасности, связанных с запросами и вычислениями MDX см. в разделе по оптимизации MDX в [SQL Server Analysis Services Performance Guide (руководстве по производительности служб SQL Server Analysis Services)](http://go.microsoft.com/fwlink/p/?LinkId=399050).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Базовый скрипт многомерных выражений (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md)|Подробные сведения о базовых скриптах многомерных выражений, включая описание скрипта многомерных выражений по умолчанию, предусмотренного в каждом кубе, а также описание общих принципов функционирования скриптов многомерных выражений в кубах служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Управление областью и контекстом (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/managing-scope-and-context-mdx.md)|Использование инструкций [CALCULATE](../../../mdx/mdx-scripting-calculate.md) и [SCOPE](../../../mdx/mdx-scripting-scope.md) и функции [This](../../../mdx/this-mdx.md) для управления контекстом и областью действия в скриптах многомерных выражений.|  
|[Переменные и параметры (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/using-variables-and-parameters-mdx.md)|Использование переменных и параметров в скриптах многомерных выражений.|  
|[Обработка ошибок (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/error-handling-mdx.md)|Обработка ошибок в скриптах многомерных выражений.|  
|[Поддержка многомерных выражений (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/supported-mdx-mdx.md)|Перечень операторов, инструкций и функций многомерных выражений, поддерживаемых в скриптах многомерных выражений.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку многомерных выражений (многомерные выражения)](../../../mdx/mdx-language-reference-mdx.md)  
  
  
