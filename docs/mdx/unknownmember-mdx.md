---
title: UnknownMember (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a0332b200a74044dcd4e7d8d308923cc4b759738
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097285"
---
# <a name="unknownmember-mdx"></a>UnknownMember (многомерные выражения)


  Возвращает неизвестный элемент, связанный с уровнем или элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member expression syntax  
Member_Expression.UnknownMember  
  
Hierarchy_expression syntax  
Hierarchy_Expression.UnknownMember  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
## <a name="remarks"></a>Примечания  
 Службы Analysis Services создает неизвестный элемент для связи данных таблицы фактов с иерархией, если иерархия неизвестна. Неизвестный элемент может быть на одном из следующих уровней.  
  
-   На верхнем уровне для иерархий атрибутов, которые нельзя статистически вычислить.  
  
-   На первом уровне ниже **все** уровня для естественных иерархий.  
  
-   На любом уровне для неестественных иерархий.  
  
 Если выражение элемента указано, **UnknownMember** функция возвращает неизвестный дочерний элемент указанного элемента. Если указанный элемент не существует, функция возвращает значение NULL.  
  
 Если выражение иерархии указано, **UnknownMember** функция возвращает неизвестный элемент верхнего уровня, если он существует.  
  
 Если неизвестный элемент не существует для уровня или элемента, **UnknownMember** функция создает элемент null.  
  
> [!NOTE]  
>  Если неизвестный элемент не существует для иерархии или элемента, формируется сообщение об ошибке.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается неизвестный элемент для элемента All Products в иерархии атрибута Product для всех элементов измерения Measures.  
  
```  
SELECT [Product].[Product].[All Products].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается неизвестный элемент из иерархии Product Categories для всех элементов измерения Measures.  
  
```  
SELECT [Product].[Product Categories].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
