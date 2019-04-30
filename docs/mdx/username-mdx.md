---
title: UserName (многомерные Выражения) | Документация Майкрософт
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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63298025"
---
# <a name="username-mdx"></a>UserName (многомерные выражения)


  Возвращает имя домена и пользователя для текущего соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UserName [ ( ) ]  
```  
  
## <a name="remarks"></a>Примечания  
 Возвращаемое значение представляют собой строку следующего вида:  
  
 *имя домена или пользователя*  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается имя пользователя, выполняющего запрос.  
  
```  
WITH MEMBER Measures.x AS UserName  
SELECT Measures.x ON COLUMNS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
