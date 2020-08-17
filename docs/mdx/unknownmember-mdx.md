---
description: UnknownMember (многомерные выражения)
title: UnknownMember (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0489556836b943ba91d4e17b3a164aeca0c648d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341150"
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
  
## <a name="remarks"></a>Remarks  
 Analysis Services создает неизвестный элемент для связывания данных таблицы фактов с иерархией, если иерархия неизвестна. Неизвестный элемент может быть на одном из следующих уровней.  
  
-   На верхнем уровне для иерархий атрибутов, которые нельзя статистически вычислить.  
  
-   На первом уровне под уровнем « **все** » для естественных иерархий.  
  
-   На любом уровне для неестественных иерархий.  
  
 Если указано выражение элемента, функция **UnknownMember** возвращает неизвестный дочерний элемент указанного элемента. Если указанный элемент не существует, функция возвращает значение NULL.  
  
 Если указано выражение иерархии, функция **UnknownMember** возвращает неизвестный элемент на верхнем уровне, если он существует.  
  
 Если неизвестный элемент не существует на уровне или в элементе, функция **UnknownMember** создает элемент NULL.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
