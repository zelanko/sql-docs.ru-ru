---
title: "Запросы XQuery, обработка реляционных данных | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7765f20211ebd1278136f198b6957d674c52871c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="xqueries-handling-relational-data"></a>Запросы XQuery, обрабатывающие реляционные данные
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Задать запрос XQuery для **xml** столбца или переменной с помощью одного из [методов типа данных XML](../t-sql/xml/xml-data-type-methods.md). К ним относятся **query()**, **value()**, **exist()**, или **modify()**. Запрос XQuery выполняется для экземпляра XML, указанного в запросе, создающем XML-код.  
  
 XML-код, созданный в результате выполнения запроса XQuery, может включать значения, полученные от других переменных Transact-SQL или столбцов набора строк. Для связи реляционных данных в формате, отличном от XML, с итоговым XML-кодом в SQL Server в форме расширений XQuery реализованы следующие псевдофункции:  
  
-   **SQL: column()** функции  
  
-   **SQL: variable()** функции  
  
 Можно использовать эти расширения XQuery при указании запроса XQuery в **query()** метод **xml** тип данных. В результате **query()** метод может создать XML-ФАЙЛ, объединяющее данные из XML и не-**xml** типов данных.  
  
 Можно также использовать эти функции, при использовании **xml** методов типа данных **modify()**, **value()**, **query()**, и  **exist()**для получения реляционного значения внутри XML.  
  
 Дополнительные сведения см. в разделе [функции SQL: column() (XQuery)](../xquery/xquery-extension-functions-sql-column.md) и [функции SQL: variable() (XQuery)](../xquery/xquery-extension-functions-sql-variable.md).  
  
## <a name="see-also"></a>См. также:  
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)   
 [Справочник по языку XQuery (SQL Server)](../xquery/xquery-language-reference-sql-server.md)   
 [Построение XML &#40; XQuery &#41;](../xquery/xml-construction-xquery.md)  
  
  
