---
title: Функция Count (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b50b101-daf8-4fb0-ae04-57384755779f
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: e623374290e9620d048d651683a58bfcd3ddf573
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187961"
---
# <a name="count-function-report-builder-and-ssrs"></a>Функция Count (построитель отчетов и службы SSRS)
  Возвращает количество значений, отличных от NULL, определяемое выражением, вычисляемым в контексте данной области.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Count(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>Параметры  
 *expression*  
 (`Variant` или `Binary`) выражение, к которому применяется статистическая обработка, например, `=Fields!FieldName.Value`.  
  
 *область*  
 (`String`) Имя набора данных, группы или области данных, содержащую отчет, элементы, к которым применяется Агрегатная функция. Если аргумент *scope* не задан, используется текущая область.  
  
 *рекурсивные*  
 (**Перечислимый тип**) Необязательно. `Simple` (по умолчанию) или `RdlRecursive`. Указывает, нужно ли выполнять статистическую обработку рекурсивно.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Возвращает `Integer`.  
  
## <a name="remarks"></a>Примечания  
 Значение *scope* должно быть строковой константой и не может быть выражением. Для внешних агрегатов и агрегатов, в которых не задаются другие агрегаты, параметр *scope* должен ссылаться не текущую область или включающую область. Для агрегатов, содержащих агрегаты, во вложенных агрегатах может указываться дочерняя область.  
  
 *Expression* может содержать вызовы вложенных агрегатных функций со следующими условиями и исключениями.  
  
-   Параметр*Scope* для вложенных агрегатов должен совпадать с областью внешнего агрегата или входить в нее. Одна область из всех уникальных областей в выражении должна быть дочерней относительно всех других областей.  
  
-   Параметр*Scope* для вложенных агрегатов не может быть именем набора данных.  
  
-   *Выражение* не должны содержать `First`, `Last`, `Previous`, или `RunningValue` функции.  
  
-   *Expression* не может содержать вложенные агрегаты, в которых указан параметр *recursive*.  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Дополнительные сведения о рекурсивных агрегатах см. в разделе [Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
 Пример  
  
## <a name="description"></a>Описание  
 В следующем примере кода показано выражение, вычисляющее число значений `Size` , отличных от NULL, для области по умолчанию и для области родительской группы. Выражение добавляется в ячейку строки, относящуюся к дочерней группе `GroupbySubcategory`. Родительской группой является `GroupbyCategory`. Выражение отображает результаты для группы `GroupbySubcategory` (область по умолчанию) и затем для группы `GroupbyCategory` (область родительской группы).  
  
> [!NOTE]  
>  Выражения не должны содержать действительные возвраты каретки и разрывы строк; эти символы включены в пример для поддержки модулей подготовки отчетов документации. При копировании следующего примера удалите возвраты каретки изо всех строк.  
  
## <a name="code"></a>код  
  
```  
="Count (Subcategory): " & Count(Fields!Size.Value) &   
"Count (Category): " & Count(Fields!Size.Value,"GroupbyCategory")  
```  
  
## <a name="see-also"></a>См. также  
 [Выражения используются в отчетах &#40;отчетов построителя отчетов и службы SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md)   
 [Область выражения для итогов, статистических функций и встроенных коллекций &#40;отчетов построителя отчетов и службы SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  