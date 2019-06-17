---
title: DataMember (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 98b10c951043416280c05fd6a0e5eeb5df92c104
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248152"
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
  
## <a name="remarks"></a>Примечания  
 Эта функция работает с неконечными элементами любой иерархии и может использоваться [UPDATE CUBE Statement (MDX)](../mdx/mdx-data-manipulation-update-cube.md) для обратной записи данных непосредственно в неконечные элементы, а не в потомки конечных элементов.  
  
> [!NOTE]  
>  Возвращает указанный элемент, если он является конечным или если с неконечным элементом не связан элемент данных.  
  
## <a name="example"></a>Пример  
 В следующем примере используется **DataMember** функции в вычисляемой мере для отображения квоты продаж для каждого отдельного работника:  
  
```  
WITH MEMBER measures.InvidualQuota AS   
([Employee].[Employees].currentmember.datamember, [Measures].[Sales Amount Quota])  
,FORMAT_STRING='Currency'  
SELECT {[Measures].[Sales Amount Quota],[Measures].InvidualQuota} ON COLUMNS,  
[Employee].[Employees].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)   
 [Основные понятия многомерных выражений (службы Analysis Services)](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)  
  
  
