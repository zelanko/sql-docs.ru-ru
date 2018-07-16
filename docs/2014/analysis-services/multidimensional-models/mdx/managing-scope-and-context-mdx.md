---
title: Управление областью и контекстом (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], context
- scope [MDX]
- CALCULATE statement
- This function [MDX]
- SCOPE statement
- scripts [MDX], scope
ms.assetid: 631e7c20-8be9-4c35-8609-76516aef19d1
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 28d50024f2419ab3ee135aede45abc7243ec5084
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37288040"
---
# <a name="managing-scope-and-context-mdx"></a>Управление областью и контекстом (многомерные выражения)
  В службах [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]скрипты многомерных выражений могут распространяться на весь куб или на его отдельные участки в особых точках при выполнении скрипта. В скриптах многомерных выражений используется многоуровневый подход к вычислениям в кубе при помощи этапов вычисления.  
  
> [!NOTE]  
>  Дополнительные сведения о влиянии этапов вычисления на сами вычисления см. в разделе [Основные сведения о порядке этапов и порядке вычисления (многомерные выражения)](mdx-data-manipulation-understanding-pass-order-and-solve-order.md).  
  
 Чтобы управлять вычислений, областью и контекстом в скриптах многомерных Выражений, в частности использовать применяются инструкция CACULATE, `This` функции и инструкция SCOPE.  
  
## <a name="using-the-calculate-statement"></a>Инструкция CALCULATE  
 Инструкция CALCULATE заполняет каждую ячейку в кубе статистическими данными. Например, скрипт многомерных выражений по умолчанию содержит одну инструкцию CALCULATE в начале.  
  
 Дополнительные сведения о синтаксисе инструкции CALCULATE см. в разделе [Инструкция CALCULATE (многомерные выражения)](/sql/mdx/mdx-scripting-calculate).  
  
> [!NOTE]  
>  Если скрипт содержит инструкцию SCOPE, содержащую в себе инструкцию CALCULATE, в многомерных выражениях инструкция CALCULATE вычисляется в рамках контекста вложенного куба, определенного инструкцией SCOPE, а не для всего куба.  
  
## <a name="using-the-this-function"></a>Функция This  
 Функция `This` позволяет обратиться к текущему вложенному кубу в рамках скрипта многомерных выражений. Можно использовать `This` функции, чтобы быстро заполнить ячейки в текущем вложенном кубе Многомерным выражением. Часто используют `This` функция в сочетании с инструкцией SCOPE для изменения содержимого конкретного вложенного куба на определенном этапе вычислений.  
  
> [!NOTE]  
>  Если скрипт содержит инструкцию SCOPE, содержащая `This` функции, многомерное Выражение вычисляет `This` функции в рамках контекста вложенного куба, определенного инструкцией SCOPE, а не для всего куба.  
  
### <a name="this-function-example"></a>Пример функции This  
 В следующем примере команд скрипта многомерных Выражений используется `This` функции для увеличения значения меры Amount в группе мер Finance [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] образца куба на 10% для потомков элемента Redmond в измерении «Заказчик»:  
  
```  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 Дополнительные сведения о синтаксисе `This` функции, см. в разделе [это &#40;многомерных Выражений&#41;](/sql/mdx/this-mdx).  
  
## <a name="using-the-scope-statement"></a>Инструкция SCOPE  
 Инструкция SCOPE определяет текущий вложенный куб, содержащий другие выражения и инструкции многомерных выражений и определяющий для них область в рамках скрипта многомерных выражений. В многомерных выражениях эти другие выражения и многомерные инструкции, включая функцию `This` и инструкцию CALCULATE, вычисляются в контексте данного вложенного куба.  
  
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
  
 Дополнительные сведения о синтаксисе инструкции SCOPE см. в разделе [Инструкция SCOPE (многомерные выражения)](/sql/mdx/mdx-scripting-scope).  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку многомерных Выражений &#40;многомерных Выражений&#41;](/sql/mdx/mdx-language-reference-mdx)   
 [Базовый скрипт многомерных Выражений &#40;многомерных Выражений&#41;](the-basic-mdx-script-mdx.md)   
 [Основные принципы запросов многомерных Выражений &#40;служб Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
