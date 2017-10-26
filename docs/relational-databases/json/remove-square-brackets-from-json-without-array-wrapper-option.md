---
title: "Удаление квадратных скобок из JSON — метод с использованием WITHOUT_ARRAY_WRAPPER | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WITHOUT_ARRAY_WRAPPER
ms.assetid: aa86c2d1-458e-465f-abfa-75470137d054
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: bf0d7645df22c9a7540650e3c7f2ca2d0db8e1cc
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="remove-square-brackets-from-json---withoutarraywrapper-option"></a>Удаление квадратных скобок из JSON — метод с использованием WITHOUT_ARRAY_WRAPPER
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Чтобы удалить квадратные скобки, в которые выходные данные JSON предложения **FOR JSON** заключаются по умолчанию, укажите параметр **WITHOUT_ARRAY_WRAPPER** . При применении к однострочному результату этот параметр позволяет создать в качестве выходных данных не массив, а единый объект JSON.

При применении к многострочному результату выходные данные не будут представлять собой действительный объект JSON в связи с использованием сразу нескольких компонентов и отсутствием квадратных скобок.  
  
## <a name="example-single-row-result"></a>Пример (однострочный результат)  
В следующем примере показаны выходные данные предложения **FOR JSON** с параметром **WITHOUT_ARRAY_WRAPPER** и без него.  
  
 **Запрос**  
  
```sql  
SELECT 2015 as year, 12 as month, 15 as day  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER 
```  

 **Результат** с параметром **WITHOUT_ARRAY_WRAPPER**  
  
```json  
{
    "year": 2015,
    "month": 12,
    "day": 15
} 
```  
  
 **Результат** (по умолчанию) без параметра **WITHOUT_ARRAY_WRAPPER**  
  
```json  
[{
    "year": 2015,
    "month": 12,
    "day": 15
}]
```  

## <a name="example-multiple-row-result"></a>Пример (многострочный результат)
Вот другой пример предложения **FOR JSON** с параметром **WITHOUT_ARRAY_WRAPPER** . В этом примере создается результат, состоящий из нескольких строк. Выходные данные не являются допустимым объектом JSON в связи с использованием сразу нескольких компонентов и отсутствием квадратных скобок.
  
 **Запрос**  
  
```sql  
SELECT TOP 3 SalesOrderNumber, OrderDate, Status  
FROM Sales.SalesOrderHeader  
ORDER BY ModifiedDate  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER 
```  
  
 **Результат** с параметром **WITHOUT_ARRAY_WRAPPER**  
  
```json  
{
    "SalesOrderNumber": "SO43662",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43661",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43660",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
} 
```  
  
 **Результат** (по умолчанию) без параметра **WITHOUT_ARRAY_WRAPPER**  
  
```json  
[{
    "SalesOrderNumber": "SO43662",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43661",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43660",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}]
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Большое количество определенных решений, варианты использования и рекомендации см. в разделе [записи в блогах о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) в SQL Server и базах данных SQL Azure с руководителем программ Microsoft (Jovan Popovic).
  
## <a name="see-also"></a>См. также:  
 [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  

