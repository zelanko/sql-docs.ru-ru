---
title: Функция Multilookup (построитель отчетов) | Документация Майкрософт
description: Функция Multilookup возвращает набор первых подходящих значений для указанного набора имен из набора данных, содержащего пары "имя-значение", в построителе отчетов.
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 1fec079e-33b3-4e4d-92b3-6b4d06a49a77
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b8db1d2a7fe18264c81d7585e02babef65b3346d
ms.sourcegitcommit: b3a711a673baebb2ff10d7142b209982b46973ae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2020
ms.locfileid: "93364576"
---
# <a name="report-builder-functions---multilookup-function"></a>Функции построителя отчетов — функция Multilookup
  Возвращает набор первых подходящих значений для указанного набора имен из набора данных, содержащего пары «имя-значение».  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Multilookup(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a>Параметры  
 *source_expression*  
 ( **VariantArray** ) Выражение, вычисляемое в текущей области и указывающее набор имен или ключей для поиска. Например, для многозначного параметра `=Parameters!IDs.value`.  
  
 *destination_expression*  
 ( **Variant** ) Выражение, вычисляемое для каждой строки в наборе данных и указывающее имя или ключ для сопоставления. Например, `=Fields!ID.Value`.  
  
 *result_expression*  
 ( **Variant** ) Выражение, которое вычисляется для строки в наборе данных, где *source_expression* = *destination_expression* , и указывает возвращаемое значение. Например, `=Fields!Name.Value`.  
  
 *набор данных*  
 Константа, задающая имя набора данных в отчете. Например, «Colors».  
  
## <a name="return"></a>Возвращает  
 Возвращает значение **VariantArray** или **Nothing** , если совпадения нет.  
  
## <a name="remarks"></a>Remarks  
 Функция **Multilookup** служит для извлечения набора значений из набора данных, содержащего пары "имя-значение" со связью "один к одному". Функция **MultiLookup** является эквивалентом функции **Lookup** для набора имен или ключей. Например, для параметра с несколькими значениями на основе идентификаторов первичных ключей функция **Multilookup** может быть использована в выражении в текстовом поле таблицы для извлечения связанных значений из набора данных, не привязанного к параметру или таблице.  
  
 Функция **Multilookup** выполняет следующие действия.  
  
-   вычисляет исходное выражение в текущей области и создает массив объектов типа variant;  
  
-   для всех объектов массива вызывается [функция Lookup (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-lookup-function.md), а результаты добавляются к массиву возвращаемых значений;  
  
-   возвращает набор результатов.  
  
 Для извлечения единственного значения для указанного имени из набора данных, состоящего из пар "имя-значение" со связью "один к одному", используйте [функцию Lookup (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-lookup-function.md). Для извлечения нескольких значений для имени из набора данных, состоящего из пар "имя-значение" со связью "один ко многим", используйте [функцию LookupSet (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-lookupset-function.md).  
  
 Применяются следующие ограничения:  
  
-   Функция **Multilookup** вычисляется после применения всех критериев фильтра.  
  
-   Поддерживается только один уровень уточняющего запроса. Исходное, целевое и результирующее выражения не могут включать в себя ссылки на функцию уточняющего запроса.  
  
-   Исходное и результирующее выражения должны возвращать один и тот же тип данных.  
  
-   Исходное, целевое и результирующее выражения не могут включать в себя ссылки на переменные отчета или группы.  
  
-   Функцию **Multilookup** нельзя использовать в качестве выражения для следующих элементов отчета:  
  
    -   динамические строки соединения для источника данных;  
  
    -   вычисляемые поля в наборе данных;  
  
    -   параметры запроса в наборе данных;  
  
    -   фильтры в наборе данных;  
  
    -   параметры отчета;  
  
    -   Свойство Report.Language.  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="examples"></a>Примеры

### <a name="a-use-multilookup-function"></a>A. Использование функции MultiLookup
 Предположим, набор данных Category содержит поле CategoryList, которое содержит список идентификаторов категорий с разделителями-запятыми, например «2, 4, 2, 1».  
  
 Набор данных «CategoryNames» содержит идентификатор и название категории, как показано в следующей таблице.  
  
|ID|Имя|  
|--------|----------|  
|1|Accessories|  
|2|Bikes|  
|3|Clothing|  
|4|Components|  
  
 Для поиска имен, соответствующих списку идентификаторов, используйте функцию **Multilookup**. Сначала необходимо разбить список на массив строк, вызвать  функцию **Multilookup** для извлечения названий категорий и объединить результаты в строку.  
  
 Следующее выражение при помещении текстового поля в область данных, привязанную к набору данных Category, отображает «Bikes, Components, Bikes, Accessories».  
  
```  
=Join(MultiLookup(Split(Fields!CategoryList.Value,","),  
   Fields!CategoryID.Value,Fields!CategoryName.Value,"Category")),  
   ", ")  
```  
  
### <a name="b-use-multilookup-with-multivalue-parameter"></a>Б. Использование MultiLookup с многозначным параметром  
 Предположим, в наборе данных с именем ProductColors есть поле идентификатора цвета ColorID и поле значения цвета Color, как показано в следующей таблице.  
  
|ColorID|Color|  
|-------------|-----------|  
|1|Красный|  
|2|Синий|  
|3|Зеленый|  
  
 Предположим, параметр с несколькими значениями *MyColors* не привязан к доступным значениям набора данных. По умолчанию для параметра заданы значения 2 и 3. Следующее выражение при помещении в текстовое поле таблицы объединяет несколько выбранных значений параметра в список с разделителями-запятыми и отображает «Blue, Green».  
  
```  
=Join(MultiLookup(Parameters!MyColors.Value,Fields!ColorID.Value,Fields!Color.Value,"ProductColors"),", ")  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
