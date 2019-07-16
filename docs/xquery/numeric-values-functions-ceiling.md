---
title: Функция CEILING (XQuery) | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
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
  
## <a name="remarks"></a>Примечания  
 Если тип *$arg* является одним из трех базовых числовых типов, **xs: float**, **xs: double**, или **xs: decimal**, тип возвращаемого значения совпадает со значением *$arg* типа.  
  
 Если тип *$arg* — тип, который является производным от одного из числовых типов, тип возвращаемого значения будет иметь базовый числовой тип.  
  
 Если входные данные функций fn: FLOOR, fn: CEILING или fn: Round **xdt: untypedAtomic**, неявно приведен к **xs: double**.  
  
 Использование любого другого типа вызовет статическую ошибку.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** -столбец базы данных AdventureWorks.  
  
### <a name="a-using-the-ceiling-xquery-function"></a>A. Использование функции XQuery ceiling()  
 Для модели продуктов 7 этот запрос вернет список адресов цехов, участвующих в производстве продуктов этой модели. Для каждого адреса цеха запрос вернет идентификатор адреса, рабочее время и размер территории, если они указаны. В запросе используется **ceiling** функция, возвращающая рабочего времени в виде значения типа **десятичное**.  
  
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
  
-   **Инструкции** — **xml** столбец типа. Таким образом [метода query() (тип данных XML)](../t-sql/xml/query-method-xml-data-type.md) используется для определения запроса XQuery. Инструкция XQuery задана как аргумент метода query.  
  
-   **для... возвращают** — конструкция цикла. В запросе **для** цикла определяет список \<расположение > элементы. Для каждого адреса цеха **возвращают** инструкции в **для** цикла описывает XML будет создан:  
  
    -   Объект \<расположение > элемент, имеющий атрибуты LocationID и LaborHrs. Соответствующее выражение в фигурных скобках ({ }) получает запрашиваемые значения из документа.  
  
    -   {$i/@LotSize } Выражение получает значение атрибута LotSize из документа, если он имеется.  
  
    -   Это результат:  
  
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
  
-   **Ceiling()** функция сопоставляет все целочисленные значения типу xs: decimal.  
  
## <a name="see-also"></a>См. также  
 [Функция FLOOR &#40;XQuery&#41;](../xquery/numeric-values-functions-floor.md)   
 [Функция Round &#40;XQuery&#41;](../xquery/numeric-values-functions-round.md)  
  
  
