---
title: --(Comment) (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c848277505dde5fabb10247641ee6b7f955d84e0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68006281"
---
# <a name="comment---mdx-operator-reference"></a>Comment-Справочник по операторам многомерных выражений


  Обозначает текст комментариев пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>Параметры  
 *Comment_Text*  
 Строка, содержащая текст комментария.  
  
## <a name="remarks"></a>Remarks  
 Комментарии могут занимать отдельную строку, добавляться в конец строк скрипта многомерных выражений или входить в инструкцию многомерных выражений. Сервер не обрабатывает комментарий.  
  
 Этот оператор используется для однострочных или вложенных комментариев. Комментарии, вставленные с помощью символов --, продолжаются до символа новой строки.  
  
 Длина комментариев не ограничена.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется использование этого оператора.  
  
```  
-- This member returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM -- Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>См. также:  
 [Комментарий &#40;&#41;многомерных выражений](../mdx/comment-mdx.md)   
 [&#40;комментарий&#41; &#40;&#41;многомерных выражений](../mdx/comment-mdx-double-slash.md)   
 [Справочник по операторам многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-operator-reference-mdx.md)  
  
  
