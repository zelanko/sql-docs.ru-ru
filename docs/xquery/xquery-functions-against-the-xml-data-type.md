---
title: Функции XQuery для типа данных xml | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- XQuery, functions
- xml data type [SQL Server], XQuery
- functions [SQL Server], XQuery
ms.assetid: 8df0877d-a03f-4ca9-b84e-908c4bb42b5e
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: db1906027692ec40974668f48521588b2231cebd
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37997116"
---
# <a name="xquery-functions-against-the-xml-data-type"></a>Функции XQuery для типа данных xml
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом разделе и его подразделах описываются функции, которые можно использовать при указании запроса XQuery к **xml** тип данных. Спецификации W3C см. в разделе [ http://www.w3.org/TR/2004/WD-xpath-functions-20040723 ](http://go.microsoft.com/fwlink/?LinkId=4873).  
  
 Функции XQuery принадлежат к http://www.w3.org/2004/07/xpath-functions пространства имен. Спецификации W3C используют префикс пространства имен «fn:» для описания этих функций. При использовании функций нет необходимости явно указывать префикс пространства имен «fn:». По этой причине, а также для удобства чтения префиксы пространства имен, как правило, не используются в данной документации.  
  
 В следующей таблице перечислены функции XQuery, поддерживаемые для **xml**тип данных.  
  
|Категория|Имя функции|  
|--------------|-------------------|  
|[Функции для числовых значений](http://msdn.microsoft.com/library/d5740a32-b174-43b9-b64d-1cc6edc50cff)|[верхний предел](../xquery/numeric-values-functions-ceiling.md)|  
||[функция FLOOR](../xquery/numeric-values-functions-floor.md)|  
||[Округление](../xquery/numeric-values-functions-round.md)|  
|[Функции XQuery для строковых значений](http://msdn.microsoft.com/library/2dccefef-5d90-4f56-bda7-4c1954d8a730)|[Concat](../xquery/functions-on-string-values-concat.md)|  
||[содержит](../xquery/functions-on-string-values-contains.md)|  
||[SUBSTRING](../xquery/functions-on-string-values-substring.md)|  
||[LOWER-Case, функция &#40;XQuery&#41;](../xquery/functions-on-string-values-lower-case.md)|  
||[Длина строки](../xquery/functions-on-string-values-string-length.md)|  
||[Функции Upper-case &#40;XQuery&#41;](../xquery/functions-on-string-values-upper-case.md)|  
|Функции над значениями типа Boolean|[не](../xquery/functions-on-boolean-values-not-function.md)|  
|[Функции с узлами](http://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)|[номер](../xquery/functions-on-nodes-number.md)|  
||[Функция local-name (XQuery)](../xquery/functions-on-nodes-local-name.md)|  
||[Функция namespace-uri (XQuery)](../xquery/functions-on-nodes-namespace-uri.md)|  
|[Функции контекста](http://msdn.microsoft.com/library/f7d8af33-9de9-450c-a667-23dee3129b5f)|[последний](../xquery/context-functions-last-xquery.md)|  
||[положение](../xquery/context-functions-position-xquery.md)|  
|[Функции над последовательностями](http://msdn.microsoft.com/library/672d2795-53ab-49c2-bf24-bc81a47ecd3f)|[пустой](../xquery/functions-on-sequences-empty.md)|  
||[уникальных значений](../xquery/functions-on-sequences-distinct-values.md)|  
||[Функция ID (XQuery)](../xquery/functions-on-sequences-id.md)|  
|[Агрегатные функции &#40;XQuery&#41;](http://msdn.microsoft.com/library/be647ef1-291e-4a5d-ab18-07c759efe176)|[count](../xquery/aggregate-functions-count.md)|  
||[AVG](../xquery/aggregate-functions-avg.md)|  
||[мин.](../xquery/aggregate-functions-min.md)|  
||[max](../xquery/aggregate-functions-max.md)|  
||[Сумма](../xquery/aggregate-functions-sum.md)|  
|[Функции-конструкторы &#40;XQuery&#41;](../xquery/constructor-functions-xquery.md)|[Функции-конструкторы](../xquery/constructor-functions-xquery.md)|  
|[Функции метода доступа к данным](../xquery/data-accessor-functions.md)|[строка](../xquery/data-accessor-functions-string-xquery.md)|  
||[data](../xquery/data-accessor-functions-data-xquery.md)|  
|[Функции логического конструктора &#40;XQuery&#41;](http://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)|[Функция true (XQuery)](../xquery/boolean-constructor-functions-true-xquery.md)|  
||[Функция false (XQuery)](../xquery/boolean-constructor-functions-false-xquery.md)|  
|[Функции, связанные с QName &#40;XQuery&#41;](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)|[expanded-QName (XQuery)](../xquery/functions-related-to-qnames-expanded-qname.md)|  
||[local-name-from-QName (XQuery)](../xquery/functions-related-to-qnames-local-name-from-qname.md)|  
||[пространство имен uri-from-QName (XQuery)](../xquery/functions-related-to-qnames-namespace-uri-from-qname.md)|  
|[Функции расширения XQuery для SQL Server](http://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)|[функция SQL: column() (XQuery)](../xquery/xquery-extension-functions-sql-column.md)|  
||[функция SQL: variable() (XQuery)](../xquery/xquery-extension-functions-sql-variable.md)|  
  
## <a name="see-also"></a>См. также  
 [методов типа данных xml](../t-sql/xml/xml-data-type-methods.md)   
 [Справочник по языку XQuery (SQL Server)](../xquery/xquery-language-reference-sql-server.md)   
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)  
  
  
