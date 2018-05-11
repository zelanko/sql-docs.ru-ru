---
title: Изменение данных (многомерные Выражения) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 720cf79b92c840fd41ae8453b41fbbe18cefe19f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="mdx-data-modification---modifying-data"></a>Изменение данных MDX - изменение данных
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Наряду с использованием многомерных выражений для получения и обработки данных измерений и кубов можно использовать многомерные выражения для обновления и *обратной записи* данных измерений и кубов. Обновления могут быть как временными, например в случае гипотетического анализа «что, если...», так и постоянными, когда изменения должны происходить на основе анализа данных.  
  
 Данные могут обновляться на уровне измерения или куба.  
  
 **Обратная запись в измерение**  
 Для изменения данных измерения, доступного для записи, используется [Инструкция ALTER CUBE (многомерные выражения)](../../../mdx/mdx-data-definition-alter-cube.md) , а для отражения операций удаления, создания и обновления значений атрибутов используется [Инструкция REFRESH CUBE (многомерные выражения)](../../../mdx/mdx-data-definition-refresh-cube.md) . Кроме того, при помощи инструкции ALTER CUBE можно выполнять такие сложные операции, как удаление всего вложенного дерева в иерархии и продвижение потомков удаленного элемента.  
  
 **Обратная запись в куб**  
 Для обновления данных куба, доступного для записи, используется инструкция [UPDATE CUBE](../../../mdx/mdx-data-manipulation-update-cube.md) . Инструкция UPDATE CUBE позволяет записать конкретное значение в кортеж. [Инструкция REFRESH CUBE (многомерные выражения)](../../../mdx/mdx-data-definition-refresh-cube.md) используется для отражения обновленных данных в клиентском сеансе.  
  
 Дополнительные сведения см. в разделе [Обратная запись в куб (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-data-modification-using-cube-writebacks.md).  
  
## <a name="see-also"></a>См. также:  
 [Основные принципы запросов многомерных Выражений & #40; Службы Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
