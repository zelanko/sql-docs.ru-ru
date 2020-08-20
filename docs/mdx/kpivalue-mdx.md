---
description: KPIValue (многомерные выражения)
title: KPIValue (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 24189ffb3e9a550fd4819b15cfbd8ae41a48a64f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471816"
---
# <a name="kpivalue-mdx"></a>KPIValue (многомерные выражения)


  Возвращает элемент, вычисляющий значение указанного ключевого показателя эффективности (KPI).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
KPIValue(KPI_Name)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Название_КПЭ*  
 Допустимое строковое выражение, указывающее имя ключевого показателя эффективности.  
  
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
  
  
