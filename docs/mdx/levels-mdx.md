---
description: Levels (многомерные выражения)
title: Levels (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f3b0a7eaea166fdefbfd947faf95b58f74bdb8be
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429876"
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
  
## <a name="remarks"></a>Remarks  
 Если указан номер уровня, функция **Levels** возвращает уровень, связанный с заданной позицией, начинающейся с нуля.  
  
 Если указано имя уровня, функция **Levels** Возвращает указанный уровень.  
  
> [!NOTE]  
>  Для пользовательских функций используйте синтаксис строкового выражения.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показаны все синтаксисы функций **уровней** .  
  
### <a name="numeric"></a>Числовой  
 Следующий пример возвращает уровень Сountry.  
  
```  
SELECT [Geography].[Geography].Levels(1) ON 0  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>Строка  
 Следующий пример возвращает уровень Сountry.  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
