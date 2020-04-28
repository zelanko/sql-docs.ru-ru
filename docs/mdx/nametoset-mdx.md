---
title: NameToSet (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 77731495eb058da05f6c61be391591a40725e579
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68088393"
---
# <a name="nametoset-mdx"></a>NameToSet (многомерные выражения)


  Возвращает набор, содержащий элемент, заданный в формате строки МНОГОМЕРных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NameToSet(Member_Name)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Name*  
 Допустимое строковое выражение, представляющее собой имя элемента.  
  
## <a name="remarks"></a>Remarks  
 Если указанное имя элемента существует, функция **NameToSet** возвращает набор, содержащий этот элемент. В противном случае функция возвращает пустой набор.  
  
> [!NOTE]  
>  Заданное имя элемента должно быть только именем элемента, оно не может быть выражением элемента. Сведения об использовании выражения элемента см. в разделе [StrToSet &#40;многомерных выражений&#41;](../mdx/strtoset-mdx.md).  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается значение меры по умолчанию для заданного имени элемента.  
  
```  
SELECT NameToSet('[Date].[Calendar].[July 2001]') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
