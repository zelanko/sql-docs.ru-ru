---
description: Children (многомерные выражения)
title: Children (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9a37bc27564baf9d75e10af78fb477ea08be092e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466516"
---
# <a name="children-mdx"></a>Children (многомерные выражения)


  Возвращает набор потомков указанного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.Children  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Remarks  
 Функция **Children** Возвращает естественно упорядоченный набор, содержащий дочерние элементы указанного элемента. Если у элемента нет потомков, функция возвращает пустой набор.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращаются потомки элемента США в иерархии Geography измерения Geography.  
  
```  
SELECT [Geography].[Geography].[Country].&[United States].Children ON 0  
FROM [Adventure Works]  
```  
  
 В следующем примере возвращаются все элементы в измерении **Measures** на оси столбцов, включая все Вычисляемые элементы, а также набор всех дочерних элементов `[Product].[Model Name]` иерархии атрибута на оси строк из куба **Adventure Works** .  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
  
```  
  
|Выпуск|Журнал|  
|-------------|-------------|  
|[!INCLUDE[ssBOL2005_R03](../includes/ssbol2005-r03-md.md)]|**Измененное содержимое**<br /> — Обновлен синтаксис и аргументы для улучшения ясности.<br /><br /> — Добавлены обновленные примеры.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
