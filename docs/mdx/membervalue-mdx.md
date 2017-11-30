---
title: "MemberValue (многомерные Выражения) | Документы Microsoft"
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
f1_keywords: MEMBERVALUE
dev_langs: kbMDX
helpviewer_keywords: MemberValue function
ms.assetid: f9b2af16-2b81-48e4-ae81-99f64e4bbc98
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2e3489ae5740b28f10a7aebed2b48d35d64c36da
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="membervalue-mdx"></a>MemberValue (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает значение элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.MemberValue  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, результатом вычисления которого является элемент.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение элемента содержит следующие сведения, перечисленные в том порядке, в котором они сообщаются в возвращаемом значении:  
  
-   Привязка значения, если она определена.  
  
-   Ключ с исходным типом данных, если нет привязки имени или ключ и заголовок привязаны к одному столбцу.  
  
-   Заголовок элемента.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается привязка значения, ключ элемента и заголовок первой даты в измерении Date куба Adventure Works.  
  
```  
WITH MEMBER Measures.ValueColumn as [Date].[Calendar].[July 1, 2001].MemberValue  
MEMBER Measures.KeyColumn as [Date].[Calendar].[July 1, 2001].Member_Key  
MEMBER Measures.NameColumn as [Date].[Calendar].[July 1, 2001].Member_Name  
  
SELECT {Measures.ValueColumn, Measures.KeyColumn, Measures.NameColumn}  ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
