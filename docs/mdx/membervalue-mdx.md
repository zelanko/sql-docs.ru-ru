---
title: MemberValue (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 73a54986a951095b16465cd4934b4dfd447d38bb
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742173"
---
# <a name="membervalue-mdx"></a>MemberValue (многомерные выражения)


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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
