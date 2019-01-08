---
title: Ascendants (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3122b3aa2f53da69f88e6ffad508f12c8e10da1c
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52404349"
---
# <a name="ascendants-mdx"></a>Ascendants (многомерные выражения)


  Возвращает набор родителей указанного элемента, включая его самого.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Ascendants(Member_Expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 **Предки** функция возвращает всех предков элемента из данного элемента до верхней части элемента в иерархии; в частности, он выполняет обход в обратном порядке в иерархии для указанного члена, а затем Возвращает все родительские элементы связан с элементом, включая его самого, в наборе. Это отличается от [предка](../mdx/ancestor-mdx.md) функцию, которая возвращает указанный родительский элемент или предок на определенном уровне.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается количество заказов посредников для `[Sales Territory].[Northwest]` элемент и все его родители из этого члена из **Adventure Works** куба. **Ascendants** функция создает набор, который содержит `[Sales Territory].[Northwest]` члена и его родителей по оси СТРОК.  
  
```  
SELECT  
   Measures.[Reseller Order Count] ON COLUMNS,  
   Order(  
      Ascendants(  
         [Sales Territory].[Northwest]  
      ),  
      DESC  
   ) ON ROWS  
FROM  
   [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
