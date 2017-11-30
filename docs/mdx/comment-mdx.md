---
title: "Комментарий (MDX) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '*/'
- /*
dev_langs: kbMDX
helpviewer_keywords:
- commenting characters
- /*...*/ (comment)
ms.assetid: 64434ae4-80ce-4634-86b8-4125dfaa7f61
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f09911224fb93b1ba5ca70ecf57d933f67f3f85b
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="comment-mdx"></a>Комментарий (многомерные Выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Обозначает текст комментариев пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
/* Comment_Text */      
```  
  
#### <a name="parameters"></a>Параметры  
 *Comment_Text*  
 Строка, содержащая текст комментария.  
  
## <a name="remarks"></a>Замечания  
 Сервер не обрабатывает текст между символами комментария / * и \*/. Комментарии можно вставлять отдельной строкой либо вставлять в инструкцию многомерных выражений. Многострочные комментарии должны обозначаться символами /\* и \*/.  
  
 Длина комментариев не ограничена. Можно создавать вложенные комментарии. Например, `/* Test /*Comment*/ Text*/` — вложенный комментарий.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется использование этого оператора.  
  
```  
/* This member returns the gross profit margin for product types  
  and reseller types crossjoined by year. */  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
    [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM /* Select from the Adventure Works cube. */  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>См. также:  
 [&#40; Комментарий &#41; &#40; Многомерные Выражения &#41;](../mdx/comment-mdx-double-slash.md)   
 [--&#40; Комментарий &#41; &#40; Многомерные Выражения &#41;](../mdx/comment-mdx-operator-reference.md)   
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
