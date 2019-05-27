---
title: Часто используемые фильтры (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- multivalued parameters [Reporting Services]
- single-valued parameters [Reporting Services]
- parameters [Reporting Services], multivalued
- valid values [Reporting Services]
ms.assetid: cb70d0cd-707b-4de5-b39f-e4eb57d316aa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f807060994c2225dc1e6605344bbb3bd5d2709e8
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66106238"
---
# <a name="commonly-used-filters-report-builder-and-ssrs"></a>Часто используемые фильтры (построитель отчетов и службы SSRS)
  Чтобы создать фильтр, необходимо указать одно или несколько уравнений фильтра. Уравнение фильтра состоит из выражения, типа данных, оператора и значения. В этом разделе приведены примеры распространенных фильтров.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="filter-examples"></a>Примеры фильтров  
 В следующей таблице перечислены примеры уравнений фильтра, использующих различные типы данных и различные операторы. Область сравнения определяется элементом отчета, для которого определен фильтр. Например, для фильтра, определенного для набора данных, **TOP % 10** — это верхние 10% значений в наборе данных; для фильтра, определенного для группы, **TOP % 10** — это верхние 10% значений в группе.  
  
|Простое выражение|Тип данных|Оператор|Значение|Описание|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|`Integer`|`>`|`7`|Включает все значения данных, превышающие 7.|  
|`[SUM(Quantity)]`|`Integer`|`TOP N`|`10`|Включает 10 верхних значений данных.|  
|`[SUM(Quantity)]`|`Integer`|`TOP %`|`20`|Включает верхние 20% значений данных.|  
|`[Sales]`|`Text`|`>`|`=CDec(100)`|Включает все значения типа System.Decimal (тип данных, используемый в SQL для денежных сумм), превышающие 100.|  
|`[OrderDate]`|`DateTime`|`>`|`2088-01-01`|Включает все даты с 1 января 2008 года по сегодняшний день.|  
|`[OrderDate]`|`DateTime`|`BETWEEN`|`2008-01-01`<br /><br /> `2008-02-01`|Включает все даты с 1 января 2008 года до 1 февраля 2008 года включительно.|  
|`[Territory]`|`Text`|`LIKE`|`*east`|Все названия территорий, заканчивающиеся словом «east».|  
|`[Territory]`|`Text`|`LIKE`|`%o%th*`|Все названия территорий, начинающиеся словами «North» или «South».|  
|`=LEFT(Fields!Subcat.Value,1)`|`Text`|`IN`|`B, C, T`|Все значения подкатегорий, начинающиеся с букв «В», «C» или «T».|  
  
## <a name="examples-with-report-parameters"></a>Примеры с параметрами отчетов  
 В следующей таблице приведены примеры критериев фильтра, которые включают ссылку на однозначный и многозначный параметр.  
  
|Тип параметра|Критерий (фильтра)|Оператор|Значение|Тип данных|  
|--------------------|---------------------------|--------------|-----------|---------------|  
|Однозначный|`[EmployeeID]`|=|`[@EmployeeID]`|Целочисленный|  
|Многозначный|`[EmployeeID]`|IN|`[@EmployeeID]`|Целочисленный|  
  
## <a name="see-also"></a>См. также  
 [Параметры отчета (построитель отчетов и конструктор отчетов)](report-parameters-report-builder-and-report-designer.md)   
 [Добавление фильтров набора данных, фильтров области данных и групповых фильтров (построитель отчетов и службы SSRS)](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md)  
  
  
