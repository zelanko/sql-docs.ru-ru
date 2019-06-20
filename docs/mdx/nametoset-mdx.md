---
title: NameToSet (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d42a94ce4e878a3f4ac0ef14a48872bf5d32a144
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63456611"
---
# <a name="nametoset-mdx"></a>NameToSet (многомерные выражения)


  Возвращает набор, содержащий элемент, заданный строкой в формате Многомерных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NameToSet(Member_Name)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Name*  
 Допустимое строковое выражение, представляющее собой имя элемента.  
  
## <a name="remarks"></a>Примечания  
 Если член с указанным именем существует, **NameToSet** функция возвращает набор, содержащий данный элемент. В противном случае функция возвращает пустой набор.  
  
> [!NOTE]  
>  Заданное имя элемента должно быть только именем элемента, оно не может быть выражением элемента. Чтобы использовать выражение элемента, см. в разделе [StrToSet &#40;многомерных Выражений&#41;](../mdx/strtoset-mdx.md).  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается значение меры по умолчанию для заданного имени элемента.  
  
```  
SELECT NameToSet('[Date].[Calendar].[July 2001]') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
