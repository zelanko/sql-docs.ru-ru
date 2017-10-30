---
title: "NextMember (многомерные Выражения) | Документы Microsoft"
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
- NEXTMEMBER
dev_langs:
- kbMDX
helpviewer_keywords:
- NextMember function
ms.assetid: f67be3d0-082e-4bec-92e4-ba6ff33af303
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 665fe7316413bbe163ee4e51062c41f92023e7e2
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="nextmember-mdx"></a>NextMember (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает следующий элемент уровня, содержащего заданный элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.NextMember   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Замечания  
 **NextMember** функция возвращает следующий элемент на том же уровне, который содержит указанный элемент.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается элемент для августа 2001 г. как следующий по отношению к элементу для июля 2001 г.  
  
```  
SELECT [Date].[Calendar].[Month].[July 2001].NextMember ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

