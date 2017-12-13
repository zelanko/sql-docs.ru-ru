---
title: "Управление областью и контекстом (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts [MDX], context
- scope [MDX]
- CALCULATE statement
- This function [MDX]
- SCOPE statement
- scripts [MDX], scope
ms.assetid: 631e7c20-8be9-4c35-8609-76516aef19d1
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: ceb78ab6b4ee006784660dbeeaa71558c565aa6c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="managing-scope-and-context-mdx"></a>Управление областью и контекстом (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]В [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], скрипт многомерных выражений (MDX) можно применять ко всему кубу или к определенной части куба, в особых точках при выполнении сценария. В скриптах многомерных выражений используется многоуровневый подход к вычислениям в кубе при помощи этапов вычисления.  
  
> [!NOTE]  
>  Дополнительные сведения о влиянии этапов вычисления на сами вычисления см. в разделе [Основные сведения о порядке этапов и порядке вычисления (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md).  
  
 Для управления этапами вычислений, областью и контекстом в скриптах многомерных выражений применяются инструкция CACULATE, функция **This** и инструкция SCOPE.  
  
## <a name="using-the-calculate-statement"></a>Инструкция CALCULATE  
 Инструкция CALCULATE заполняет каждую ячейку в кубе статистическими данными. Например, скрипт многомерных выражений по умолчанию содержит одну инструкцию CALCULATE в начале.  
  
 Дополнительные сведения о синтаксисе инструкции CALCULATE см. в разделе [Инструкция CALCULATE (многомерные выражения)](../../../mdx/mdx-scripting-calculate.md).  
  
> [!NOTE]  
>  Если скрипт содержит инструкцию SCOPE, содержащую в себе инструкцию CALCULATE, в многомерных выражениях инструкция CALCULATE вычисляется в рамках контекста вложенного куба, определенного инструкцией SCOPE, а не для всего куба.  
  
## <a name="using-the-this-function"></a>Функция This  
 Функция **This** позволяет обратиться к текущему вложенному кубу в рамках скрипта многомерных выражений. Функция **This** позволяет быстро заполнить ячейки в текущем вложенном кубе многомерным выражением. Функция **This** часто используется в сочетании с инструкцией SCOPE для изменения содержимого конкретного вложенного куба на определенном этапе вычислений.  
  
> [!NOTE]  
>  Если в скрипте присутствует инструкция SCOPE, содержащая функцию **This** , в многомерных выражениях функция **This** вычисляется в рамках контекста вложенного куба, определенного инструкцией SCOPE, а не для всего куба.  
  
### <a name="this-function-example"></a>Пример функции This  
 В следующем примере команд скрипта многомерных выражений функция **This** используется для увеличения значения меры Amount в группе мер Finance образца куба [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] на 10 % для потомков элемента Redmond в измерении Customer.  
  
```  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 Дополнительные сведения о синтаксисе функции **This** см. в разделе [This (многомерные выражения)](../../../mdx/this-mdx.md).  
  
## <a name="using-the-scope-statement"></a>Инструкция SCOPE  
 Инструкция SCOPE определяет текущий вложенный куб, содержащий другие выражения и инструкции многомерных выражений и определяющий для них область в рамках скрипта многомерных выражений. В многомерных выражениях эти другие выражения и многомерные инструкции, включая функцию **This** и инструкцию CALCULATE, вычисляются в контексте данного вложенного куба.  
  
 Инструкция SCOPE является динамической, но по своей природе она не итеративна. Инструкции, содержащиеся в инструкции SCOPE, выполняются один раз, но сам вложенный куб может определяться динамически. Пусть, например, создан куб SampleCube. К кубу SampleCube можно обратиться со следующей инструкцией SCOPE для определения вложенного куба, определяющего контекст, аналогичный ALLMEMBERS в измерении Measures.  
  
 `SCOPE([Measures].ALLMEMBERS);`  
  
 `THIS = [Measures].ALLMEMBERS.COUNT;`  
  
 `END SCOPE;`  
  
 Эти инструкции и выражения в инструкции SCOPE выполняются лишь один раз.  
  
 Пусть теперь пользователь обращается со следующим запросом многомерных выражений, содержащим одну меру ExistingMeasure, к кубу SampleCube.  
  
 `WITH MEMBER [Measures].[NewMeasure] AS '1'`  
  
 `SELECT`  
  
 `[Measures].ALLMEMBERS ON COLUMNS,`  
  
 `[Customer].DEFAULTMEMBER ON ROWS`  
  
 `FROM`  
  
 `[SampleCube]`  
  
 Возвращенный этим запросом набор ячеек примерно соответствует выводу, приведенному в следующей таблице.  
  
||[ExistingMeasure]|[NewMeasure]|  
|-|-------------------------|--------------------|  
|[Customer].[All]|2|2|  
  
 Обратите внимание, что в возвращаемом наборе ячеек значение ExistingMeasure, включенное в инструкцию SCOPE в данном скрипте многомерных выражений, динамически обновляется после определения меры NewMeasure.  
  
 Инструкция SCOPE может быть вложена в другую инструкцию SCOPE. Однако, поскольку инструкция SCOPE не является итеративной, главное назначение вложенных инструкций SCOPE — дальнейшее подразделение вложенного куба для последующей обработки.  
  
### <a name="scope-statement-example"></a>Пример инструкции SCOPE  
 В следующем примере скрипта многомерных выражений инструкция SCOPE используется для увеличения значения меры Amount в группе мер Finance образца куба [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] на 10 % для потомков элемента Redmond в измерении Customer. Однако этот вложенный куб далее изменяется следующей инструкцией SCOPE так, чтобы он включал в себя меру Amount для потомков 2002 календарного года. Затем мера Amount обрабатывается только для этого вложенного куба, оставляя статистические значения для меры Amount в других календарных годах без изменений.  
  
```  
/* Calculate the entire cube first. */  
CALCULATE;  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 Дополнительные сведения о синтаксисе инструкции SCOPE см. в разделе [Инструкция SCOPE (многомерные выражения)](../../../mdx/mdx-scripting-scope.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку многомерных выражений (многомерные выражения)](../../../mdx/mdx-language-reference-mdx.md)   
 [Базовый скрипт многомерных Выражений &#40; Многомерные Выражения &#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md)   
 [Основные принципы запросов многомерных выражений (службы Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
