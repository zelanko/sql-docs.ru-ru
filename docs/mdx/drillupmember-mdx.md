---
title: DrillupMember (многомерные Выражения) | Документы Microsoft
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
- DRILLUPMEMBER
dev_langs:
- kbMDX
helpviewer_keywords:
- DrillupMember function
ms.assetid: debcd966-ea4e-4ecf-8600-0a4d346d03f8
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 156a26cfbfb8812c93d8850313d6f73482021cd5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="drillupmember-mdx"></a>DrillupMember (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает элементы указанного набора, которые не являются потомками элементов второго заданного набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DrillupMember(Set_Expression1, Set_Expression2)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Set_Expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Замечания  
 **DrillupMember** функция возвращает набор элементов, основывающихся на элементах, заданных в первом наборе и являющихся потомками элементов второго набора. Первый набор может иметь любую размерность, но второй набор должен быть одномерным. Порядок среди исходных элементов первого набора сохраняется. Функция формирует набор путем включения в него только тех элементов набора, которые являются прямыми потомками элементов набора. Если прямой предок элемента первого набора не представлен во втором наборе, то элемент первого набора включается в набор, возвращаемый этой функцией. Потомки первого набора, предшествующие предку элемента второго набора, также включаются.  
  
 Первый набор может содержать кортежи вместо элементов. Углубленная детализация кортежей является расширением OLE DB и возвращает набор кортежей вместо набора элементов.  
  
> [!IMPORTANT]  
>  Элемент должен быть обобщен, только если за ним непосредственно следует потомок. Порядок элементов в наборе значим для обоих углубленную детализацию\* и Drillup\* семейства функций. Рассмотрите возможность использования **Hierarchize** функцию для упорядочивания элементов первого набора.  
  
## <a name="example"></a>Пример  
 Следующие три примера идентичны, за исключением второго набора. В первом примере вторым набором являются США. В результате Колорадо исключается из результирующего набора. Он является потомком США.  
  
```  
SELECT DrillUpMember (   
  { [Geography].[Geography].[Country].[Canada]   
   ,[Geography].[Geography].[Country].[United States]   
   ,[Geography].[Geography].[State-Province].[Colorado]   
   ,[Geography].[Geography].[State-Province].[Alberta]   
   ,[Geography].[Geography].[State-Province].[Brunswick]    
 }   
 , {[Geography].[Geography].[Country].[United States]}   
 ) ON 0   
FROM [Adventure Works]  
```  
  
 Второй пример показывает важность порядка элементов. Поскольку **DrillupMember** обобщением только для тех элементов, которые являются прямых потомков в первом наборе, он не выполняет детализацию обобщением элемент Canada. Канаду отделяются от ее потомков США и Колорадо. Если изменить порядок элементов таким образом, что Канада окажется непосредственно над Альбертой, то Альберта и Брунсвик исключаются из набора строк.  
  
```  
SELECT DrillUpMember (   
 {  [Geography].[Geography].[Country].[Canada]   
   ,[Geography].[Geography].[Country].[United States]   
   ,[Geography].[Geography].[State-Province].[Colorado]   
   ,[Geography].[Geography].[State-Province].[Alberta]   
   ,[Geography].[Geography].[State-Province].[Brunswick]    
 }   
 , {[Geography].[Geography].[Country].[Canada]}   
 )   
ON 0   
FROM [Adventure Works]  
```  
  
 Третий пример показывает способ использования **Hierarchize** может компенсировать влияние порядка элементов и обобщением элемент Canada.  
  
```  
SELECT DrillUpMember (   
 Hierarchize   
  (   
   { [Geography].[Geography].[Country].[Canada]   
    ,[Geography].[Geography].[Country].[United States]   
    ,[Geography].[Geography].[State-Province].[Colorado]   
    ,[Geography].[Geography].[State-Province].[Alberta]   
    ,[Geography].[Geography].[State-Province].[Brunswick]    
   }   
  ), {[Geography].[Geography].[Country].[Canada]}   
 )   
ON 0   
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
