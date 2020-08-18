---
description: Ascendants (многомерные выражения)
title: Предков (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eb485e2785facba4a47647f8a51548e0140b3efb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491470"
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
  
## <a name="remarks"></a>Remarks  
 Функция **предков** возвращает все предки элемента из самого элемента в верхнюю часть иерархии элемента. в частности, он выполняет обход иерархии для указанного элемента, а затем возвращает все элементы по возрастанию, связанные с элементом, включая самого себя, в набор. Это отличается от функции- [предка](../mdx/ancestor-mdx.md) , которая возвращает конкретный элемент Ascend или ancestor на определенном уровне.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается число заказов торгового посредника для `[Sales Territory].[Northwest]` элемента и все предков этого элемента из куба **Adventure Works** . Функция **предков** конструирует набор, включающий `[Sales Territory].[Northwest]` элемент и его предков для оси ROWS.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
