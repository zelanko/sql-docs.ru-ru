---
title: Функция Union (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: c87e16fe-c12a-4c9d-a9df-7a94e229fd04
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 09c16397bae867309fce5d47cc5f0397825d7953
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59935630"
---
# <a name="union-function-report-builder-and-ssrs"></a>Функция Union (построитель отчетов и службы SSRS)
  Возвращает объединение всех числовых значений, отличных от NULL, заданных выражением, вычисляемым для данной области.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Union(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>Параметры  
 *expression*  
 (`SqlGeometry` или `SqlGeography`) Выражение, к которому применяется статистическая обработка.  
  
 *область*  
 (`String`) Необязательно. Имя набора данных, группы или области данных, содержащих элементы отчета, к которым применяется агрегатная функция. Если аргумент *scope* не задан, используется текущая область.  
  
 *рекурсивные*  
 (**Перечислимый тип**) Необязательно. `Simple` (по умолчанию) или `RdlRecursive`. Указывает, нужно ли выполнять статистическую обработку рекурсивно.  
  
## <a name="return"></a>Возвращает  
 Возвращает пространственный объект, или `SqlGeometry`, или `SqlGeography`, в зависимости от типа выражения. Дополнительные сведения о `SqlGeometry` и `SqlGeography` пространственных типов данных, см. в разделе [Общие сведения о типах пространственных данных](../../relational-databases/spatial/spatial-data-types-overview.md).  
  
## <a name="remarks"></a>Примечания  
 Данные в наборе, указанном в выражении, должны иметь один и тот же тип.  
  
 Значение *scope* должно быть строковой константой и не может быть выражением. Для внешних агрегатов и агрегатов, в которых не задаются другие агрегаты, параметр *scope* должен ссылаться не текущую область или включающую область. Области наборов данных не поддерживаются. Для агрегатов, содержащих агрегаты, во вложенных агрегатах может указываться дочерняя область.  
  
 *Expression* может содержать вызовы вложенных агрегатных функций со следующими условиями и исключениями.  
  
-   Параметр*Scope* для вложенных агрегатов должен совпадать с областью внешнего агрегата или входить в нее. Одна область из всех уникальных областей в выражении должна быть дочерней относительно всех других областей.  
  
-   Параметр*Scope* для вложенных агрегатов не может быть именем набора данных.  
  
-   *Выражение* не может содержать `First`, `Last`, `Previous`, или `RunningValue` функции.  
  
-   *Expression* не может содержать вложенные агрегаты, в которых указан параметр *recursive*.  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Дополнительные сведения о рекурсивных агрегатах см. в разделе [Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Пример  
 Следующая таблица содержит примеры выражений `SqlGeometry` и результирующих выражений `Union` в формате WKT (Well Known Text) для пространственных данных.  
  
|Поле с пространственными данными|Пример|Результат Union|  
|-----------------------------|-------------|------------------|  
|[PointLocation]|POINT(1 2)<br /><br /> POINT(3 4)|MULTIPOINT((1 2), (3 4))|  
|[PathDefinition]|LINESTRING(1 2, 3 4)<br /><br /> LINESTRING(5 6, 7 8)|MULTILINESTRING((7 8, 5 6), (3 4, 1 2))|  
|[PolygonDefinition]|POLYGON((1 2, 3 4, 5 2, 1 2))<br /><br /> POLYGON((-1 2, -3 4, -5 2, -1 2))|MULTIPOLYGON(((1 2, 5 2, 3 4, 1 2)), ((-5 2, -1 2, -3 4, -5 2)))|  
  
```  
=Union(Fields!PointLocation.Value)  
=Union(Fields!PathDefinition.Value)  
=Union(Fields!PolygonDefinition.Value, "Group1")  
```  
  
## <a name="see-also"></a>См. также  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
