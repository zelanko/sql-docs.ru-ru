---
title: Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 589fe7470de4909d9513d80726c59412f5ea2447
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56292362"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)
Чтобы вывести в отчете [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с разбиением на страницы рекурсивные данные, отражающие связь между родительским и дочерним объектами, представленную полями набора данных, можно задать выражение группы области данных на основании дочернего поля и установить свойство Parent на основании родительского поля.  
  
 Обычно группы рекурсивной иерархии используются для отображения иерархических данных, например, отношений подчиненных в структуре организации. Набор данных включает в себя список сотрудников и руководителей, причем имена руководителей также перечислены в списке сотрудников.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>Создание рекурсивных иерархий  
 Чтобы создать рекурсивную иерархию в области данных табликса, нужно задать для поля выражение группы, задающее дочерние данные, а свойству Parent группы присвоить поле, задающее родительские данные. Например, если набор данных содержит идентификатор сотрудника и идентификатор руководителя, нужно присвоить выражению группы идентификатор сотрудника, а свойству Parent — идентификатор руководителя.  
  
 Группа, которая определена как рекурсивная иерархия (то есть группа, которая использует свойство Parent), может иметь только одно выражение группы. Можно использовать функцию **Level** для дополнения текстового поля, чтобы выровнять имена служащих на основе их уровней в иерархии.  
  
 Дополнительные сведения см. в разделах [Добавление или удаление группы в области данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) и [Создание группы рекурсивной иерархии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### <a name="aggregate-functions-that-support-recursion"></a>Агрегатные функции, поддерживающие рекурсию  
 Для вычисления сводных данных в рекурсивных иерархиях можно использовать агрегатные функции служб Reporting Services, принимающие параметр *Recursive* . Параметр **Recursive** поддерживают следующие функции: [Sum](../../reporting-services/report-design/report-builder-functions-sum-function.md), [Avg](../../reporting-services/report-design/report-builder-functions-avg-function.md), [Count](../../reporting-services/report-design/report-builder-functions-count-function.md), [CountDistinct](../../reporting-services/report-design/report-builder-functions-countdistinct-function.md), [CountRows](../../reporting-services/report-design/report-builder-functions-countrows-function.md), [Max](../../reporting-services/report-design/report-builder-functions-max-function.md), [Min](../../reporting-services/report-design/report-builder-functions-min-function.md), [StDev](../../reporting-services/report-design/report-builder-functions-stdev-function.md), [StDevP](../../reporting-services/report-design/report-builder-functions-stdevp-function.md), [Sum](../../reporting-services/report-design/report-builder-functions-sum-function.md), [Var](../../reporting-services/report-design/report-builder-functions-var-function.md) и [VarP](../../reporting-services/report-design/report-builder-functions-varp-function.md). Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>См. также:  
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Область данных табликса (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)   
 [Таблицы &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Матрицы &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Списки &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)    
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
