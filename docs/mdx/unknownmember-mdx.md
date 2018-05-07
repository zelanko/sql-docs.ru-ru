---
title: UnknownMember (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- UnknownMember
dev_langs:
- kbMDX
helpviewer_keywords:
- UnknownMember function
ms.assetid: 5ae39cbe-65c8-4a59-9548-71b28ecf6eb5
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 7c423b452f7ec49a7f544984fab6b0891391ac8b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="unknownmember-mdx"></a>UnknownMember (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает неизвестный элемент, связанный с уровнем или элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member expression syntax  
Member_Expression.UnknownMember  
  
Hierarchy_expression syntax  
Hierarchy_Expression.UnknownMember  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
## <a name="remarks"></a>Замечания  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Создает неизвестный элемент для связи данных таблицы фактов с иерархией, если иерархия неизвестна. Неизвестный элемент может быть на одном из следующих уровней.  
  
-   На верхнем уровне для иерархий атрибутов, которые нельзя статистически вычислить.  
  
-   На первом уровне ниже **все** уровня для естественных иерархий.  
  
-   На любом уровне для неестественных иерархий.  
  
 Если выражение элемента указано, **UnknownMember** функция возвращает неизвестный дочерний элемент указанного элемента. Если указанный элемент не существует, функция возвращает значение NULL.  
  
 Если указано выражение иерархии, **UnknownMember** функция возвращает неизвестный элемент верхнего уровня, если он существует.  
  
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
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
