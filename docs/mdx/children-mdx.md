---
title: Children (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0af4d7b97777002dc5683c075f82531ccc8df86e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016805"
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
  
## <a name="remarks"></a>Примечания  
 **Дочерние элементы** функция возвращает естественно упорядоченный набор, содержащий дочерний элемент указанного элемента. Если у элемента нет потомков, функция возвращает пустой набор.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращаются потомки элемента United States в иерархии Geography измерения Geography.  
  
```  
SELECT [Geography].[Geography].[Country].&[United States].Children ON 0  
FROM [Adventure Works]  
```  
  
 Следующий пример возвращает все элементы в **меры** измерения на оси столбцов, сюда входят все вычисляемые элементы и набор всех потомков `[Product].[Model Name]` иерархии на оси строк атрибута из **Adventure Works** куба.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
  
```  
  
|Выпуск|Журнал|  
|-------------|-------------|  
|[!INCLUDE[ssBOL2005_R03](../includes/ssbol2005-r03-md.md)]|**Измененное содержимое:**<br /> -Обновлены синтаксис и аргументы для облегчения понимания.<br /><br /> — Добавлены обновленные примеры.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
