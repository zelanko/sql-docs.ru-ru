---
title: "Привязка реляционных данных внутри XML-данных | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- relational data binding [SQL Server]
- XML [SQL Server], binding relational data
- xml data type [SQL Server], relational data binding
- binding relational data [XML in SQL Server]
- variables [XML in SQL Server], relational data binding
- columns [XML in SQL Server], relational data binding
ms.assetid: 03d013a9-b53f-46c3-9628-da77f099c74a
caps.latest.revision: "36"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef249a7482610419873604637290cab3ef18e34b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="binding-relational-data-inside-xml-data"></a>Привязка реляционных данных внутри XML-данных
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Можно указать [методы типа данных xml](../../t-sql/xml/xml-data-type-methods.md) от **xml** переменной или столбце типа данных. Например [запрос &#40; &#41; Метод &#40; тип данных xml &#41; ](../../t-sql/xml/query-method-xml-data-type.md) выполняет заданный запрос XQuery к экземпляру XML. При построении XML таким способом может понадобиться ввести значение их столбца с типом данных, отличным от XML или переменной Transact-SQL. Данный процесс называется привязкой реляционных данных внутри XML.  
  
 Для привязки реляционных данных с типом, отличным от XML, внутри XML компонент SQL Server Database Engine обладает следующими псевдофункциями:  
  
-   [SQL: column() &#40; &#41; Функция &#40; XQuery &#41; ](../../xquery/xquery-extension-functions-sql-column.md) Позволяет использовать значения из реляционного столбца в выражении XQuery или XML DML.  
  
-   [SQL: variable &#40; &#41; Функция &#40; XQuery &#41; ](../../xquery/xquery-extension-functions-sql-variable.md) . Позволяет использовать значения переменной SQL в выражении XQuery или XML DML.  
  
 Можно использовать эти функции с **xml** методов типа данных каждый раз при необходимости получения реляционного значения внутри XML.  
  
 Эти функции нельзя использовать со ссылочными данными в столбцах или переменных типа **xml**, CLR определяемого пользователем типа datetime, smalldatetime, **текст**, **ntext**, **sql_variant**, и **изображения** типов.  
  
 Однако данная привязка доступна только для чтения, то есть нельзя записывать данные в столбцы, использующие эти функции. Например, sql:variable("@x") =»*некоторое выражение «* не допускается.  
  
## <a name="example-cross-domain-query-using-sqlvariable"></a>Пример: Запрос между доменами с помощью SQL: variable()  
 В этом примере показано, как **SQL: variable()** позволяет приложению подготовить параметризованный запрос. ISBN-номер передается в с помощью переменной SQL @isbn. Заменив константу с **SQL: variable()**, запрос может использоваться для поиска любого ISBN-номера, а не только с ISBN-0-7356-1588-2.  
  
```  
DECLARE @isbn varchar(20)  
SET     @isbn = '0-7356-1588-2'  
SELECT  xCol  
FROM    T  
WHERE   xCol.exist ('/book/@ISBN[. = sql:variable("@isbn")]') = 1  
```  
  
 **SQL: column()** можно использовать так же, как и дает дополнительные преимущества. Для повышения эффективности могут использоваться индексы столбца — это решает оптимизатор запросов на основе траты ресурсов. В вычисляемом столбце можно хранить свойство, для которого было выполнено продвижение.  
  
## <a name="see-also"></a>См. также:  
 [Методы для типа данных XML](../../t-sql/xml/xml-data-type-methods.md)  
  
  
