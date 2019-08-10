---
title: DataMember (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4395f0ff113c8549ec2250d5fa87d37090627b3c
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892917"
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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)   
 [Основные понятия многомерных выражений (службы Analysis Services)](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services)  
  
  
