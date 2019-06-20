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
manager: kfile
ms.openlocfilehash: 03c96a1c90f7ca0a18bd49c371a2ec90582b38f1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208787"
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
  
  
