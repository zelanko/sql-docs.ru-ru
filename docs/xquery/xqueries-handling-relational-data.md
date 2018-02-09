---
title: "Запросы XQuery, обработка реляционных данных | Документы Microsoft"
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
- relational data [XQuery]
- XQuery, relational data
ms.assetid: 9812b71a-52ec-48a0-92f3-016a93660229
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 420caf1620974293f279e72892f0da2cad6a140b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="xqueries-handling-relational-data"></a>Запросы XQuery, обрабатывающие реляционные данные
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Задать запрос XQuery для **xml** столбца или переменной с помощью одного из [методов типа данных XML](../t-sql/xml/xml-data-type-methods.md). К ним относятся **query()**, **value()**, **exist()**, или **modify()**. Запрос XQuery выполняется для экземпляра XML, указанного в запросе, создающем XML-код.  
  
 XML-код, созданный в результате выполнения запроса XQuery, может включать значения, полученные от других переменных Transact-SQL или столбцов набора строк. Для связи реляционных данных в формате, отличном от XML, с итоговым XML-кодом в SQL Server в форме расширений XQuery реализованы следующие псевдофункции:  
  
-   **SQL: column()** функции  
  
-   **SQL: variable()** функции  
  
 Можно использовать эти расширения XQuery при указании запроса XQuery в **query()** метод **xml** тип данных. В результате **query()** метод может создать XML-ФАЙЛ, объединяющее данные из XML и не-**xml** типов данных.  
  
 Можно также использовать эти функции, при использовании **xml** методов типа данных **modify()**, **value()**, **query()**, и  **exist()**для получения реляционного значения внутри XML.  
  
 Дополнительные сведения см. в разделе [функции SQL: column() (XQuery)](../xquery/xquery-extension-functions-sql-column.md) и [функции SQL: variable() (XQuery)](../xquery/xquery-extension-functions-sql-variable.md).  
  
## <a name="see-also"></a>См. также  
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)   
 [Справочник по языку XQuery (SQL Server)](../xquery/xquery-language-reference-sql-server.md)   
 [Построение XML &#40; XQuery &#41;](../xquery/xml-construction-xquery.md)  
  
  
