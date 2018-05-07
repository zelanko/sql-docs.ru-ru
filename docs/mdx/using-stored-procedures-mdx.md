---
title: С помощью хранимых процедур (многомерные Выражения) | Документы Microsoft
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
dev_langs:
- kbMDX
helpviewer_keywords:
- user-defined functions [MDX]
- stored procedures [MDX]
ms.assetid: 818fb2ad-f88b-4d0c-9f70-f378aed42e8e
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 13733d811ba642c82f46d0bbe617f2bc42e51756
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-stored-procedures-mdx"></a>Использование хранимых процедур (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возможности служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и многомерных выражений можно расширить путем записи хранимых процедур платформы .NET или определяемых пользователем функций. Дополнительные сведения см. в разделе [программирование сервера ADOMD.NET](../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
 При обращении или вызове хранимой процедуры необходимо указать имя функции и круглые скобки. Внутри скобок можно указать выражения (или аргументы), представляющие собой данные, передаваемые в виде параметров. Вызывая функцию, необходимо указать значения аргументов для всех параметров, причем в той последовательности, в которой параметры перечислены в определении пользовательской функции.  
  
 В следующем примере запроса предполагается, что на сервере служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] зарегистрирована сборка SampleAssembly:  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
> [!NOTE]  
>  *Хранимая процедура* является терминологию, используемую в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] для этих типов функций. Более ранних версиях [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] вызывается таких типов функций как *определяемые пользователем функции*.  
  
## <a name="types-of-stored-procedures"></a>Типы хранимых процедур  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживает сборки COM и CLR. Рекомендуется использовать сборки CLR, поскольку для них имеются расширенные механизмы защиты. Если на сервере установлена электронная таблица Microsoft Office Excel, можно также использовать функции Excel.  
  
> [!NOTE]  
>  COM-сборки Microsoft Visual Basic for Applications (VBA) регистрируются автоматически.  
  
## <a name="see-also"></a>См. также  
 [Функции &#40;синтаксис многомерных Выражений&#41;](../mdx/functions-mdx-syntax.md)  
  
  
