---
title: "Соглашения о синтаксисе многомерных Выражений (MDX) | Документы Microsoft"
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
- Multidimensional Expressions [Analysis Services], syntax
- MDX [Analysis Services], syntax
ms.assetid: 50a6e723-91c4-407b-a0d5-87d0d4e4e0f6
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 522b9ad28f712c52e603a2eaf539bb76f4dd0bd6
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-syntax-conventions-mdx"></a>Синтаксические соглашения в многомерных выражениях (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В диаграммах синтаксиса многомерных выражений в справочнике по языку многомерных выражений используются следующие обозначения.  
  
|Обозначение|Использование|  
|----------------|-----------|  
|*курсив*|Пользовательские аргументы в синтаксисе многомерных выражений.|  
|&#124; (вертикальная черта)|Разделитель элементов синтаксиса внутри квадратных или фигурных скобок. Может быть выбран только один из элементов.|  
|`[ ]`(скобки)|Необязательные элементы синтаксиса. Скобки не вводятся.|  
|[,] ...n|Указание на то, что предыдущий элемент может повторяться любое число раз. Элементы разделяются запятыми.|  
|\<Метка >:: =|Имя синтаксического блока. Это обозначение используется для группирования и именования длинных фрагментов синтаксиса или синтаксических блоков, которые могут использоваться в нескольких местах внутри инструкции. Каждое место, в котором используется этот синтаксический блок, обозначается меткой, заключенной в угловые скобки: \<метка >.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-language-reference-mdx.md)  
  
  


