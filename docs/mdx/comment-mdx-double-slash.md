---
title: (Примечание) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6570694bc38eb6f32f660006f1ed1b6797793b7b
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739523"
---
# <a name="comment-mdx-double-slash"></a>Двойная косая черта многомерных Выражений комментария


  Обозначает текст комментария пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
// Comment_Text   
```  
  
#### <a name="parameters"></a>Параметры  
 *Comment_Text*  
 Строка, содержащая текст комментария.  
  
## <a name="remarks"></a>Примечания  
 Комментарии могут занимать отдельную строку, добавляться в конец строк скрипта многомерных выражений или входить в инструкцию многомерных выражений. Сервер не обрабатывает комментарий.  
  
 Символы // используются только для однострочных комментариев. Комментарии, вставленные с помощью символов //, разделяются символом новой строки.  
  
 Длина комментариев не ограничена.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется использование этого оператора.  
  
```  
// This member returns the gross profit margin for product types  
// and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM // Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>См. также  
 [Комментарий (MDX)](../mdx/comment-mdx.md)   
 [-- (Комментарий) (MDX)](../mdx/comment-mdx-operator-reference.md)   
 [Справочник по операторам Многомерных &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
