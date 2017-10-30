---
title: "LastPeriods (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LASTPERIODS
dev_langs:
- kbMDX
helpviewer_keywords:
- LastPeriods function
ms.assetid: a15df7a1-b261-48ed-aacc-d2804db8dbf7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dc24f14f734c697946226974a8d51761a6d8182e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="lastperiods-mdx"></a>LastPeriods (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает набор элементов до указанного элемента включительно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LastPeriods(Index [ ,Member_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Индекс*  
 Допустимое числовое выражение, указывающее число периодов.  
  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Замечания  
 Если указанное число периодов положительно, **LastPeriods** функция возвращает набор элементов, которые начинаются с элемента, отстающего *индекс* -1 от указанного выражения элемента и заканчивается указанным элементом. Число элементов, возвращаемых функцией равно *индекса*.  
  
 Если число периодов отрицательно, **LastPeriods** функция возвращает набор, начинающийся с указанного элемента и заканчивающийся элементом (- *индекс* - 1) из заданного элемента. Число элементов, возвращаемых функцией равно абсолютное значение *индекса*.  
  
 Если число периодов равно нулю, **LastPeriods** функция возвращает пустой набор. В отличие от **запаздывания** функции, которая возвращает указанный элемент, если указано значение 0.  
  
 Если элемент не указан, **LastPeriods** функция использует **Time.CurrentMember**. Если измерение маркировано как измерение времени, функция будет интерпретироваться и выполняться без ошибки, но приведет к ошибке ячейки в клиентском приложении.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается значение меры по умолчанию для второго, третьего и четвертого финансовых кварталов 2002 финансового года.  
  
```  
SELECT LastPeriods(3,[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]) ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  В этом примере могут также быть написаны с использованием: (двоеточие):  
>   
>  `[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]: [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2002]`  
  
 В следующем примере возвращается значение меры по умолчанию для первого квартала 2002 финансового года. Хотя указаны три финансовых периода, может быть возвращен только один, поскольку в финансовом году нет более ранних периодов.  
  
```  
SELECT LastPeriods  
   (3,[Date].[Fiscal].[Fiscal Quarter].[Q1 FY 2002]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

