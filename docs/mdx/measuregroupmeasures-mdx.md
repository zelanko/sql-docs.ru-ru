---
title: MeasureGroupMeasures (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 45d7adc5e1f4e103790d9d067bc4876fb5b134d2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68033878"
---
# <a name="measuregroupmeasures-mdx"></a>MeasureGroupMeasures (многомерные выражения)


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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
