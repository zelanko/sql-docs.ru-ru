---
description: Использование хранимых процедур (многомерные выражения)
title: Использование хранимых процедур (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 095a4ab1b3acd4ec5a238f19c27446b7cebe27b2
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92196933"
---
# <a name="using-stored-procedures-mdx"></a>Использование хранимых процедур (многомерные выражения)


  Возможности служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и многомерных выражений можно расширить путем записи хранимых процедур платформы .NET или определяемых пользователем функций. Дополнительные сведения см. в разделе [ADOMD.NET Server Programming](/analysis-services/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming) .  
  
 При обращении или вызове хранимой процедуры необходимо указать имя функции и круглые скобки. Внутри скобок можно указать выражения (или аргументы), представляющие собой данные, передаваемые в виде параметров. Вызывая функцию, необходимо указать значения аргументов для всех параметров, причем в той последовательности, в которой параметры перечислены в определении пользовательской функции.  
  
 В следующем примере запроса предполагается, что на сервере служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] зарегистрирована сборка SampleAssembly:  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
> [!NOTE]  
>  *Хранимая процедура* — это терминология, используемая в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] для этих типов функций. Более ранние версии [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] вызывали эти типы функций в качестве *определяемых пользователем функций*.  
  
## <a name="types-of-stored-procedures"></a>Типы хранимых процедур  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживает сборки COM и CLR. Рекомендуется использовать сборки CLR, поскольку для них имеются расширенные механизмы защиты. Если на сервере установлена электронная таблица Microsoft Office Excel, можно также использовать функции Excel.  
  
> [!NOTE]  
>  COM-сборки Microsoft Visual Basic for Applications (VBA) регистрируются автоматически.  
  
## <a name="see-also"></a>См. также:  
 [Функции &#40;синтаксиса многомерных выражений&#41;](../mdx/functions-mdx-syntax.md)  
  
