---
title: '* (Перекрестное соединение) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2f8377acec8f213c423de5d19d8859c8b3d93a06
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68047137"
---
# <a name="crossjoin----mdx-operator-reference"></a>Crossjoin - Справочник по операторам многомерных Выражений


  Выполняет операцию над наборами, возвращающую перекрестное произведение двух наборов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set_Expression * Set_Expression  
```  
  
## <a name="parameter"></a>Параметр  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Набор, содержащий перекрестное произведение обоих заданных наборов.  
  
## <a name="remarks"></a>Примечания  
 **\*(Перекрестное соединение)** оператор функционально эквивалентен [Crossjoin](../mdx/crossjoin-mdx.md) функции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется использование этого оператора.  
  
```  
-- This query returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
    [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Gross Profit Margin])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
