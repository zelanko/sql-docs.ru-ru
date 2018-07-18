---
title: Levels (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6e8edfdc3c6888c34dd789c521bc42c6b919e1a4
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741193"
---
# <a name="levels-mdx"></a>Levels (многомерные выражения)


  Возвращает уровень, положение которого в измерении или иерархии указано числовым выражением или имя которого указано строковым выражением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Numeric expression syntax  
Hierarchy_Expression.Levels( Level_Number )  
  
String expression syntax  
Hierarchy_Expression.Levels( Level_Name )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
 *Level_Number*  
 Допустимое числовое выражение, указывающее номер уровня.  
  
 *Level_Name*  
 Допустимое строковое выражение, указывающее имя уровня.  
  
## <a name="remarks"></a>Примечания  
 Если указан номер уровня, **уровни** функция возвращает уровень, связанный с указанной позиции (с нуля).  
  
 Если указано имя уровня **уровни** функция возвращает указанный уровень.  
  
> [!NOTE]  
>  Для пользовательских функций используйте синтаксис строкового выражения.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показаны каждого из **уровни** синтаксис функции.  
  
### <a name="numeric"></a>Числовой  
 Следующий пример возвращает уровень Сountry.  
  
```  
SELECT [Geography].[Geography].Levels(1) ON 0  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>String  
 Следующий пример возвращает уровень Сountry.  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
