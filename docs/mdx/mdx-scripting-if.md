---
title: "Если инструкция (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- statements [MDX], IF
ms.assetid: 8830cce5-9e06-4f89-a555-295bb0d0a8a1
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1d29f1f62214f669367aed255699825ccac0b6ee
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-scripting---if"></a>Скрипты многомерных Выражений: Если
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выполняет инструкцию, если условие истинно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IF expression THEN assignment END IF  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Многомерное выражение, принимающее логическое значение TRUE или FALSE.  
  
 *Назначение*  
 Многомерное выражение, присваивающее значение вложенному кубу или вычисляемому свойству.  
  
## <a name="remarks"></a>Замечания  
 Используйте инструкцию IF для потока управления, который в отличие от [IIf &#40; Многомерные Выражения &#41; ](../mdx/iif-mdx.md) функции и [инструкции CASE &#40; Многомерные Выражения &#41; ](../mdx/case-statement-mdx.md) , может использоваться только для возвращения значений или объектов.  
  
## <a name="examples"></a>Примеры  
 В следующем примере область ограничена уровнем «Страна» иерархии «География заказчика» в измерении «Заказчики». Если текущая мера — это «Сумма продаж через Интернет», то сумме продаж через Интернет присваивается значение 10.  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

