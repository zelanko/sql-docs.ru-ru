---
title: "Справочник по языку XQuery (SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- XQuery
- XQuery, about XQuery
- xml data type [SQL Server], XQuery
- XML [SQL Server], XQuery
- queries [XML in SQL Server], XQuery
ms.assetid: 8a69344f-2990-4357-8160-cb26aac95b91
caps.latest.revision: "51"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 4c13cc549ad05caf3f866f5e1574033b350bdd47
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="xquery-language-reference-sql-server"></a>Справочник по языку XQuery (SQL Server)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[tsql](../includes/tsql-md.md)]поддерживает подмножество языка XQuery, который используется для выполнения запросов к **xml** тип данных. Эта реализация XQuery совпадает с рабочим эскизом XQuery на июль 2004 г. Язык разрабатывается консорциумом World Wide Web Consortium (W3C) с участием всех основных поставщиков баз данных, а также корпорации Майкрософт. Так как спецификации W3C могут быть подвержены изменениям в будущем, перед тем как стать рекомендациями W3C, эта реализация может отличаться от конечной рекомендации. Данный подраздел охватывает семантику и синтаксис поднабора XQuery, который поддерживается в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Дополнительные сведения см. в разделе [спецификация языка W3C XQuery 1.0](http://go.microsoft.com/fwlink/?LinkId=48846).  
  
 XQuery является языком, который может выполнять запросы к структурированным или полуструктурированным XML-данным. С **xml** поддержке в типа данных [!INCLUDE[ssDE](../includes/ssde-md.md)], документы могут храниться в базе данных и запрашиваться при помощи языка XQuery.  
  
 Язык XQuery основан на существующем языке запросов XPath с дополнительной улучшенной поддержкой итераций, результатов сортировки и возможности конструировать необходимые структуры XML. Язык XQuery работает с моделью данных XQuery. Это абстракция XML-документов и результатов XQuery, которые могут быть типизированными и нетипизированными. Сведения о типе основываются на типах, предоставляемых языком XML-схем W3C. Если нет доступных сведений по типам, XQuery считает данные нетипизированными. Это похоже на то, как XPath версии 1.0 обрабатывает XML.  
  
 Для запроса к экземпляру XML, который хранится в переменной или столбце типа **xml** , можно использовать [методы типа данных xml](../t-sql/xml/xml-data-type-methods.md). Например, можно объявить переменную **xml** введите и запрашивать его, используя **query()** метод **xml** тип данных.  
  
```  
DECLARE @x xml  
SET @x = '<ROOT><a>111</a></ROOT>'  
SELECT @x.query('/ROOT/a')  
```  
  
 В следующем примере запрос адресован столбцу Instructions типа **xml** типа в таблице ProductModel в базе данных AdventureWorks.  
  
```  
SELECT Instructions.query('declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";           
    /AWMI:root/AWMI:Location[@LocationID=10]  
') as Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Запрос XQuery включает объявление пространства имен, `declare namespace``AWMI=...`, а также выражение запроса `/AWMI:root/AWMI:Location[@LocationID=10]`.  
  
 Обратите внимание, что запрос XQuery задан для столбца Instructions **xml** типа. [Метода query()](../t-sql/xml/query-method-xml-data-type.md) XML-данных тип используется для определения запроса XQuery.  
  
 В следующей таблице перечисляются соответствующие темы, которые могут помочь в понимании реализации XQuery в [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)|Объясняется поддержка для **xml**в тип данных [!INCLUDE[ssDE](../includes/ssde-md.md)] и методы, которые можно использовать для этого типа данных. **Xml** тип данных, форм, модель данных ввода XQuery, на которой выполняются выражения XQuery.|  
|[Коллекции XML-схем (SQL Server)](../relational-databases/xml/xml-schema-collections-sql-server.md)|Описывается, как хранящиеся в базе данных экземпляры XML могут быть типизированы. Это означает, что можно связать коллекцию XML-схем с **xml** тип столбца. Все экземпляры, хранящиеся в столбце, проверяются и типизируются схемой в коллекции и предоставляют типизированные сведения для XQuery.|  
|||  
  
> [!NOTE]  
>  Организация этого раздела основана на спецификации рабочего эскиза XQuery корпорации World Wide Web Consortium (W3C). Некоторые диаграммы, приведенные в этом разделе, взяты из спецификации. В этом разделе сравнивается реализация Microsoft XQuery со спецификацией W3C, описывается, чем Microsoft XQuery отличается от W3C, и указывается, какие возможности W3C не поддерживаются. Спецификация W3C доступна на [http://www.w3.org/TR/2004/WD-xquery-20040723](http://go.microsoft.com/fwlink/?LinkId=48846).  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Основы XQuery](../xquery/xquery-basics.md)|Приводится общий обзор основных понятий XQuery, а также вычисления выражений (статический и динамический контекст), атомизации, действительного логического значения, системы типов XQuery, последовательного сравнения типов и обработки ошибок.|  
|[Выражения XQuery](../xquery/xquery-expressions.md)|Описываются основные выражения XQuery, выражения пути, выражения последовательности, логические выражения и выражения арифметического сравнения, конструкция XQuery, выражения FLWOR, условные и количественные выражения, а также различные выражения типов последовательностей.|  
|[Модули и Прологи &#40; XQuery &#41;](../xquery/modules-and-prologs-xquery.md)|Введение в XQuery.|  
|[Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)|Описывается список поддерживаемых функций XQuery.|  
|[Операторы XQuery для типа данных XML](../xquery/xquery-operators-against-the-xml-data-type.md)|Описываются поддерживаемые операторы XQuery.|  
|[Дополнительные образцы запросов XQuery для типа данных XML](../xquery/additional-sample-xqueries-against-the-xml-data-type.md)|Приводятся дополнительные образцы запросов XQuery.|  
  
## <a name="see-also"></a>См. также:  
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)   
 [Коллекции XML-схем (SQL Server)](../relational-databases/xml/xml-schema-collections-sql-server.md)   
 [Примеры массового импорта и экспорта XML-документов (SQL Server)](../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
  
