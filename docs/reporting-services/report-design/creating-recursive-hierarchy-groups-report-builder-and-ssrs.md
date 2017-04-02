---
title: "Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)
Чтобы вывести в отчете [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с разбиением на страницы рекурсивные данные, отражающие связь между родительским и дочерним объектами, представленную полями набора данных, можно задать выражение группы области данных на основании дочернего поля и установить свойство Parent на основании родительского поля.  
  
 Обычно группы рекурсивной иерархии используются для отображения иерархических данных, например, отношений подчиненных в структуре организации. Набор данных включает в себя список сотрудников и руководителей, причем имена руководителей также перечислены в списке сотрудников.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Создание рекурсивных иерархий  
 Чтобы создать рекурсивную иерархию в области данных табликса, нужно задать для поля выражение группы, задающее дочерние данные, а свойству Parent группы присвоить поле, задающее родительские данные. Например, если набор данных содержит идентификатор сотрудника и идентификатор руководителя, нужно присвоить выражению группы идентификатор сотрудника, а свойству Parent — идентификатор руководителя.  
  
 Группа, которая определена как рекурсивная иерархия (то есть группа, которая использует свойство Parent), может иметь только одно выражение группы. Можно использовать функцию **Level** для дополнения текстового поля, чтобы выровнять имена служащих на основе их уровней в иерархии.  
  
 Дополнительные сведения см. в разделах [Добавление или удаление группы в области данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) и [Создание группы рекурсивной иерархии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### Агрегатные функции, поддерживающие рекурсию  
 Для вычисления сводных данных в рекурсивных иерархиях можно использовать агрегатные функции служб Reporting Services, принимающие параметр *Recursive* . Параметр **Recursive** поддерживают следующие функции: [Sum](../../reporting-services/report-design/sum-function-report-builder-and-ssrs.md), [Avg](../../reporting-services/report-design/avg-function-report-builder-and-ssrs.md), [Count](../../reporting-services/report-design/count-function-report-builder-and-ssrs.md), [CountDistinct](../../reporting-services/report-design/countdistinct-function-report-builder-and-ssrs.md), [CountRows](../../reporting-services/report-design/countrows-function-report-builder-and-ssrs.md), [Max](../../reporting-services/report-design/max-function-report-builder-and-ssrs.md), [Min](../../reporting-services/report-design/min-function-report-builder-and-ssrs.md), [StDev](../../reporting-services/report-design/stdev-function-report-builder-and-ssrs.md), [StDevP](../../reporting-services/report-design/stdevp-function-report-builder-and-ssrs.md), [Sum](../../reporting-services/report-design/sum-function-report-builder-and-ssrs.md), [Var](../../reporting-services/report-design/var-function-report-builder-and-ssrs.md)и [VarP](../../reporting-services/report-design/varp-function-report-builder-and-ssrs.md). Дополнительные сведения см. в разделе [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md).  
  
## См. также  
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Область данных табликса (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md)   
 [Таблицы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Матрицы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)    
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  