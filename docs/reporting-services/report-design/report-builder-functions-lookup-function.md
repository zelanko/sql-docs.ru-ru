---
title: Функция подстановки (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: e60e5bab-b286-4897-9685-9ff12703517d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 333c75f3ca10d1ed6ecd738a3dc76a32a53305c6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "65579572"
---
# <a name="report-builder-functions---lookup-function"></a>Функции построителя отчетов — функция Lookup
  Возвращает первое совпадающее значение для заданного имени из набора данных, содержащего пары «имя-значение».  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Lookup(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a>Параметры  
 *source_expression*  
 (**Variant**) Выражение, вычисляемое в текущей области и указывающее имя или ключ для поиска. Например, `=Fields!ProdID.Value`.  
  
 *destination_expression*  
 (**Variant**) Выражение, вычисляемое для каждой строки в наборе данных и указывающее имя или ключ для сопоставления. Например, `=Fields!ProductID.Value`.  
  
 *result_expression*  
 (**Variant**) Выражение, которое вычисляется для строки в наборе данных, где *source_expression* = *destination_expression*, и указывает возвращаемое значение. Например, `=Fields!ProductName.Value`.  
  
 *набор данных*  
 Константа, задающая имя набора данных в отчете. Например, «Продукты».  
  
## <a name="return"></a>Возвращает  
 Возвращает значение **Variant**или **Nothing** , если совпадения нет.  
  
## <a name="remarks"></a>Remarks  
 Функция **Lookup** позволяет извлечь значение из указанного набора данных, состоящего из пар "имя-значение" с отношением "один к одному". Например, для поля ID в таблице функция **Lookup** может быть использована для поиска соответствующего поля Name в наборе данных, не привязанном к области данных.  
  
 Функция**Lookup** выполняет следующие действия.  
  
-   Вычисляет исходное выражение в текущей области.  
  
-   Вычисляет целевое выражение для каждой строки указанного набора данных после применения фильтров с учетом заданных для него параметров сортировки.  
  
-   При первом совпадении исходного и целевого выражений вычисляет результирующее выражение для этой строки в наборе данных.  
  
-   Возвращает результирующее значение выражения.  
  
 Для получения множества значений по одному имени или ключевому полю, если существует отношение связь "один ко многим", пользуйтесь [функцией LookupSet (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-lookupset-function.md). Для вызова функции **Lookup** для набора значений используйте [функцию Multilookup (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-multilookup-function.md).  
  
 Применяются следующие ограничения:  
  
-   Функция**Lookup** вычисляется после применения всех выражений фильтров.  
  
-   Поддерживается только один уровень уточняющего запроса. Исходное, целевое и результирующее выражения не могут включать в себя ссылки на функцию уточняющего запроса.  
  
-   Исходное и результирующее выражения должны возвращать один и тот же тип данных. Возвращаемый тип совпадает с типом данных вычисленного результирующего выражения.  
  
-   Исходное, целевое и результирующее выражения не могут включать в себя ссылки на переменные отчета или группы.  
  
-   Функцию**Lookup** нельзя использовать в качестве выражения для следующих элементов отчета:  
  
    -   динамические строки соединения для источника данных;  
  
    -   вычисляемые поля в наборе данных;  
  
    -   параметры запроса в наборе данных;  
  
    -   фильтры в наборе данных;  
  
    -   параметры отчета;  
  
    -   Свойство Report.Language.  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Пример  
 В следующем примере предположим, что таблица привязана к набору данных, включающему в себя поле для идентификатора продукта ProductID. Отдельный набор данных с именем Product содержит соответствующий идентификатор продукта ID и его название Name.  
  
 В следующем выражении функция **Lookup** сравнивает значение ProductID со значением ID для каждой из строк набора данных Product и, при совпадении, возвращает значение поля Name для этой строки.  
  
```  
=Lookup(Fields!ProductID.Value, Fields!ID.Value, Fields!Name.Value, "Product")  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
