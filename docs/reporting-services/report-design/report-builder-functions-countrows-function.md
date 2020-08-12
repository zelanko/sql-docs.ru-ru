---
title: Функция CountRows (построитель отчетов) | Документация Майкрософт
description: Узнайте больше о функции CountRows, которая возвращает число строк в указанной области, включая строки со значениями NULL.
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 5b1c403d-6afd-44c8-b5f6-5ecff2a29a45
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 81b82f0d0d01dec7e3302eb32e3422f527f02064
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85034934"
---
# <a name="report-builder-functions---countrows-function"></a>Функции построителя отчетов — функция CountRows
  Возвращает число строк в указанной области, включая строки со значениями NULL.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CountRows(scope, recursive)  
```  
  
#### <a name="parameters"></a>Параметры  
 *область*  
 (**String**) — имя набора данных, области данных или группы, содержащих подсчитываемые элементы отчета.  
  
 *рекурсивные*  
 (**Перечислимый тип**) Необязательно. **Simple** (по умолчанию) или **RdlRecursive**. Указывает, нужно ли выполнять статистическую обработку рекурсивно.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Возвращает значение типа **Integer**.  
  
## <a name="remarks"></a>Remarks  
 Функция**CountRows** подсчитывает все строки в указанной области, включая строки со значениями NULL.  
  
 Значение *scope* не может быть выражением и должно указывать на текущую или включающую область.  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Дополнительные сведения о рекурсивных агрегатах см. в разделе [Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано выражение, вычисляющее число строк в группе строк, называемой `GroupbyCategory` (на основании выражения `[Category]`).  
  
```  
="Number of rows: " & CountRows("GroupbyCategory")  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
