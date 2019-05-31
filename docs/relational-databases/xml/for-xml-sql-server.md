---
title: FOR XML (SQL Server) | Документация Майкрософт
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, about FOR XML clause
- PATH FOR XML mode, construction
- EXPLICIT FOR XML mode
- RAW FOR XML mode
- retrieving XML data
- XML [SQL Server], FOR XML clause
- AUTO FOR XML mode
- XML [SQL Server], construction
ms.assetid: 2b6b5c61-c5bd-49d2-8c0c-b7cf15857906
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||=azuresqldb-mi-current||>=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions
ms.openlocfilehash: f0cc7033845f55a6df33a58d7b100c8a59926821
ms.sourcegitcommit: 982a1dad0b58315cff7b54445f998499ef80e68d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66175095"
---
# <a name="for-xml-sql-server"></a>FOR XML (SQL Server)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Запрос SELECT возвращает результаты в виде набора строк. При необходимости можно получать результаты SQL-запроса в формате XML. Для этого в запросе необходимо указать предложение FOR XML. Предложение FOR XML может использоваться в запросах верхнего уровня и во вложенных запросах. Предложение FOR XML верхнего уровня можно использовать только в инструкции SELECT. Во вложенных запросах предложение FOR XML можно использовать в инструкциях INSERT, UPDATE и DELETE. FOR XML также можно использовать в инструкциях присваивания.

В предложении FOR XML можно указать один из следующих режимов:

- RAW
- AUTO
- EXPLICIT
- PATH

В режиме RAW создается одиночный элемент \<row> для каждой строки набора строк, возвращенного инструкцией SELECT. XML-иерархию можно создать с помощью написания вложенных запросов FOR XML.

В режиме AUTO вложенность XML создается эвристически, в зависимости от метода определения инструкции SELECT. Управление формой создаваемой XML структуры минимально. Для создания XML-иерархии, расширяющей возможности XML-структуры, созданной эвристически в режиме AUTO, можно написать вложенные запросы FOR XML.

Режим EXPLICIT предоставляет больше возможностей по управлению формой XML-структуры. В XML-структуре могут быть использованы смешанные атрибуты и элементы. Это требует особого формата для результирующего набора строк, создаваемого в результате выполнения запроса. Формат этого набора строк затем сопоставляется с формой XML-структуры. Преимущества режима EXPLICIT состоят в возможности использования смешанных атрибутов и элементов, в возможности создания упаковщиков и вложенных составных свойств, создания значений, разделенных пробелами (например, атрибут OrderID может содержать список значений идентификаторов порядка), и смешанного содержимого.

Однако написание запросов в режиме EXPLICIT может быть очень обременительным. Можно использовать некоторые новые возможности предложения FOR XML, например написание вложенных запросов FOR XML в режиме RAW/AUTO/PATH и директивы TYPE вместо использования режима EXPLICIT для создания иерархий. Вложенные запросы FOR XML могут создавать любую XML структуру, которую можно создать с помощью режима EXPLICIT. Дополнительные сведения см. в статьях [Использование вложенных запросов FOR XML](../../relational-databases/xml/use-nested-for-xml-queries.md) и [Директива TYPE в запросах FOR XML](../../relational-databases/xml/type-directive-in-for-xml-queries.md).

Режим PATH совместно с вложенным запросом FOR XML обеспечивает гибкость режима EXPLICIT более простым образом.

Эти режимы на самом деле работают только при выполнении запросов, для которых они установлены. Они не влияют на результаты любых последующих запросов.

Предложение FOR XML недопустимо для выборки с использованием предложений FOR BROWSE.

## <a name="example"></a>Пример

Следующая инструкция `SELECT` получает данные из таблиц `Sales.Customer` и `Sales.SalesOrderHeader` базы данных `AdventureWorks2012` . В этом запросе задается режим `AUTO` в предложении `FOR XML` :

```sql
USE AdventureWorks2012
GO
SELECT Cust.CustomerID,
       OrderHeader.CustomerID,
       OrderHeader.SalesOrderID,
       OrderHeader.Status
FROM Sales.Customer Cust 
INNER JOIN Sales.SalesOrderHeader OrderHeader
ON Cust.CustomerID = OrderHeader.CustomerID
FOR XML AUTO;
```

## <a name="the-for-xml-clause-and-server-names"></a>Предложение FOR XML и имена сервера

Если в инструкции SELECT, использующей предложение FOR XML, указано четырехкомпонентное имя, в возвращаемом документе имя сервера отсутствует, если запрос выполняется на локальном компьютере. Однако имя сервера возвращается как часть имени, если запрос выполняется на сетевом сервере.

В качестве примера рассмотрим запрос:

```sql
SELECT TOP 1 LastName
  FROM ServerName.AdventureWorks2012.Person.Person
  FOR XML AUTO;
```

&nbsp;

**Локальный сервер.** &nbsp; Если `ServerName` — локальный сервер, запрос возвращает следующий текст:

```xml
<AdventureWorks2012.Person.Person LastName="Achong" />  
```

&nbsp;

**Сетевой сервер.** &nbsp; Если `ServerName` — сетевой сервер, запрос возвращает следующий текст:

```xml
<ServerName.AdventureWorks2012.Person.Person LastName="Achong" />
```

&nbsp;

**Исключение неоднозначности.** &nbsp; Возможной неоднозначности можно избежать с помощью такого псевдонима:

```sql
SELECT TOP 1 LastName
  FROM ServerName.AdventureWorks2012.Person.Person x
  FOR XML AUTO;
```

Теперь запрос, для которого исключена неоднозначность, возвращает следующий текст:

```xml
<x LastName="Achong"/>
```

## <a name="see-also"></a>См. также:

[Базовый синтаксис предложения FOR XML](../../relational-databases/xml/basic-syntax-of-the-for-xml-clause.md)  
[Использование RAW Mode с FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
[Использование AUTO Mode с FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md)  
[Использование режима EXPLICIT с предложением FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
[Использование режима PATH совместно с FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
[OPENXML (SQL Server)](../../relational-databases/xml/openxml-sql-server.md)  
[Добавление пространств имен в запросы с WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)
