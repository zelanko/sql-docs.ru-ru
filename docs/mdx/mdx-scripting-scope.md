---
title: Инструкция SCOPE (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2f355842999b505a97c3387ab9e51d3b651c3b7c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138283"
---
# <a name="mdx-scripting---scope"></a>Сценарии многомерных выражений — SCOPE


  Ограничивает область заданных инструкций многомерных выражений указанным вложенным кубом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SCOPE(Subcube_Expression)   
   [ MDX_Statement ]  
END SCOPE  
  
Subcube_Expression ::=(Auxiliary_Subcube [, Auxiliary_Subcube,...n])  
  
Auxiliary_Subcube ::=   
        Limited_Set   
    | Root([dimension_name])   
    | Leaves([dimension_name])  
  
Limited_Set ::=   
        single_tuple   
    | member   
    | Common_Grain_Members   
    | hierarchy.members   
    | level.members   
    | {}   
    | Descendants  
            (  
                  Member  
         , [level  
         [  
            , SELF   
             | AFTER   
                          | BEFORE   
                          | SELF_AND_AFTER   
                          | SELF_AND_BEFORE   
                          | SELF_BEFORE_AFTER   
                          | LEAVES  
                  ]  
            )   
[* <limited set>]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Subcube_Expression*  
 Допустимое многомерное выражение вложенного куба.  
  
 *MDX_Statement*  
 Допустимая инструкция многомерных выражений.  
  
 *Common_Grain_Members*  
 Допустимая инструкция многомерных выражений, принимающая значение элементов с одинаковой детализацией.  
  
 *single_tuple*  
 Один кортеж.  
  
## <a name="remarks"></a>Примечания  
 Инструкция SCOPE определяет вложенный куб, на который будет распространяться действие одной или нескольких инструкций многомерных выражений. Если инструкция многомерных выражений не ограничена инструкцией SCOPE, то неявной областью инструкции является весь куб.  
  
> [!NOTE]  
>  Скрытые элементы появляются в инструкциях SCOPE.  
  
 Инструкции SCOPE создают вложенные кубы, предоставлять «дыры» вне зависимости от **MDX Compatibility** параметр. Например, инструкция `Scope( Customer.State.members )` может включать штаты в тех странах или регионах, которые не имеют штатов, но содержат элементы-заполнители для штатов, невидимые в остальных случаях.  
  
 Действие инструкции SCOPE не распространяется на вычисляемые элементы и именованные наборы, созданные в этой инструкции SCOPE.  
  
## <a name="example"></a>Пример  
 В следующем примере, из скрипта вычисления многомерных Выражений в Adventure Works образец решения, текущая область определяется как финансовый квартал 2005 финансового года и мера квоты суммы продаж и затем присваивает значение ячейки в текущей области, используя  **ParallelPeriod** функции. В примере затем изменяет область с помощью другой инструкции SCOPE, а затем выполняет другой с помощью назначения [This (MDX)](../mdx/this-mdx.md) функции.  
  
```  
Scope   
 (   
    [Date].[Fiscal Year].&[2005],  
    [Date].[Fiscal].[Fiscal Quarter].Members,  
    [Measures].[Sales Amount Quota]  
 ) ;     
  
   This = ParallelPeriod                               
          (   
             [Date].[Fiscal].[Fiscal Year], 1,  
             [Date].[Fiscal].CurrentMember   
          ) * 1.35 ;  
  
/*-- Allocate equally to months in FY 2002 -----------------------------*/  
  
  Scope   
  (   
     [Date].[Fiscal Year].&[2002],  
     [Date].[Fiscal].[Month].Members   
  ) ;     
  
    This = [Date].[Fiscal].CurrentMember.Parent / 3 ;     
  
  End Scope ;     
End Scope ;     
```  
  
## <a name="see-also"></a>См. также  
 [Инструкции для создания скриптов многомерных выражений (многомерные выражения)](../mdx/mdx-scripting-statements-mdx.md)  
  
  
