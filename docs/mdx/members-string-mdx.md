---
title: "Members (строка) (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Members
dev_langs: kbMDX
helpviewer_keywords: Members function
ms.assetid: 21fca354-448b-4b05-93f4-111bde1568f1
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 86f1471db7ccf4314ed59defdb1cd1b183c4e60d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="members-string-mdx"></a>Members (строка) (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает элемент, заданный строковым выражением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Members(Member_Name)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Name*  
 Допустимое строковое выражение, обозначающее имя элемента.  
  
## <a name="remarks"></a>Замечания  
 **Members (строка)** функция возвращает единственный элемент с заданным именем. Обычно используется **Members (строка)** функция с внешними функциями, предоставление **Members (строка)** строка, определяющая член, функции и **Members (строка)** функция возвращает значение для указанного элемента.  
  
## <a name="example"></a>Пример  
 В следующем примере используется **Members (строка)** для преобразования заданной строки является допустимый элемент и затем возвращается мера по умолчанию для элемента, указанного в строке. Указанная строка приведена в одинарных кавычках. Мерой по умолчанию является Reseller Sales Amount.  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
