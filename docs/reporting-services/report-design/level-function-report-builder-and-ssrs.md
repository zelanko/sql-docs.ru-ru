---
title: "Функция Level (построитель отчетов и службы SSRS) | Microsoft Docs"
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
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Функция Level (построитель отчетов и службы SSRS)
  Возвращает текущий уровень глубины в рекурсивной иерархии.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Синтаксис  
  
```  
  
Level(scope)  
```  
  
#### Параметры  
 *область*  
 (**String**) (необязательно). Имя набора данных, группы или области данных, содержащих элементы отчета, к которым применяется агрегатная функция. Если аргумент *scope* не задан, используется текущая область.  
  
## Тип возвращаемых данных  
 Возвращает значение типа **Integer**. Если параметр *scope* определяет набор данных, область данных или нерекурсивное группирование (т. е. группирование без элемента **Parent**), функция **Level** возвращает значение 0. Если параметр *scope* не указан, то возвращается уровень текущей области.  
  
## Замечания  
 Возвращаемые функцией **Level** значения отсчитываются от нуля, т. е. первым уровнем в иерархии является 0.  
  
 Функция **Level** может использоваться для обеспечения автоматического определения отступов в рекурсивной иерархии, такой как список сотрудников.  
  
 Дополнительные сведения о рекурсивных иерархиях см. в разделе [Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## Пример  
 Следующий пример кода показывает уровень строки в группе «Сотрудники»:  
  
```  
=Level("Employees")  
```  
  
## См. также  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  