---
title: Функция ceiling (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:ceiling function
- ceiling function [XQuery]
ms.assetid: 594f1dd0-3c27-41b3-b809-9ce6714c5a97
author: rothja
ms.author: jroth
ms.openlocfilehash: fe18f488b83c1a8c9236c642751c1dc80bfe7e6c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67946577"
---
# <a name="numeric-values-functions---ceiling"></a>Функции с числовыми значениями — ceiling 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает наименьшее целое число, которое не меньше значения, переданного как аргумент функции. Если аргумент представляет собой пустую последовательность, то возвращается пустая последовательность.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:ceiling ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Число, к которому применяется функция.  
  
## <a name="remarks"></a>Remarks  
 Если тип *$arg* является одним из трех числовых базовых типов, **xs: float**, **xs: double**или **xs: decimal**, возвращаемый тип совпадает с типом *$arg* .  
  
 Если тип *$arg* является типом, производным от одного из числовых типов, то возвращаемым типом является базовый числовой тип.  
  
 Если входными данными для функций Fn: Floor, fn: Ceiling или Fn: Round является **xdt: untypedAtomic**, то он неявно приводится к типу **xs: Double**.  
  
 Использование любого другого типа вызовет статическую ошибку.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в базе данных AdventureWorks.  
  
### <a name="a-using-the-ceiling-xquery-function"></a>A. Использование функции XQuery ceiling()  
 Для модели продуктов 7 этот запрос вернет список адресов цехов, участвующих в производстве продуктов этой модели. Для каждого адреса цеха запрос вернет идентификатор адреса, рабочее время и размер территории, если они указаны. Запрос использует функцию **Ceiling** для возврата рабочих часов в качестве значений типа **Decimal**.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
     for $i in /AWMI:root/AWMI:Location  
     return   
       <Location LocationID="{ $i/@LocationID }"   
                   LaborHrs="{ ceiling($i/@LaborHours) }" >  
                    {   
                      $i/@LotSize  
                    }    
       </Location>  
') AS Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Префикс пространства имен AWMI означает «Adventure Works Manufacturing Instructions» (производственные инструкции Adventure Works). Этот префикс именует то же пространство имен, что используется и в документе, к которому строится запрос.  
  
-   **Инструкции** — это столбец типа **XML** . Поэтому для указания XQuery используется [метод query () (тип данных XML)](../t-sql/xml/query-method-xml-data-type.md) . Инструкция XQuery задана как аргумент метода query.  
  
-   **для... Return** является конструкцией цикла. В запросе цикл **for** определяет список \<расположений> элементов. Для каждого расположения рабочего центра оператор **return** в цикле **for** описывает создаваемый XML:  
  
    -   Элемент \<Location>, содержащий атрибуты LocationID и лаборхрс. Соответствующее выражение в фигурных скобках ({ }) получает запрашиваемые значения из документа.  
  
    -   Выражение {$i/@LotSize } извлекает из документа атрибут LotSize, если он есть.  
  
    -   Результат:  
  
```  
ProductModelID Result    
-------------- ------------------------------------------------------  
7      <Location LocationID="10" LaborHrs="3" LotSize="100"/>  
       <Location LocationID="20" LaborHrs="2" LotSize="1"/>     
       <Location LocationID="30" LaborHrs="1" LotSize="1"/>     
       <Location LocationID="45" LaborHrs="1" LotSize="20"/>  
       <Location LocationID="60" LaborHrs="3" LotSize="1"/>     
       <Location LocationID="60" LaborHrs="4" LotSize="1"/>  
```  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   Функция **ceiling ()** сопоставляет все целочисленные значения с типом xs: Decimal.  
  
## <a name="see-also"></a>См. также:  
 [Функция Floor &#40;XQuery&#41;](../xquery/numeric-values-functions-floor.md)   
 [Функция Round &#40;XQuery&#41;](../xquery/numeric-values-functions-round.md)  
  
  
