---
title: KPIGoal (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f818731fdc2d7b7b6ee6b000fd4e85b150c9f92c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68105242"
---
# <a name="kpigoal-mdx"></a>KPIGoal (многомерные выражения)


  Возвращает элемент, вычисляющий значение цели указанного ключевого показателя эффективности (KPI).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
KPIGoal(KPI_Name)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Название_КПЭ*  
 Допустимое строковое выражение, представляющее собой имя ключевого показателя эффективности.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="example"></a>Пример  
 В следующем примере возвращаются значение, цель, состояние и тренд ключевого показателя эффективности для меры доходов от продаж через партнерскую сеть для потомков трех элементов иерархии атрибута Fiscal Year.  
  
```  
SELECT  
   { KPIValue("Channel Revenue"),   
     KPIGoal("Channel Revenue"),  
     KPIStatus("Channel Revenue"),   
     KPITrend("Channel Revenue")  
   } ON Columns,  
Descendants  
   ( { [Date].[Fiscal].[Fiscal Year].&[2002],  
       [Date].[Fiscal].[Fiscal Year].&[2003],  
       [Date].[Fiscal].[Fiscal Year].&[2004]   
     }, [Date].[Fiscal].[Fiscal Quarter]  
   ) ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
