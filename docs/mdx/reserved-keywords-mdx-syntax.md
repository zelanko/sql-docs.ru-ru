---
title: "Зарезервированные ключевые слова (синтаксис многомерных Выражений) | Документы Microsoft"
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
- reserved words [MDX]
- Multidimensional Expressions [Analysis Services], reserved words
- MDX [Analysis Services], reserved words
ms.assetid: 0baab5fb-bd04-4ab3-b99a-9f91f3470fbb
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: fe6d331df302b14d46ed643adaee879b2a0f4dd1
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="reserved-keywords-mdx-syntax"></a>Зарезервированные ключевые слова (синтаксис многомерных выражений)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] резервируют определенные ключевые слова для эксклюзивного использования. Список зарезервированных ключевых слов см. в разделе [зарезервированные слова многомерных Выражений](../mdx/mdx-reserved-words.md).  
  
 Для зарезервированных ключевых слов есть правила:   
  
-   Нельзя включать зарезервированные ключевые слова в инструкции многомерных выражений нигде, кроме той позиции, которая задана службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   Имя ни одного объекта базы данных не должно совпадать с зарезервированным ключевым словом. Если такое имя существует, то к объекту всегда следует обращаться, используя идентификаторы с разделителями.  Хотя такой метод позволяет называть объекты именами из зарезервированных слов, все же лучше этого не делать.   
  
-   Следуйте соглашению об именовании, которое избегает употребления зарезервированных ключевых слов. Если имя объекта будет выглядеть как зарезервированное слово, можно удалить согласные или гласные из этого имени.  
  
## <a name="see-also"></a>См. также:  
 [Элементы синтаксиса многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  

