---
title: "Элементы синтаксиса многомерных Выражений (MDX) | Документы Microsoft"
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
ms.assetid: f4c16e1a-cf1a-4be0-839a-db018430ff14
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 77aab8ddf130fc7f93cecfe762833bbda873c81a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-syntax-elements-mdx"></a>Синтаксические элементы в многомерных выражениях (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В языке многомерных выражений существует ряд элементов, используемых в большинстве инструкций или оказывающих влияние на них.  
  
|Термин|Определение|  
|----------|----------------|  
|[Идентификаторы](../mdx/identifiers-mdx.md)|Идентификаторы — это имена таких объектов, как кубы, измерения, элементы и меры.|  
|**Типы данных**|Определяют типы данных, содержащихся в ячейках, свойствах элементов и свойствах ячеек. В языке многомерных выражений поддерживается только тип данных OLE VARIANT. Дополнительные сведения о приведении, преобразовании и манипуляциях с типом данных VARIANT см. в разделе «VARIANT и VARIANTARG» документации пакета Platform SDK.|  
|[Выражения &#40; Многомерные Выражения &#41;](../mdx/expressions-mdx.md)|Выражения являются элементы синтаксиса, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] можно определять отдельные (скалярные) значения или объектов. Выражения включают в себя функции, возвращающие одно значение, выражения набора и т. п.|  
|[Операторы](../mdx/operators-mdx-syntax.md)|Операторы — это синтаксические элементы, с помощью которых из одного или нескольких простых многомерных выражений конструируются более сложные многомерные выражения.|  
|[Функции](../mdx/functions-mdx-syntax.md)|Функции — это синтаксические элементы, принимающие одно или несколько входных значений, либо вовсе не принимающие их и возвращающие скалярное значение или объект. Примеры включают [сумма](../mdx/sum-mdx.md) для добавления нескольких значений, функцию [члены](../mdx/members-set-mdx.md) возвращает набор элементов из измерения или уровня и т. д.|  
|[Комментарии](../mdx/comments-mdx-syntax.md)|Комментарии — это фрагменты текста, которые вставляются в инструкции или скрипты многомерных выражений в качестве пояснения. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]не исполняют текст комментариев.|  
|[Зарезервированные ключевые слова](../mdx/reserved-keywords-mdx-syntax.md)|Зарезервированные слова — это слова, зарезервированные для определенных целей языком многомерных выражений. Их не следует использовать в именах объектов, указываемых в инструкциях многомерных выражений.|  
|[Элементы, кортежи и наборы](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)|Элементы, кортежи и наборы — это ключевые понятия многомерных данных, которые следует изучить перед созданием многомерных запросов.|  
  
## <a name="see-also"></a>См. также:  
 [Многомерные выражения &#40; Многомерные Выражения &#41; Ссылка](../mdx/multidimensional-expressions-mdx-reference.md)  
  
  

