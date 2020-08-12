---
title: Примеры уравнений фильтра (построитель отчетов) | Документация Майкрософт
description: Сведения о том, как создать фильтр отчета. Рассмотрение примеров часто используемых фильтров для создания собственного варианта.
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
helpviewer_keywords:
- filtering data [Reporting Services], filter equation examples
ms.assetid: 66bec93d-7c3b-4d4a-8cb6-7a7bb2f34ec6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 074a7d7b300d9ae55776199479b229407b2ba3a1
ms.sourcegitcommit: 5b7457c9d5302f84cc3baeaedeb515e8e69a8616
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2020
ms.locfileid: "83689737"
---
# <a name="filter-equation-examples-report-builder-and-ssrs"></a>Примеры уравнений фильтра (построитель отчетов и службы SSRS)
  Чтобы создать фильтр, необходимо указать одно или несколько уравнений фильтра. Уравнение фильтра состоит из выражения, типа данных, оператора и значения. В этом разделе приведены примеры распространенных фильтров.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="filter-examples"></a>Примеры фильтров  
 В следующей таблице перечислены примеры уравнений фильтра, использующих различные типы данных и различные операторы. Область сравнения определяется элементом отчета, для которого определен фильтр. Например, для фильтра, определенного для набора данных, **TOP % 10** — это верхние 10% значений в наборе данных; для фильтра, определенного для группы, **TOP % 10** — это верхние 10% значений в группе.  
  
|Простое выражение|Тип данных|Оператор|Значение|Описание|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|**Целое число**|**>**|`7`|Включает все значения данных, превышающие 7.|  
|`[SUM(Quantity)]`|**Целое число**|**TOP N**|`10`|Включает 10 верхних значений данных.|  
|`[SUM(Quantity)]`|**Целое число**|**TOP %**|`20`|Включает верхние 20% значений данных.|  
|`[Sales]`|**Текст**|**>**|`=CDec(100)`|Включает все значения типа System.Decimal (тип данных, используемый в SQL для денежных сумм), превышающие 100.|  
|`[OrderDate]`|**DateTime**|**>**|`2008-01-01`|Включает все даты с 1 января 2008 года по сегодняшний день.|  
|`[OrderDate]`|**DateTime**|**BETWEEN**|`2008-01-01`<br /><br /> `2008-02-01`|Включает все даты с 1 января 2008 года до 1 февраля 2008 года включительно.|  
|`[Territory]`|**Текст**|**LIKE**|`*east`|Все названия территорий, заканчивающиеся словом «east».|  
|`[Territory]`|**Текст**|**LIKE**|`%o%th*`|Все названия территорий, начинающиеся словами «North» или «South».|  
|`=LEFT(Fields!Subcat.Value,1)`|**Текст**|**IN**|`B, C, T`|Все значения подкатегорий, начинающиеся с букв «В», «C» или «T».|  
  
## <a name="see-also"></a>См. также:  
 [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Добавление фильтров набора данных, фильтров области данных и групповых фильтров (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)  
  
  
