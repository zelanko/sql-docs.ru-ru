---
description: OR (многомерные выражения)
title: OR (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d5ea3e65dd9bad768ef829858d42d6e4adea7a72
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471756"
---
# <a name="or-mdx"></a>OR (многомерные выражения)


  Выполняет логическое сложение двух числовых выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Expression1 OR Expression2   
```  
  
#### <a name="parameters"></a>Параметры  
 Expression1  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
 Expression2  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, которое возвращает **true** , если один или оба аргумента имеют **значение true**; в противном случае — **значение false**.  
  
## <a name="remarks"></a>Комментарии  
 Оператор **или** обрабатывает оба аргумента как логические значения (ноль, 0, как **false**; в противном случае — **значение true**), прежде чем оператор выполняет логическое сложение. В следующей таблице показано, как оператор **or** выполняет логическое сложение.  
  
|*Expression1*|*Expression2*|Возвращаемое значение|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**true**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="example"></a>Пример  
 Следующий запрос содержит вычисляемую меру, которая возвращает строку «в БРАКе или пол», если текущий элемент в иерархии «Пол» измерения «Заказчик» имеет значение «пол» или текущий элемент в иерархии «семейное положение» измерения «Заказчик» находится в браке. в противном случае возвращается строка "не в БРАКе или гнездо".  
  
```  
WITH  
MEMBER MEASURES.ORDEMO AS  
IIF(  
([Customer].[Gender].CURRENTMEMBER IS [Customer].[Gender].&[M])  
OR  
([Customer].[Marital Status].CURRENTMEMBER IS [Customer].[Marital Status].&[M]),  
"MARRIED OR MALE",  
"UNMARRIED OR FEMALE")  
SELECT [Customer].[Gender].[Gender].MEMBERS ON 0,  
[Customer].[Marital Status].[Marital Status].MEMBERS ON 1  
FROM [Adventure Works]  
WHERE(MEASURES.ORDEMO)  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-operator-reference-mdx.md)  
  
  
