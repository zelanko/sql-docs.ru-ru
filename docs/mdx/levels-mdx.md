---
title: "Levels (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Levels
dev_langs: kbMDX
helpviewer_keywords: Levels function
ms.assetid: 1a989cc9-8aa8-4ec3-b5e9-795d6fa84983
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: dbe9522966cb3efdeffc8f2a34297f9edb80c99b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="levels-mdx"></a>Levels (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>Замечания  
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
  
### <a name="string"></a>Строковые значения  
 Следующий пример возвращает уровень Сountry.  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
