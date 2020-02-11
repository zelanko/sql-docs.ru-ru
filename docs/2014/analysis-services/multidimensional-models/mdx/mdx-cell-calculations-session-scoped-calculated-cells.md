---
title: Создание вычисляемых ячеек с областью действия сеанса | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- session-scoped calculated members [MDX]
ms.assetid: f2d14a89-6286-4e74-9afb-091076f93f21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4388ef278c0762184859162dc55f656aae1c9a15
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074430"
---
# <a name="creating-session-scoped-calculated-cells"></a>Создание вычисляемых ячеек с областью действия сеанса
    
> [!IMPORTANT]  
>  Этот синтаксис больше не используется. Вместо него используются присваивания языка многомерных выражений. Дополнительные сведения о присваиваниях см. в разделе [Базовый скрипт многомерных выражений (многомерные выражения)](the-basic-mdx-script-mdx.md).  
  
 Чтобы создать вычисляемые ячейки, доступные для всех запросов одного и того же сеанса, можно использовать инструкцию [CREATE CELL CALCULATION](/sql/mdx/mdx-data-definition-create-cell-calculation) или инструкцию [ALTER CUBE](/sql/mdx/mdx-data-definition-alter-cube) . Обе инструкции обеспечивают одинаковый результат.  
  
## <a name="create-cell-calculation-syntax"></a>Синтаксис CREATE CELL CALCULATION  
  
> [!IMPORTANT]  
>  Этот синтаксис больше не используется. Вместо него используются присваивания языка многомерных выражений. Дополнительные сведения о присваиваниях см. в разделе [Базовый скрипт многомерных выражений (многомерные выражения)](the-basic-mdx-script-mdx.md).  
  
 Чтобы определить вычисляемую ячейку с областью действия сеанса с помощью инструкции CREATE CELL CALCULATION, используется следующий синтаксис:  
  
```  
CREATE CELL CALCULATION Cube_Expression.<CREATE CELL CALCULATION body clause>  
  
<CREATE CELL CALCULATION body clause> ::=CellCalc_Identifier FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
## <a name="alter-cube-syntax"></a>Синтаксис ALTER CUBE  
  
> [!IMPORTANT]  
>  Этот синтаксис больше не используется. Вместо него используются присваивания языка многомерных выражений. Дополнительные сведения о присваиваниях см. в разделе [Базовый скрипт многомерных выражений (многомерные выражения)](the-basic-mdx-script-mdx.md).  
  
 Для определения вычисляемой ячейки с областью действия сеанса с помощью инструкции ALTER CUBE используется следующий синтаксис:  
  
```  
ALTER CUBE Cube_Identifier CREATE CELL CALCULATION  
FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
 Значение выражения `String_Expression` содержит список ортогональных многомерных выражений набора с одним измерением, каждое из которых должно приводиться к одной из следующих категорий наборов:  
  
|Категория|Description|  
|--------------|-----------------|  
|Пустой набор|Выражение набора многомерных выражений, которое разрешается к пустому набору. В этом случае областью вычисляемой ячейки является весь куб.|  
|Одноэлементный набор|Выражение набора многомерных выражений, которое разрешается к единственному элементу.|  
|Набор элементов уровня|Выражение набора многомерных выражений, которое разрешается к элементам одного уровня. Примером этого является *Level_Expression*.`Members` Функция многомерных выражений. Чтобы включить вычисляемые элементы, используйте *Level_Expression*.`AllMembers` Функция многомерных выражений.<br /><br /> Дополнительные сведения см. в разделе [AllMembers (многомерные выражения)](/sql/mdx/allmembers-mdx).|  
|Набор потомков|Выражение набора многомерных выражений, которое разрешается к потомкам одного элемента. Примером этого является функция многомерных `Descendants`выражений (*Member_Expression*, *Level_Expression*, *Desc_Flag*).<br /><br /> Дополнительные сведения см. в разделе [Descendants (многомерные выражения)](/sql/mdx/descendants-mdx).|  
  
## <a name="see-also"></a>См. также:  
 [Создание вычислений ячеек в МНОГОМЕРных выражениях &#40;многомерных выражениях&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
