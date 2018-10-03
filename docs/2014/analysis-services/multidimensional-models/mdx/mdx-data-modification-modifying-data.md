---
title: Изменение данных (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying data [MDX]
- Multidimensional Expressions [Analysis Services], data modifications
- MDX [Analysis Services], data modifications
- data modifications [MDX]
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9e83cd72f972107b83bb6efea27d28857053e200
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177604"
---
# <a name="modifying-data-mdx"></a>Изменение данных (многомерные выражения)
  Наряду с использованием многомерных выражений для получения и обработки данных измерений и кубов можно использовать многомерные выражения для обновления и *обратной записи* данных измерений и кубов. Обновления могут быть как временными, например в случае гипотетического анализа «что, если...», так и постоянными, когда изменения должны происходить на основе анализа данных.  
  
 Данные могут обновляться на уровне измерения или куба.  
  
 **Обратная запись в измерение**  
 Для изменения данных измерения, доступного для записи, используется [Инструкция ALTER CUBE (многомерные выражения)](/sql/mdx/mdx-data-definition-alter-cube) , а для отражения операций удаления, создания и обновления значений атрибутов используется [Инструкция REFRESH CUBE (многомерные выражения)](/sql/mdx/mdx-data-definition-refresh-cube) . Кроме того, при помощи инструкции ALTER CUBE можно выполнять такие сложные операции, как удаление всего вложенного дерева в иерархии и продвижение потомков удаленного элемента.  
  
 **Обратная запись в куб**  
 Для обновления данных куба, доступного для записи, используется инструкция [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) . Инструкция UPDATE CUBE позволяет записать конкретное значение в кортеж. [Инструкция REFRESH CUBE (многомерные выражения)](/sql/mdx/mdx-data-definition-refresh-cube) используется для отражения обновленных данных в клиентском сеансе.  
  
 Дополнительные сведения см. в разделе [Обратная запись в куб (многомерные выражения)](mdx-data-modification-using-cube-writebacks.md).  
  
## <a name="see-also"></a>См. также  
 [Основные принципы запросов многомерных Выражений &#40;служб Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
