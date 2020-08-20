---
description: Siblings (многомерные выражения)
title: Одноуровневые элементы (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cfced6c9fb760903ef93a26e8e417df3d6cabd40
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500437"
---
# <a name="siblings-mdx"></a>Siblings (многомерные выражения)


  Возвращает элементы, имеющие общего родителя с указанным элементом, включая сам элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.Siblings   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
### <a name="example"></a>Пример  
 В следующем примере возвращается мера по умолчанию для элементов с общим родителем «Март 2003» (такими элементами являются «Январь 2003», «Февраль 2003») и самого элемента «Март 2003».  
  
```  
SELECT [Date].[Calendar].[Month].[March 2003].Siblings ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
