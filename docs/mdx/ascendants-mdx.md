---
title: "Ascendants (многомерные Выражения) | Документы Microsoft"
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
- ASCENDANTS
dev_langs:
- kbMDX
helpviewer_keywords:
- Ascendants function
ms.assetid: a2baf4a2-7d66-4766-b708-739a3c21b09e
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a290643abeb55db3a2c7091976731af9dbb200ff
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="ascendants-mdx"></a>Ascendants (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает набор родителей указанного элемента, включая его самого.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Ascendants(Member_Expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Замечания  
 **Предки** функция возвращает всех предков элемента из элемента до верхнего элемента в иерархии; в частности, он выполняет обход в обратном порядке иерархии указанного элемента и затем возвращает все родительские элементы связан с элементом, включая его самого, в наборе. Это отличается от [предка](../mdx/ancestor-mdx.md) функции, которая возвращает указанный родительский элемент или предок указанного уровня.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается количество заказов посредников для `[Sales Territory].[Northwest]` элемента и всех его предков этого члена из **Adventure Works** куба. **Предки** функция создает набор, который содержит `[Sales Territory].[Northwest]` и всех его предков по оси ROWS.  
  
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
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

