---
title: Удаление XML-индексов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- dropping indexes
- XML indexes [SQL Server], dropping
ms.assetid: 7591ebea-34af-4925-8553-b2adb5b487c2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 82fd8836bb4fda85a7fdadd6345826cf432485cf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194154"
---
# <a name="drop-xml-indexes"></a>Удаление XML-индексов
  Инструкция [DROP INDEX (Transact-SQL)](/sql/t-sql/statements/drop-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] позволяет удалить существующие первичные и вторичные XML-индексы и индексы других типов. Однако к XML-индексам не применяется ни один из параметров DROP INDEX. Если удаляется первичный XML-индекс, то вместе с ним удаляются также и все имеющиеся вторичные индексы.  
  
 Синтаксис инструкции DROP для *TableName.IndexName* постепенно вытесняется и для XML-индексов не поддерживается.  
  
## <a name="example-creating-and-dropping-a-primary-xml-index"></a>Пример. Создание и удаление первичного XML-индекса  
 В следующем примере создается XML-индекса на `xml` столбец типа.  
  
```  
DROP TABLE T  
GO  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create Primary XML index   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Verify the index creation.   
-- Note index type is 3 for xml indexes.  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'   
-- Drop the index.  
DROP INDEX PIdx_T_XmlCol ON T  
```  
  
 При удалении таблицы автоматически удаляются все созданные для нее XML-индексы. Однако столбец XML не может быть удален из таблицы, если для него существует XML-индекс.  
  
 В следующем примере создается XML-индекса на `xml` столбец типа. Дополнительные сведения см. в статье [Сравнение типизированного и нетипизированного XML](../xml/compare-typed-xml-to-untyped-xml.md).  
  
```  
CREATE TABLE TestTable(  
 Col1 int primary key,   
 Col2 xml (Production.ProductDescriptionSchemaCollection))   
GO  
```  
  
 Теперь можно создать первичный XML-индекс для столбца `Co12`.  
  
```  
CREATE PRIMARY XML INDEX PIdx_TestTable_Col2   
ON TestTable(Col2)  
GO  
```  
  
## <a name="example-creating-an-xml-index-by-using-the-dropexisting-index-option"></a>Пример. Создание XML-индекса с помощью параметра DROP_EXISTING  
 В следующем примере XML-индекс создается для столбца`XmlColx`. Затем для другого столбца (`XmlColy`) создается другой XML-индекс с тем же именем. Так как задан параметр `DROP_EXISTING` , существующий XML-индекс для столбца (`XmlColx)` ) удаляется и вместо него создается новый XML-индекс для столбца (`XmlColy`).  
  
```  
DROP TABLE T  
GO  
CREATE TABLE T(Col1 int primary key, XmlColx xml, XmlColy xml)  
GO  
-- Create XML index on XmlColx.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlColx)  
GO  
-- Create same name XML index on XmlColy.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlColy)   
WITH (DROP_EXISTING = ON)  
-- Verify the index is created on XmlColy.d.  
SELECT sc.name   
FROM   sys.xml_indexes si inner join sys.index_columns sic   
ON     sic.object_id=si.object_id and sic.index_id=si.index_id  
INNER  join sys.columns sc on sc.object_id=sic.object_id   
AND    sc.column_id=sic.column_id  
WHERE  si.name='PIdx_T_XmlCol'   
AND    si.object_id=object_id('T')  
```  
  
 Запрос возвращает имя столбца, для которого создан XML-индекс.  
  
## <a name="see-also"></a>См. также  
 [XML-индексы (SQL Server)](xml-indexes-sql-server.md)  
  
  
