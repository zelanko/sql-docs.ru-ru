---
title: UserName (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f8c08855d70d6a880607cc4310e6adcabbf7d9ad
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743483"
---
# <a name="username-mdx"></a>UserName (многомерные выражения)


  Возвращает имя домена и пользователя для текущего соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UserName [ ( ) ]  
```  
  
## <a name="remarks"></a>Примечания  
 Возвращаемое значение представляют собой строку следующего вида:  
  
 *домен\пользователь.*  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается имя пользователя, выполняющего запрос.  
  
```  
WITH MEMBER Measures.x AS UserName  
SELECT Measures.x ON COLUMNS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
