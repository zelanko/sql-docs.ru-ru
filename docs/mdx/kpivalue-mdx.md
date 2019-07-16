---
title: KPIValue (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c34e5b345ee0e4d780de66449473237cc413ace6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905856"
---
# <a name="kpivalue-mdx"></a>KPIValue (многомерные выражения)


  Возвращает элемент, вычисляющий значение указанного ключевого показателя эффективности (KPI).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
KPIValue(KPI_Name)  
```  
  
## <a name="arguments"></a>Аргументы  
 *KPI_Name*  
 Допустимое строковое выражение, указывающее имя ключевого показателя эффективности.  
  
## <a name="remarks"></a>Примечания  
  
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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
