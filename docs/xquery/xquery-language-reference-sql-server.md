---
title: Ссылка на язык Хкуири (сервер S'L) Документы Майкрософт
description: Узнайте о языке X-Кери для сервера S'L и просмотрите полную ссылку на язык.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
helpviewer_keywords:
- XQuery
- XQuery, about XQuery
- xml data type [SQL Server], XQuery
- XML [SQL Server], XQuery
- queries [XML in SQL Server], XQuery
ms.assetid: 8a69344f-2990-4357-8160-cb26aac95b91
author: rothja
ms.author: jroth
ms.openlocfilehash: 35a1418e416e32ab5b8dc9647c4a9aa24700b624
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388619"
---
# <a name="xquery-language-reference-sql-server"></a>Справочник по языку XQuery (SQL Server)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[tsql](../includes/tsql-md.md)]поддерживает подмножество языка X'еry, который используется для запроса типа данных **xml.** Эта реализация XQuery совпадает с рабочим эскизом XQuery на июль 2004 г. Язык разрабатывается консорциумом World Wide Web Consortium (W3C) с участием всех основных поставщиков баз данных, а также корпорации Майкрософт. Так как спецификации W3C могут быть подвержены изменениям в будущем, перед тем как стать рекомендациями W3C, эта реализация может отличаться от конечной рекомендации. Данный подраздел охватывает семантику и синтаксис поднабора XQuery, который поддерживается в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Для получения дополнительной информации, [см.](https://go.microsoft.com/fwlink/?LinkId=48846)  
  
 XQuery является языком, который может выполнять запросы к структурированным или полуструктурированным XML-данным. С помощью **xml-типа** [!INCLUDE[ssDE](../includes/ssde-md.md)]данных в базе данных документы могут храниться в базе данных, а затем запрашиваться с помощью X'''query.  
  
 Язык XQuery основан на существующем языке запросов XPath с дополнительной улучшенной поддержкой итераций, результатов сортировки и возможности конструировать необходимые структуры XML. Язык XQuery работает с моделью данных XQuery. Это абстракция XML-документов и результатов XQuery, которые могут быть типизированными и нетипизированными. Сведения о типе основываются на типах, предоставляемых языком XML-схем W3C. Если нет доступных сведений по типам, XQuery считает данные нетипизированными. Это похоже на то, как XPath версии 1.0 обрабатывает XML.  
  
 Для запроса экземпляра XML, хранящегося в переменной или столбце типа **xml,** [используются методы типа данных xml.](../t-sql/xml/xml-data-type-methods.md) Например, можно объявить переменную типа **xml** и запросить ее с помощью метода **запроса ()** типа данных **xml.**  
  
```sql
DECLARE @x xml  
SET @x = '<ROOT><a>111</a></ROOT>'  
SELECT @x.query('/ROOT/a')  
```  
  
 В следующем примере запрос указан в отношении столбца инструкций типа **xml** в таблице ProductModel в базе данных AdventureWorks.  
  
```sql
SELECT Instructions.query('declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";           
    /AWMI:root/AWMI:Location[@LocationID=10]  
') as Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 X'еry включает в себя `declare namespace``AWMI=...`декларацию пространства имен `/AWMI:root/AWMI:Location[@LocationID=10]`и выражение запроса.  
  
 Обратите внимание, что X-Керай указан в отношении столбца Инструкций типа **xml.** Метод [запроса ()](../t-sql/xml/query-method-xml-data-type.md) типа данных xml используется для указания X'ery.  
  
 В следующей таблице перечисляются соответствующие темы, которые могут помочь в понимании реализации XQuery в [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)|Объясняет поддержку типа данных **xml** [!INCLUDE[ssDE](../includes/ssde-md.md)] в методах, которые можно использовать в отношении этого типа данных. Тип данных **xml** формирует модель входных данных X'ury, на которой выполняются выражения X'ury.|  
|[Коллекции XML-схем (SQL Server)](../relational-databases/xml/xml-schema-collections-sql-server.md)|Описывается, как хранящиеся в базе данных экземпляры XML могут быть типизированы. Это означает, что вы можете связать коллекцию схем XML с столбцей типа **xml.** Все экземпляры, хранящиеся в столбце, проверяются и типизируются схемой в коллекции и предоставляют типизированные сведения для XQuery.|  
|||  
  
> [!NOTE]  
>  Организация этого раздела основана на спецификации рабочего эскиза XQuery корпорации World Wide Web Consortium (W3C). Некоторые диаграммы, приведенные в этом разделе, взяты из спецификации. В этом разделе сравнивается реализация Microsoft XQuery со спецификацией W3C, описывается, чем Microsoft XQuery отличается от W3C, и указывается, какие возможности W3C не поддерживаются. Спецификация W3C доступна [http://www.w3.org/TR/2004/WD-xquery-20040723](https://go.microsoft.com/fwlink/?LinkId=48846)по адресу .  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Основы языка XQuery](../xquery/xquery-basics.md)|Приводится общий обзор основных понятий XQuery, а также вычисления выражений (статический и динамический контекст), атомизации, действительного логического значения, системы типов XQuery, последовательного сравнения типов и обработки ошибок.|  
|[Выражения языка XQuery](../xquery/xquery-expressions.md)|Описываются основные выражения XQuery, выражения пути, выражения последовательности, логические выражения и выражения арифметического сравнения, конструкция XQuery, выражения FLWOR, условные и количественные выражения, а также различные выражения типов последовательностей.|  
|[Модули и прологи &#40;&#41;X-](../xquery/modules-and-prologs-xquery.md)|Введение в XQuery.|  
|[Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)|Описывается список поддерживаемых функций XQuery.|  
|[Сравнение операторов XQuery с XML-данными](../xquery/xquery-operators-against-the-xml-data-type.md)|Описываются поддерживаемые операторы XQuery.|  
|[Дополнительные примеры запросов на языке XQuery к XML-данным](../xquery/additional-sample-xqueries-against-the-xml-data-type.md)|Приводятся дополнительные образцы запросов XQuery.|  
  
## <a name="see-also"></a>См. также:  
 [XML данные &#40;&#41;сервера S'L](../relational-databases/xml/xml-data-sql-server.md)   
 [XML Schema Коллекции &#40;&#41;сервера S'L](../relational-databases/xml/xml-schema-collections-sql-server.md)   
 [Примеры массового импорта и экспорта XML-документов (SQL Server)](../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
  
