---
description: Определение данных многомерных выражений — ALTER CUBE
title: Инструкция ALTER CUBE (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 052d533e503f5b82f506ec119684acbbfe7cdd5f
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92192354"
---
# <a name="mdx-data-definition---alter-cube"></a>Определение данных многомерных выражений — ALTER CUBE


  Изменяет структуру указанного куба. Обычно используется для поддержки обратной записи в измерении. Дополнительные сведения об использовании обратной записи в приложении см. в этой записи блога: [Создание приложения обратной записи с помощью Analysis Services (блог)](/archive/blogs/data_otaku/building-a-writeback-application-with-analysis-services)  
  
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
  
 *MemberName*  
 Допустимое строковое выражение, возвращающее имя элемента.  
  
 *Key_Value*  
 Допустимое скалярное выражение, определяющее ключевое значение нового элемента измерения.  
  
 *Property_Name*  
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
  
### <a name="remarks"></a>Remarks  
 Если предложение WITH DESCENDANTS не используется, потомки удаляемого элемента становятся потомками его родителя. Если предложение WITH DESCENDANTS указывается, вместе с элементом удаляются все потомки и соответствующие строки в таблице измерения.  
  
> [!NOTE]  
>  Сведения о том, как удалять вычисляемые элементы, именованные наборы, действия и вычисления ячеек, см. в разделе [инструкция DROP MEMBER &#40;&#41;многомерных выражений ](../mdx/mdx-data-definition-drop-member.md), инструкция drop [Set &#40;&#41;многомерных ](../mdx/mdx-data-definition-drop-set.md)выражений, [инструкция DROP Action &#40;многомерное ](../mdx/mdx-data-definition-drop-action.md)выражение&#41;&#40;[MDX&#41;](../mdx/mdx-data-definition-drop-cell-calculation.md).  
  
## <a name="updating-the-default-dimension-member"></a>Обновление элемента измерения по умолчанию  
 Это предложение обновляет элемент по умолчанию куба и применяется в скриптах вычисления многомерных выражений для определения элемента по умолчанию. Элемент по умолчанию может быть указан в измерении базы данных, измерении куба или для имени входа пользователя. Элемент по умолчанию можно менять во время сеанса.  
  
### <a name="arguments"></a>Аргументы  
 *Dimension_Name*  
 Допустимое строковое выражение, обозначающее имя измерения.  
  
 *MDX_Expression*  
 Допустимое многомерное выражение, возвращающее один элемент.  
  
### <a name="remarks"></a>Remarks  
 Заданное многомерное выражение может быть статическим или динамическим.  
  
## <a name="moving-a-dimension-member"></a>Перемещение элемента измерения  
 Строка изменяется в таблице базового измерения.  
  
### <a name="arguments"></a>Аргументы  
 *ParentName*  
 Допустимое строковое выражение, обозначающее нового родителя перемещаемого элемента измерения.  
  
 *MemberName*  
 Допустимое строковое выражение, возвращающее имя элемента.  
  
 Unsigned_*целое число*  
 Допустимое число, обозначающее количество уровней, которые нужно пропустить.  
  
 Если указывается предложение WITH DESCENDANTS, перемещается все дерево. Если предложение WITH DESCENDANTS не указывается, потомки перемещаемого элемента становятся потомками его родителя. Эффект перемещения выражается в простом обновлении значений в родительском ключевом столбце в таблице базового измерения.  
  
## <a name="updating-a-dimension-member"></a>Обновление элемента измерения  
 Предложение UPDATE DIMENSION MEMBER позволяет изменять свойства элемента, а также связанную с ним нестандартную формулу элемента.  
  
### <a name="arguments"></a>Аргументы  
 *MemberName*  
 Допустимое строковое выражение, возвращающее имя элемента.  
  
 *MDX_Expression*  
 Допустимое многомерное выражение, возвращающее один элемент.  
  
 *Property_Value*  
 Допустимое скалярное многомерное выражение, определяющее значение свойства вычисляемого элемента.  
  
## <a name="creating-a-cell-calculation"></a>Создание вычисления ячейки  
 Дополнительные сведения о создании вычисления ячейки с помощью инструкции ALTER CUBE см. в разделе [Drop Cell Structure statement &#40;&#41;многомерных выражений ](../mdx/mdx-data-definition-drop-cell-calculation.md).  
  
## <a name="see-also"></a>См. также:  
 [Инструкции определения данных многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-data-definition-statements-mdx.md)  
  
