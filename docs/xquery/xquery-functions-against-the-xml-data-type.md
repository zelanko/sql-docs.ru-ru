---
title: Функции XQuery для типа данных XML | Документация Майкрософт
description: Сведения о функциях XQuery, которые поддерживаются для использования с типом данных XML.
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, functions
- xml data type [SQL Server], XQuery
- functions [SQL Server], XQuery
ms.assetid: 8df0877d-a03f-4ca9-b84e-908c4bb42b5e
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e92148b5a85ced147599eafe09156cf41c47021
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037017"
---
# <a name="xquery-functions-against-the-xml-data-type"></a>Функции XQuery для типа данных xml
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  В этом разделе и его подразделах описываются функции, которые можно использовать при указании XQuery для типа данных **XML** . Спецификации W3C см. в разделе [http://www.w3.org/TR/2004/WD-xpath-functions-20040723](https://go.microsoft.com/fwlink/?LinkId=4873) .  
  
 Функции XQuery принадлежат http://www.w3.org/2004/07/xpath-functions пространству имен. Спецификации W3C используют префикс пространства имен «fn:» для описания этих функций. При использовании функций нет необходимости явно указывать префикс пространства имен «fn:». По этой причине, а также для удобства чтения префиксы пространства имен, как правило, не используются в данной документации.  
  
 В следующей таблице перечислены функции XQuery, которые поддерживаются для типа данных **XML**.  
  
|Категория|Имя функции|  
|--------------|-------------------|  
|[Функции с числовыми значениями]()|[толок](../xquery/numeric-values-functions-ceiling.md)|  
||[фабрич](../xquery/numeric-values-functions-floor.md)|  
||[округло](../xquery/numeric-values-functions-round.md)|  
|[Функции XQuery для строковых значений]()|[concat](../xquery/functions-on-string-values-concat.md)|  
||[contains](../xquery/functions-on-string-values-contains.md)|  
||[substring](../xquery/functions-on-string-values-substring.md)|  
||[Функция нижнего регистра &#40;XQuery&#41;](../xquery/functions-on-string-values-lower-case.md)|  
||[Длина строки](../xquery/functions-on-string-values-string-length.md)|  
||[Функция верхнего регистра &#40;XQuery&#41;](../xquery/functions-on-string-values-upper-case.md)|  
|Функции над значениями типа Boolean|[not](../xquery/functions-on-boolean-values-not-function.md) (не);|  
|[Функции на узлах]()|[number](../xquery/functions-on-nodes-number.md)|  
||[Функция local-name (XQuery)](../xquery/functions-on-nodes-local-name.md)|  
||[Функция namespace-uri (XQuery)](../xquery/functions-on-nodes-namespace-uri.md)|  
|[Функции контекста]()|[last](../xquery/context-functions-last-xquery.md)|  
||[position](../xquery/context-functions-position-xquery.md)|  
|[Функции над последовательностями]()|[empty](../xquery/functions-on-sequences-empty.md)|  
||[distinct-values](../xquery/functions-on-sequences-distinct-values.md)|  
||[Функция id (XQuery)](../xquery/functions-on-sequences-id.md)|  
|[Агрегатные функции &#40;&#41;XQuery ]()|[count](../xquery/aggregate-functions-count.md)|  
||[avg](../xquery/aggregate-functions-avg.md)|  
||[min](../xquery/aggregate-functions-min.md)|  
||[max](../xquery/aggregate-functions-max.md)|  
||[sum](../xquery/aggregate-functions-sum.md)|  
|[Функции конструктора &#40;XQuery&#41;](../xquery/constructor-functions-xquery.md)|[Функции-конструкторы](../xquery/constructor-functions-xquery.md)|  
|[Функции метода доступа к данным](../xquery/data-accessor-functions.md)|[string](../xquery/data-accessor-functions-string-xquery.md)|  
||[data](../xquery/data-accessor-functions-data-xquery.md)|  
|[Логические функции конструктора &#40;XQuery&#41;]()|[true (XQuery)](../xquery/boolean-constructor-functions-true-xquery.md)|  
||[Функция false (XQuery)](../xquery/boolean-constructor-functions-false-xquery.md)|  
|[Функции, связанные с QName &#40;XQuery&#41;](./functions-related-to-qnames-expanded-qname.md)|[expanded-QName (XQuery)](../xquery/functions-related-to-qnames-expanded-qname.md)|  
||[local-name-from-QName (XQuery)](../xquery/functions-related-to-qnames-local-name-from-qname.md)|  
||[namespace-uri-from-QName (XQuery)](../xquery/functions-related-to-qnames-namespace-uri-from-qname.md)|  
|[Функции расширения запросов XQuery в SQL Server](./xquery-extension-functions-sql-column.md)|[функция SQL: column () (XQuery)](../xquery/xquery-extension-functions-sql-column.md)|  
||[функция sql:variable() (XQuery)](../xquery/xquery-extension-functions-sql-variable.md)|  
  
## <a name="see-also"></a>См. также:  
 [методов типа данных xml](../t-sql/xml/xml-data-type-methods.md)   
 [Справочник по языку XQuery (SQL Server)](../xquery/xquery-language-reference-sql-server.md)   
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)  
  
