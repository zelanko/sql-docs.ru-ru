---
title: "Функция CountRows (построитель отчетов и службы SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b1c403d-6afd-44c8-b5f6-5ecff2a29a45
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Функция CountRows (построитель отчетов и службы SSRS)
  Возвращает число строк в указанной области, включая строки со значениями NULL.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Синтаксис  
  
```  
  
CountRows(scope, recursive)  
```  
  
#### Параметры  
 *область*  
 (**String**) — имя набора данных, области данных или группы, содержащих подсчитываемые элементы отчета.  
  
 *рекурсивные*  
 (**Перечислимый тип**) Необязательно. **Simple** (по умолчанию) или **RdlRecursive**. Указывает, нужно ли выполнять статистическую обработку рекурсивно.  
  
## Тип возвращаемых данных  
 Возвращает значение типа **Integer**.  
  
## Замечания  
 Функция**CountRows** подсчитывает все строки в указанной области, включая строки со значениями NULL.  
  
 Значение *scope* не может быть выражением и должно указывать на текущую или включающую область.  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md).  
  
 Дополнительные сведения о рекурсивных агрегатах см. в разделе [Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## Пример  
 В следующем примере кода показано выражение, вычисляющее число строк в группе строк, называемой `GroupbyCategory` (на основании выражения `[Category]`).  
  
```  
="Number of rows: " & CountRows("GroupbyCategory")  
```  
  
## См. также  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  