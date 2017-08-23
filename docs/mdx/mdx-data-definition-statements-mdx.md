---
title: "Инструкции определения данных многомерных Выражений (MDX) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- MDX [Analysis Services], data manipulation
- data manipulation [MDX]
- data definition statements [MDX]
- Multidimensional Expressions [Analysis Services], data manipulation
ms.assetid: 1f975d7f-8875-43b6-a571-9d5cd7c70217
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 7799b80fd5ba847492247f1d52107da4aaf569a1
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-definition-statements-mdx"></a>Инструкции определения данных многомерных выражений
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Инструкции определения данных в многомерных выражениях позволяют создавать и удалять многомерные объекты, а также управлять ими. В следующей таблице приведены доступные инструкции определения данных.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Инструкция ALTER CUBE &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-alter-cube.md)|Изменяет структуру заданного куба.|  
|[СОЗДАТЬ оператор действия &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-create-action.md)|Создает действие, которое можно связать с кубом, измерением, иерархией или подчиненным объектом.|  
|[Создать инструкции ВЫЧИСЛЕНИЯ ЯЧЕЙКИ &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-create-cell-calculation.md)|Создает алгоритм вычисления многомерного выражения на указанном наборе кортежей в кубе.|  
|[СОЗДАТЬ инструкцию глобального КУБА &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-create-global-cube.md)|Создает и заполняет значениями локально материализованный куб на основе вложенного куба из куба на сервере. Чтобы соединиться с локально материализованным кубом, соединяться с сервером необязательно.|  
|[CREATE MEMBER, инструкция #40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-create-member.md)|Создает вычисляемый элемент.|  
|[СОЗДАТЬ инструкцию КУБА СЕАНСА &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-create-session-cube.md)|Создает и заполняет значениями куб, доступный для всех запросов в одном сеансе и созданный на основе кубов сервера.|  
|[СОЗДАТЬ инструкцию SET &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-create-set.md)|Создает именованный набор для заданного куба.|  
|[CREATE SUBCUBE, инструкция #40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-create-subcube.md)|Переопределяет пространство заданного куба или вложенного куба на указанный вложенный куб.|  
|[Действие инструкции DROP &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-drop-action.md)|Удаляет указанное действие из указанного куба.|  
|[Удалите инструкции ВЫЧИСЛЕНИЯ ЯЧЕЙКИ &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-drop-cell-calculation.md)|Удаляет указанное вычисление ячейки.|  
|[Инструкция DROP MEMBER &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-drop-member.md)|Удаляет вычисляемый элемент.|  
|[Инструкция DROP SET &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-drop-set.md)|Удаляет именованный набор.|  
|[Инструкция DROP SUBCUBE &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-drop-subcube.md)|Сбрасывает указанный вложенный куб, возвращаясь к ранее определенному кубу или определению вложенного куба с указанным именем.|  
|[Инструкцию обновления КУБА &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-refresh-cube.md)|Обновляет кэш клиента для куба.|  
  
## <a name="see-also"></a>См. также:  
 [Справка по инструкциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-statement-reference-mdx.md)   
 [Инструкции для манипулирования данными многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Инструкции сценариев многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  

