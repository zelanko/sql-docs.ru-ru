---
title: "Функция CEILING (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:ceiling function
- ceiling function [XQuery]
ms.assetid: 594f1dd0-3c27-41b3-b809-9ce6714c5a97
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f50d1816ea6adb7e11bbf583f37ca8e8b9176223
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="numeric-values-functions---ceiling"></a>Числовые значения функции — ceiling 
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
 Если тип *$arg* является одним из трех базовых числовых типов, **xs: float**, **xs: double**, или **xs: decimal**, тип возвращаемого значения совпадает со значением *$arg* типа.  
  
 Если тип *$arg* — тип, который является производным от одного из числовых типов, тип возвращаемого значения будет иметь базовый числовой тип.  
  
 Если входные данные функций fn: FLOOR, fn: CEILING или fn: Round — **xdt: untypedAtomic**, оно неявно приводится к **xs: double**.  
  
 Использование любого другого типа вызовет статическую ошибку.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
### <a name="a-using-the-ceiling-xquery-function"></a>A. Использование функции XQuery ceiling()  
 Для модели продуктов 7 этот запрос вернет список адресов цехов, участвующих в производстве продуктов этой модели. Для каждого адреса цеха запрос вернет идентификатор адреса, рабочее время и размер территории, если они указаны. В запросе используется **ceiling** функцию для возвращения рабочего времени в виде значений типа **десятичное**.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
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
  
-   **Инструкции** — **xml** тип столбца. Таким образом [метода query() (тип данных XML)](../t-sql/xml/query-method-xml-data-type.md) используется для определения запроса XQuery. Инструкция XQuery задана как аргумент метода query.  
  
-   **для... возвращают** — конструкция цикла. В запросе **для** цикл определяет список \<расположение > элементов. Для каждого адреса цеха **возвращают** инструкции в **для** цикла описывает XML должен быть создан:  
  
    -   Объект \<расположение > элемент, имеющий атрибуты LocationID и LaborHrs. Соответствующее выражение в фигурных скобках ({ }) получает запрашиваемые значения из документа.  
  
    -   {$i/@LotSize } Выражение получает значение атрибута LotSize из документа, если он имеется.  
  
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
  
-   **Ceiling()** функция сопоставляет все целочисленные значения типу xs: decimal.  
  
## <a name="see-also"></a>См. также  
 [FLOOR, функция &#40; XQuery &#41;](../xquery/numeric-values-functions-floor.md)   
 [Round, функция &#40; XQuery &#41;](../xquery/numeric-values-functions-round.md)  
  
  
