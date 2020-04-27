---
title: Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea704f5ec6ab26db37bb56b86a42605ab50dd48b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66106122"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)
  Чтобы отобразить рекурсивные данные, в которых связь между родительским и дочерним элементами представлена полями в наборе данных, можно задать выражение группы области данных на основе дочернего поля и установить свойство Parent на основе родительского поля.  
  
 Обычно группы рекурсивной иерархии используются для отображения иерархических данных, например, отношений подчиненных в структуре организации. Набор данных включает в себя список сотрудников и руководителей, причем имена руководителей также перечислены в списке сотрудников.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>Создание рекурсивных иерархий  
 Чтобы создать рекурсивную иерархию в области данных табликса, нужно задать для поля выражение группы, задающее дочерние данные, а свойству Parent группы присвоить поле, задающее родительские данные. Например, если набор данных содержит идентификатор сотрудника и идентификатор руководителя, нужно присвоить выражению группы идентификатор сотрудника, а свойству Parent — идентификатор руководителя.  
  
 Группа, которая определена как рекурсивная иерархия (то есть группа, которая использует свойство Parent), может иметь только одно выражение группы. Можно использовать функцию `Level` для дополнения текстового поля, чтобы выровнять имена служащих на основе их уровней в иерархии.  
  
 Дополнительные сведения см. в разделах [Добавление или удаление группы в области данных (построитель отчетов и службы SSRS)](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) и [Создание группы рекурсивной иерархии (построитель отчетов и службы SSRS)](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### <a name="aggregate-functions-that-support-recursion"></a>Агрегатные функции, поддерживающие рекурсию  
 Для вычисления сводных данных в рекурсивных иерархиях можно использовать агрегатные функции служб Reporting Services, принимающие параметр *Recursive* . Следующие функции принимаются `Recursive` в качестве параметра: [Sum](report-builder-functions-sum-function.md), [AVG](report-builder-functions-avg-function.md), [Count](report-builder-functions-count-function.md), [CountDistinct](report-builder-functions-countdistinct-function.md), [CountRows](report-builder-functions-countrows-function.md), [Max](report-builder-functions-max-function.md), [min](report-builder-functions-min-function.md), [STDEV](report-builder-functions-stdev-function.md), [StDevP](report-builder-functions-stdevp-function.md), [Sum](report-builder-functions-sum-function.md), [var](report-builder-functions-var-function.md)и [VARP](report-builder-functions-varp-function.md). Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>См. также:  
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Область данных табликса (построитель отчетов и службы SSRS)](../tablix-data-region-report-builder-and-ssrs.md)   
 [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](report-builder-functions-aggregate-functions-reference.md)   
 [Таблицы &#40;построитель отчетов и службы SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Матрицы &#40;построитель отчетов и службы SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Списки &#40;построитель отчетов и службы SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
