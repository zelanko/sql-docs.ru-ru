---
title: "Правила использования методов типа данных xml | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], methods
- methods [XML in SQL Server]
ms.assetid: 1a483aa1-42de-4c88-a4b8-c518def3d496
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e02d385d699c1c26d44f2e7383584416c2d9dd5c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="guidelines-for-using-xml-data-type-methods"></a>Правила использования методов типа данных XML
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом разделе описаны рекомендации по использованию **xml** методов типа данных.  
  
## <a name="the-print-statement"></a>Инструкция PRINT  
 **Xml** методов типа данных не может использоваться в инструкции PRINT, как показано в следующем примере. **Xml** методов типа данных обрабатываются как подзапросы, а вложенные запросы недопустимы в инструкции PRINT. В результате следующий пример возвращает ошибку:  
  
```  
DECLARE @x xml  
SET @x = '<root>Hello</root>'  
PRINT @x.value('/root[1]', 'varchar(20)') -- will not work because this is treated as a subquery (select top 1 col from table)   
```  
  
 Решением этой проблемы является вначале присвоить результат **value()** метод переменной **xml** введите, а потом использовать переменную в запросе.  
  
```  
DECLARE @x xml  
DECLARE @c varchar(max)  
SET @x = '<root>Hello</root>'  
SET @c = @x.value('/root[1]', 'varchar(11)')  
PRINT @c                                                        
```  
  
## <a name="the-group-by-clause"></a>Предложение GROUP BY  
 **Xml** методов типа данных внутри обрабатываются как подзапросы. Поскольку GROUP BY требует скалярного выражения и не допускает статистических вычислений или подзапросов, нельзя указать **xml** методов типа данных в предложении GROUP BY. Решением является вызов пользовательской функции, которая использует методы XML.  
  
## <a name="reporting-errors"></a>Ведение отчетов об ошибках  
 При сообщении об ошибках, **xml** методов типа данных вызывают ошибки в следующем формате:  
  
```  
Msg errorNumber, Level levelNumber, State stateNumber:  
XQuery [database.table.method]: description_of_error  
```  
  
 Например:  
  
```  
Msg 2396, Level 16, State 1:  
XQuery [xmldb_test.xmlcol.query()]: Attribute may not appear outside of an element  
```  
  
## <a name="singleton-checks"></a>Одноэлементные проверки  
 Шаги определения расположения данных, параметры функций и операторы, которым нужны единственные значения, возвращают ошибку, если компилятор не может определить, будет ли в период выполнения гарантирована единственность элемента. Эта проблема часто возникает при работе с нетипизированными данными. Например, при уточняющем запросе атрибута необходима информация о единственном родительском элементе. Указать порядковый номер, выбирающий единственный родительский узел, недостаточно. Вычисление **node()**-**value()** сочетание, чтобы извлечь значения атрибутов могут не требовать указание порядкового номера. Это показано в следующем примере.  
  
### <a name="example-known-singleton"></a>Пример: Известный единственный экземпляр  
 В этом примере **nodes()** метод создает отдельную строку для каждого <`book`> элемент. **Value()** метод, который вычисляется на <`book`> узел извлекает значение @genre и, будучи атрибутом, является Singleton-классом.  
  
```  
SELECT nref.value('@genre', 'varchar(max)') LastName  
FROM   T CROSS APPLY xCol.nodes('//book') AS R(nref)  
```  
  
 Чтобы проверить типы типизированного XML, используется XML-схема. Если в XML-схеме узел указан как единственный, компилятор это учитывает, и ошибки не возникают. В противном случае необходим порядковый номер, выбирающий единственный узел. В частности, применение оси descendant-or-self (/ /) оси, таких как/book / / title, ослабляет вывод единственности \<title > элемент, даже если схема XML определяет именно так. Таким образом, следует переписать его как (/book//title)[1].  
  
 Важно знать о различии между выражениями //first-name[1] и (//first-name)[1] при проверке типов. Первое из них возвращает последовательность \<-имя > узлов, в которых каждый узел является самым левым действием \<первый name > среди одноуровневых узлов. Второе возвращает первый единственный экземпляр \<первый name > узла в порядке документа в экземпляре XML.  
  
### <a name="example-using-value"></a>Пример: Использование метода value()  
 Следующий запрос данных из нетипизированного XML-столбца приводит к статической ошибке компиляции. Это вызвано **value()** ожидает единственный узел как первый аргумент и компилятор не может определить, является ли только один \<Фамилия > узел будет выполняться во время выполнения:  
  
```  
SELECT xCol.value('//author/last-name', 'nvarchar(50)') LastName  
FROM   T  
```  
  
 Вот решение этой проблемы, которое возможно как вариант:  
  
```  
SELECT xCol.value('//author/last-name[1]', 'nvarchar(50)') LastName  
FROM   T  
```  
  
 Однако это решение не устраняет ошибку, потому что в каждом экземпляре XML могут содержаться несколько узлов <`author`>. Следующий вариант работает:  
  
```  
SELECT xCol.value('(//author/last-name/text())[1]', 'nvarchar(50)') LastName  
FROM   T  
```  
  
 Этот запрос возвращает значение первого элемента `<last-name>` в каждом из экземпляров XML.  
  
## <a name="see-also"></a>См. также:  
 [Методы для типа данных XML](../../t-sql/xml/xml-data-type-methods.md)  
  
  

