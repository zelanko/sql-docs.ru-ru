---
title: ALTER CUBE, инструкция (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Cube
- ALTER_CUBE
- ALTER CUBE
- ALTER
dev_langs:
- kbMDX
helpviewer_keywords:
- ALTER CUBE statement
- cubes [Analysis Services], modifying
- modifying cubes
ms.assetid: 2f0af61b-f509-4e1a-990f-20a215d22994
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 1db5a0a41669c97728cdb12107d18b0467481a42
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition---alter-cube"></a>Определения данных многомерных Выражений — ALTER CUBE
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Изменяет структуру указанного куба. Обычно используется для поддержки обратной записи в измерении. Дополнительные сведения об использовании обратной записи в приложении см. в записи блога: [Создание приложения обратной записи со службами Analysis Services (блог)](http://go.microsoft.com/fwlink/?LinkId=394977)  
  
 Обратите внимание, что результатом параллельной обратной записи в измерении является взаимоблокировка, когда фиксация первой обратной записи блокируется из-за совмещаемой блокировки, удерживаемой второй обратной записью. В этой ситуации не выдается никакого сообщения об ошибке, при этом продолжение ни одной из операций невозможно. Впоследствии истекает время ожидания обеих операций и выполняется их откат.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER CUBE  
      Cube_Name | CURRENTCUBE  
      <alter clause>   
            [ < alter clause> ...n]  
  
< alter clause> ::=   
   <create dimension member clause>   
  | <remove dimension member clause>  
  | <move dimension member clause>   
    | <update clause>   
    | <create cell calculation clause>  
  
<create dimension member clause> ::=  
CREATE DIMENSION MEMBER [ParentName.]MemberName  
    , [[KEY = Key_Value]   
    | [Property_Name = Property_Value[, ...n]]  
  
<dropping clause>::=  
DROP   
      DIMENSION MEMBER Member_Name   
            Member_Name ...n ]   
      [WITH DESCENDANTS]  
      | [ SESSION ] [ CALCULATED ] MEMBER Member_Name   
                  [ ,Member_Name,...n ]   
    | SET Set_Name  
                  [ ,Set_Name,...n ]   
    | [ SESSION ] CELL CALCULATION CellCalc_Name  
                  [ ,CellCalc_Name,...n ]   
    | ACTION Action_Name  
  
<move dimension member clause> ::=  
MOVE DIMENSION MEMBER MemberName  
        [, SKIPPED_LEVELS = Unsigned_Integer]   
      [WITH DESCENDANTS]  
    UNDER ParentName      
  
<update clause> ::=  
UPDATE   
    CUSTOM ROLLUP FOR MEMBER MemberName  
      [,MemberName, ...n] AS MDX_Expression  
   | DIMENSION Dimension_Name | Hierarchy_Name  
      , DEFAULT_MEMBER = MDX_Expression  
   | DIMENSION MEMBER MemberName AS  
   [MDX_Expression]  
   [Property_Name = Property_Value[, ...n]]  
  
<create cell calculation clause>::=  
CELL CALCULATION Calculation_Name   
   FOR Set_Expression AS MDX_Expression   
            [ [ CONDITION = 'Logical_Expression' ]   
    | [ DISABLED = { TRUE | FALSE } ]   
    | [ DESCRIPTION =String ]   
    | [ CALCULATION_PASS_NUMBER = Integer]   
    | [ CALCULATION_PASS_DEPTH = Integer]   
    | [ SOLVE_ORDER = Integer]   
    | [ Calculation_Name= Scalar_Expression ], ...n]  
```  
  
## <a name="creating-a-dimension-member"></a>Создание элемента измерения  
 Новая строка добавляется в таблицу базового измерения.  
  
### <a name="arguments"></a>Аргументы  
 *ParentName*  
 Допустимое строковое выражение, обозначающее имя родителя нового элемента измерения (если только не создается корневой элемент измерения).  
  
 *Имя пользователя*  
 Допустимое строковое выражение, возвращающее имя элемента.  
  
 *Key_Value*  
 Допустимое скалярное выражение, определяющее ключевое значение нового элемента измерения.  
  
 *Property_name*  
 Допустимый идентификатор многомерных выражений, обозначающий свойство элемента.  
  
 *Property_Value*  
 Допустимое скалярное многомерное выражение, определяющее значение свойства вычисляемого элемента.  
  
## <a name="dropping-a-dimension-member"></a>Удаление элемента измерения  
 При удалении элемента измерения из доступного для записи измерения удаляется сам элемент и соответствующая строка в таблице базового измерения.  
  
### <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимое строковое выражение, обозначающее имя куба.  
  
 *Member_Name*  
 Допустимое строковое выражение, обозначающее имя или ключ элемента.  
  
### <a name="remarks"></a>Замечания  
 Если предложение WITH DESCENDANTS не используется, потомки удаляемого элемента становятся потомками его родителя. Если предложение WITH DESCENDANTS указывается, вместе с элементом удаляются все потомки и соответствующие строки в таблице измерения.  
  
> [!NOTE]  
>  Сведения об удалении вычисляемых элементов, именованных наборов, действий и вычислений ячеек см. в разделе [инструкция DROP MEMBER &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-drop-member.md), [инструкция DROP SET &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-drop-set.md), [ACTION, инструкция DROP &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-drop-action.md), и [ВЫЧИСЛЕНИЯ инструкции DROP ЯЧЕЙКИ &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-drop-cell-calculation.md).  
  
## <a name="updating-the-default-dimension-member"></a>Обновление элемента измерения по умолчанию  
 Это предложение обновляет элемент по умолчанию куба и применяется в скриптах вычисления многомерных выражений для определения элемента по умолчанию. Элемент по умолчанию может быть указан в измерении базы данных, измерении куба или для имени входа пользователя. Элемент по умолчанию можно менять во время сеанса.  
  
### <a name="arguments"></a>Аргументы  
 *Dimension_Name*  
 Допустимое строковое выражение, обозначающее имя измерения.  
  
 *MDX_Expression*  
 Допустимое многомерное выражение, возвращающее один элемент.  
  
### <a name="remarks"></a>Замечания  
 Заданное многомерное выражение может быть статическим или динамическим.  
  
## <a name="moving-a-dimension-member"></a>Перемещение элемента измерения  
 Строка изменяется в таблице базового измерения.  
  
### <a name="arguments"></a>Аргументы  
 *ParentName*  
 Допустимое строковое выражение, обозначающее нового родителя перемещаемого элемента измерения.  
  
 *Имя пользователя*  
 Допустимое строковое выражение, возвращающее имя элемента.  
  
 Unsigned_*целое число со знаком*  
 Допустимое число, обозначающее количество уровней, которые нужно пропустить.  
  
 Если указывается предложение WITH DESCENDANTS, перемещается все дерево. Если предложение WITH DESCENDANTS не указывается, потомки перемещаемого элемента становятся потомками его родителя. Эффект перемещения выражается в простом обновлении значений в родительском ключевом столбце в таблице базового измерения.  
  
## <a name="updating-a-dimension-member"></a>Обновление элемента измерения  
 Предложение UPDATE DIMENSION MEMBER позволяет изменять свойства элемента, а также связанную с ним нестандартную формулу элемента.  
  
### <a name="arguments"></a>Аргументы  
 *Имя пользователя*  
 Допустимое строковое выражение, возвращающее имя элемента.  
  
 *MDX_Expression*  
 Допустимое многомерное выражение, возвращающее один элемент.  
  
 *Property_Value*  
 Допустимое скалярное многомерное выражение, определяющее значение свойства вычисляемого элемента.  
  
## <a name="creating-a-cell-calculation"></a>Создание вычисления ячейки  
 Дополнительные сведения о создании вычисления ячейки при помощи инструкции ALTER CUBE см. в разделе [инструкции DROP для ВЫЧИСЛЕНИЯ ЯЧЕЙКИ &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-drop-cell-calculation.md).  
  
## <a name="see-also"></a>См. также  
 [Инструкции определения данных многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
