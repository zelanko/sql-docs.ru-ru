---
title: DrillupMember (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a0e0a46f45b0c5ef2d0b582ca3948f6a5e34474b
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578186"
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
  
## <a name="remarks"></a>Примечания  
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
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
