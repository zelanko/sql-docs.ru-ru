---
title: "Инструкция SCOPE (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: SCOPE
dev_langs: kbMDX
helpviewer_keywords:
- scope [MDX]
- SCOPE statement
ms.assetid: ceab459d-b601-4468-b3fc-4f5bb4a1805f
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 9487e1e71916e07232eed6ee7f60c013f9598197
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="mdx-scripting---scope"></a>Скрипты многомерных Выражений: область действия
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Замечания  
 Инструкция SCOPE определяет вложенный куб, на который будет распространяться действие одной или нескольких инструкций многомерных выражений. Если инструкция многомерных выражений не ограничена инструкцией SCOPE, то неявной областью инструкции является весь куб.  
  
> [!NOTE]  
>  Скрытые элементы появляются в инструкциях SCOPE.  
  
 Инструкции SCOPE создают вложенные кубы, в которых видны «пустоты», независимо от **MDX Compatibility** параметр. Например, инструкция `Scope( Customer.State.members )` может включать штаты в тех странах или регионах, которые не имеют штатов, но содержат элементы-заполнители для штатов, невидимые в остальных случаях.  
  
 Действие инструкции SCOPE не распространяется на вычисляемые элементы и именованные наборы, созданные в этой инструкции SCOPE.  
  
## <a name="example"></a>Пример  
 Приведенный ниже в скрипте вычисления многомерного Выражения в образце решения Adventure Works, определяет область текущего как финансовый квартал 2005 финансового года и мера квоты суммы продаж, а затем присваивает значение ячейки в текущей области видимости с помощью **ParallelPeriod** функции. В примере затем изменяет область с помощью другой инструкции SCOPE, а затем выполняет другой с помощью назначения [This (MDX)](../mdx/this-mdx.md) функции.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Инструкции сценариев многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
