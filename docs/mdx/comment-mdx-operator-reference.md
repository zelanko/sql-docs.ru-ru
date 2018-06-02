---
title: --(Комментарий) (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 564327619cabc00684b064585aa323c9426597c2
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577376"
---
# <a name="comment---mdx-operator-reference"></a>Комментарий - Справочник по операторам многомерных Выражений
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Обозначает текст комментариев пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>Параметры  
 *Comment_Text*  
 Строка, содержащая текст комментария.  
  
## <a name="remarks"></a>Примечания  
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
  
## <a name="see-also"></a>См. также  
 [Комментарий (MDX)](../mdx/comment-mdx.md)   
 [&#40;Комментарий&#41; &#40;многомерных Выражений&#41;](../mdx/comment-mdx-double-slash.md)   
 [Справочник по операторам Многомерных &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
