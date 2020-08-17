---
description: UserName (многомерные выражения)
title: UserName (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6fbcc17cc34c6f4353698b918d0ab5ee3dc55701
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341140"
---
# <a name="username-mdx"></a>UserName (многомерные выражения)


  Возвращает имя домена и пользователя для текущего соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UserName [ ( ) ]  
```  
  
## <a name="remarks"></a>Remarks  
 Возвращаемое значение представляют собой строку следующего вида:  
  
 *\*  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается имя пользователя, выполняющего запрос.  
  
```  
WITH MEMBER Measures.x AS UserName  
SELECT Measures.x ON COLUMNS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
