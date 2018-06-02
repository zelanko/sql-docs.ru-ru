---
title: MeasureGroupMeasures (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cf6992f80d52a98e2b242e17fc1bfff242d9dd21
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580756"
---
# <a name="measuregroupmeasures-mdx"></a>MeasureGroupMeasures (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор мер, принадлежащий к указанной группе мер.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
MEASUREGROUPMEASURES(MeasureGroupName)  
```  
  
## <a name="arguments"></a>Аргументы  
 *MeasureGroupName*  
 Допустимое строковое выражение, содержащее имя группы мер, из которой получается набор мер.  
  
## <a name="remarks"></a>Примечания  
 Указанная строка должна точно совпадать с именем группы мер. Квадратные скобки для имен групп мер с пробелами не требуются.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращаются все меры из группы Internet Sales в кубе Adventure Works.  
  
```  
SELECT MeasureGroupMeasures('Internet Sales') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
