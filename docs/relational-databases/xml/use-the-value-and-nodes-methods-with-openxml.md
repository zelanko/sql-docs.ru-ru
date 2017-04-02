---
title: "Использование методов value() и nodes() совместно с OPENXML | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OpenXML, метод [XML в SQL Server]"
  - "value, метод [XML в SQL Server]"
  - "nodes, метод [XML в SQL Server]"
ms.assetid: c73dbe55-d685-42eb-b0ee-9f3c5b9d97f3
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# Использование методов value() и nodes() совместно с OPENXML
  Методы **value()** можно выполнять в инструкции **SELECT** в типе данных **xml** для создания набора строк извлеченных значений. Метод **nodes()** позволяет получить внутреннюю ссылку на каждый выбранный узел, которую можно использовать в дополнительных запросах. При создании набора строк из нескольких столбцов и, возможно, при высокой сложности используемых для этого выражений пути более эффективным подходом может оказаться сочетание методов **nodes()** и **value()**.  
  
 Метод **nodes()** позволяет получать экземпляры специального типа данных **xml**, для каждого из которых контекст сопоставлен с другим выбранным узлом. Этот вид экземпляра XML поддерживает методы **query()**, **value()**, **nodes()** и **exist()** и может быть использован в статистических функциях **count(\*)**. Все другие способы его использования приводят к ошибке.  
  
## Пример. Использование nodes()  
 Предположим, что требуется извлечь имена и фамилии авторов, которых зовут не «David». Кроме того, требуется извлечь эту информацию как набор строк, содержащий два столбца: FirstName и LastName. Используя методы **nodes()** и **value()**, можно сделать это следующим образом:  
  
```  
SELECT nref.value('(first-name/text())[1]', 'nvarchar(50)') FirstName,  
       nref.value('(last-name/text())[1]', 'nvarchar(50)') LastName  
FROM   T CROSS APPLY xCol.nodes('//author') AS R(nref)  
WHERE  nref.exist('first-name[. != "David"]') = 1  
```  
  
 В данном примере метод `nodes('//author')` получает набор строковых ссылок на элементы `<author>` каждого экземпляра XML. Чтобы получить имена и фамилии авторов, вызываются методы **value()** относительно этих ссылок.  
  
 SQL Server 2000 позволяет создать набор строк на основе экземпляра XML при помощи метода **OpenXml()**. При этом можно указать реляционную схему набора строк и способ сопоставления значений экземпляра XML со столбцами набора строк.  
  
## Пример. Использование OpenXml() с типом данных xml  
 Запрос из предыдущего примера можно переписать с методом **OpenXml()** так, как показано ниже. С этой целью создается курсор, считывающий каждый экземпляр XML в переменную XML и вызывающий для нее метод OpenXml():  
  
```  
DECLARE name_cursor CURSOR  
FOR  
   SELECT xCol   
   FROM   T  
OPEN name_cursor  
DECLARE @xmlVal XML  
DECLARE @idoc int  
FETCH NEXT FROM name_cursor INTO @xmlVal  
  
WHILE (@@FETCH_STATUS = 0)  
BEGIN  
   EXEC sp_xml_preparedocument @idoc OUTPUT, @xmlVal  
   SELECT   *  
   FROM   OPENXML (@idoc, '//author')  
          WITH (FirstName  varchar(50) 'first-name',  
                LastName   varchar(50) 'last-name') R  
   WHERE  R.FirstName != 'David'  
  
   EXEC sp_xml_removedocument @idoc  
   FETCH NEXT FROM name_cursor INTO @xmlVal  
END  
CLOSE name_cursor  
DEALLOCATE name_cursor   
```  
  
 Метод **OpenXml()** создает представление данных в памяти и использует вместо обработчика запросов рабочие таблицы. В основе его работы лежит процессор XPath 1.0 кода MSXML 3.0, а не ядро XQuery. Рабочие таблицы не обобщаются между несколькими вызовами метода **OpenXml()**, даже если он выполняется для одного экземпляра XML. Это ограничивает его масштабируемость. Метод **OpenXml()** позволяет обращаться к формату краевой таблицы XML-данных без предложения WITH. Кроме того, он позволяет использовать оставшееся XML-значение в отдельном столбце «переполнения».  
  
 При объединении функций **nodes()** и **value()** эффективно используются XML-индексы. Таким образом, эта комбинация может оказаться более масштабируемой, чем метод **OpenXml**.  
  
## См. также:  
 [OPENXML (SQL Server)](../../relational-databases/xml/openxml-sql-server.md)  
  
  