---
title: Комментарий (MDX) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f0aa1455ffd9f52fd917f68d2bb0bb80e3f25a94
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006271"
---
# <a name="comment-mdx"></a>Комментарий (многомерные Выражения)


  Обозначает текст комментариев пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
/* Comment_Text */      
```  
  
#### <a name="parameters"></a>Параметры  
 *Comment_Text*  
 Строка, содержащая текст комментария.  
  
## <a name="remarks"></a>Примечания  
 Сервер не обрабатывает текст между символами комментария / * и \*/. Комментарии можно вставлять отдельной строкой либо вставлять в инструкцию многомерных выражений. Многострочные комментарии необходимо отмечать сочетаниями символов /\* и \*/.  
  
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
  
## <a name="see-also"></a>См. также  
 [&#40;Комментарий&#41; &#40;многомерных Выражений&#41;](../mdx/comment-mdx-double-slash.md)   
 [-- (Комментарий) (MDX)](../mdx/comment-mdx-operator-reference.md)   
 [Справочник по операторам многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
