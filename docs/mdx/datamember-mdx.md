---
description: DataMember (многомерные выражения)
title: DataMember (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7291a8d2c57d4a996893146e8e855df234ed0139
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88413140"
---
# <a name="datamember-mdx"></a>DataMember (многомерные выражения)


  Возвращает элемент данных, сформированный системой и связанный с неконечным элементом измерения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.DataMember  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Remarks  
 Эта функция работает с неконечными элементами в любой иерархии и может использоваться командой [инструкции UPDATE CUBE (многомерные выражения)](../mdx/mdx-data-manipulation-update-cube.md) для обратной записи данных непосредственно в неконечный элемент, а не на потомков конечного элемента.  
  
> [!NOTE]  
>  Возвращает указанный элемент, если он является конечным или если с неконечным элементом не связан элемент данных.  
  
## <a name="example"></a>Пример  
 В следующем примере функция **DataMember** в вычисляемой мере используется для отображения квоты продаж для каждого отдельного сотрудника:  
  
```  
WITH MEMBER measures.InvidualQuota AS   
([Employee].[Employees].currentmember.datamember, [Measures].[Sales Amount Quota])  
,FORMAT_STRING='Currency'  
SELECT {[Measures].[Sales Amount Quota],[Measures].InvidualQuota} ON COLUMNS,  
[Employee].[Employees].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-function-reference-mdx.md)   
 [Основные понятия многомерных выражений (службы Analysis Services)](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services)  
  
  
