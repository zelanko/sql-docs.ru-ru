---
title: "Примеры уравнений фильтра (построитель отчетов и службы SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "фильтрация данных [службы Reporting Services], примеры уравнений фильтра"
ms.assetid: 66bec93d-7c3b-4d4a-8cb6-7a7bb2f34ec6
caps.latest.revision: 18
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 18
---
# Примеры уравнений фильтра (построитель отчетов и службы SSRS)
  Чтобы создать фильтр, необходимо указать одно или несколько уравнений фильтра. Уравнение фильтра состоит из выражения, типа данных, оператора и значения. В этом разделе приведены примеры распространенных фильтров.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Примеры фильтров  
 В следующей таблице перечислены примеры уравнений фильтра, использующих различные типы данных и различные операторы. Область сравнения определяется элементом отчета, для которого определен фильтр. Например, для фильтра, определенного для набора данных, **TOP % 10** — это верхние 10% значений в наборе данных; для фильтра, определенного для группы, **TOP % 10** — это верхние 10% значений в группе.  
  
|Простое выражение|Тип данных|Оператор|Значение|Description|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|**Целочисленный**|**>**|`7`|Включает все значения данных, превышающие 7.|  
|`[SUM(Quantity)]`|**Целочисленный**|**TOP N**|`10`|Включает 10 верхних значений данных.|  
|`[SUM(Quantity)]`|**Целочисленный**|**TOP %**|`20`|Включает верхние 20% значений данных.|  
|`[Sales]`|**Текст**|**>**|`=CDec(100)`|Включает все значения типа System.Decimal (тип данных, используемый в SQL для денежных сумм), превышающие 100.|  
|`[OrderDate]`|**DateTime**|**>**|`2008-01-01`|Включает все даты с 1 января 2008 года по сегодняшний день.|  
|`[OrderDate]`|**DateTime**|**BETWEEN**|`2008-01-01`<br /><br /> `2008-02-01`|Включает все даты с 1 января 2008 года до 1 февраля 2008 года включительно.|  
|`[Territory]`|**Текст**|**LIKE**|`*east`|Все названия территорий, заканчивающиеся словом «east».|  
|`[Territory]`|**Текст**|**LIKE**|`%o%th*`|Все названия территорий, начинающиеся словами «North» или «South».|  
|`=LEFT(Fields!Subcat.Value,1)`|**Текст**|**IN**|`B, C, T`|Все значения подкатегорий, начинающиеся с букв «В», «C» или «T».|  
  
## См. также  
 [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Добавление фильтров набора данных, фильтров области данных и групповых фильтров (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add dataset filters, data region filters, and group filters.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)  
  
  