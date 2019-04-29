---
title: Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 92412bbde8a1032b34264ca254560f31704281e8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63135574"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)
  Чтобы вывести рекурсивные данные, отражающие связь между родительским и дочерним, представленную полями набора данных, можно задать выражение группы области данных, на основании дочернего поля и установить свойство Parent на основании родительского поля.  
  
 Отображение иерархических данных часто используется для группы рекурсивной иерархии, например, сотрудников в структуре организации. Набор данных включает в себя список сотрудников и руководителей, где имена руководителей также перечислены в списке сотрудников.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>Создание рекурсивных иерархий  
 Чтобы выполнить сборку рекурсивную иерархию в области данных табликса, необходимо задать выражение группы в поле, задающее дочерние данные, а свойству Parent группы присвоить поле, задающее родительские данные. Например для набора данных, включающий поля, идентификатор сотрудника и идентификатор руководителя, где отчет Сотрудники диспетчерам, нужно присвоить выражению группы идентификатор сотрудника и родительское свойство диспетчеру идентификатор.  
  
 Группа, которая определена как рекурсивная иерархия (то есть группа, которая использует свойство Parent) может иметь только одно выражение группы. Можно использовать функцию `Level` для дополнения текстового поля, чтобы выравнивать имена служащих на основе их уровней в иерархии.  
  
 Дополнительные сведения см. в разделе [Добавление или удаление группы в области данных &#40;построитель отчетов и службы SSRS&#41; ](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) и [Создание группы рекурсивной иерархии &#40;построитель отчетов и службы SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### <a name="aggregate-functions-that-support-recursion"></a>Агрегатные функции, поддерживающие рекурсию  
 Можно использовать агрегатные функции служб Reporting Services, принимающие параметр *рекурсивные* для вычисления сводных данных в рекурсивных иерархиях. Следующие функции допускают `Recursive` как параметр: [Сумма](report-builder-functions-sum-function.md), [Avg](report-builder-functions-avg-function.md), [число](report-builder-functions-count-function.md), [CountDistinct](report-builder-functions-countdistinct-function.md), [CountRows](report-builder-functions-countrows-function.md), [Max](report-builder-functions-max-function.md), [Min](report-builder-functions-min-function.md), [StDev](report-builder-functions-stdev-function.md), [StDevP](report-builder-functions-stdevp-function.md), [Sum](report-builder-functions-sum-function.md), [Var](report-builder-functions-var-function.md), и [VarP](report-builder-functions-varp-function.md) . Дополнительные сведения см. в разделе [Справочник по агрегатным функциям &#40;построитель отчетов и службы SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>См. также  
 [Таблицы, матрицы и списки &#40;построитель отчетов и службы SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Область данных Табликса &#40;построитель отчетов и службы SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Справочник по агрегатным функциям &#40;построитель отчетов и службы SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)   
 [Таблицы &#40;построитель отчетов и службы SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Матрицы &#40;построитель отчетов и службы SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Перечисляет &#40;построитель отчетов и службы SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Таблицы, матрицы и списки &#40;построитель отчетов и службы SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
