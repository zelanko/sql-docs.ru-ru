---
title: "значение true, функция (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- fn:true function
- true function
ms.assetid: 318e370d-0444-4812-afe4-307df7ef9f3b
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f38cd50748b59b2a0cf32e5a7e9ab0a28f7e396b
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="boolean-constructor-functions---true-xquery"></a>Функции логического конструктора - true (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает значение True типа xs:boolean. Это равносильно `xs:boolean("1")`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
fn:true() as xs:boolean  
```  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
### <a name="a-using-the-true-xquery-boolean-function"></a>A. Применение логической функции XQuery true()  
 В следующем примере запрашивается Нетипизированная **xml** переменной. Выражение в **value()** возвращает логическое значение **true()** Если значение атрибута «aaa». **Value()** метод **xml** тип данных преобразует логическое значение в бит и возвращает его.  
  
```  
DECLARE @x XML  
SET @x= '<ROOT><elem attr="aaa">bbb</elem></ROOT>'  
select @x.value(' if ( (/ROOT/elem/@attr)[1] eq "aaa" ) then fn:true() else fn:false() ', 'bit')  
go  
-- result = 1  
```  
  
 В следующем примере задается запрос к типизированному **xml** столбца. Выражение `if` проверяет типизированное логическое значение элемента <`ROOT`> и, соответственно, возвращает созданный XML. В примере выполняются следующие действия.  
  
-   Создается коллекция XML-схем, которая задает элемент <`ROOT`> типа xs:boolean.  
  
-   Создается таблица с типизированным **xml** столбца с помощью коллекции XML-схем.  
  
-   XML-экземпляр сохраняется в столбце и запрашивается.  
  
```  
-- Drop table if exist  
--DROP TABLE T  
--go  
DROP XML SCHEMA COLLECTION SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="QNameXSD" >  
      <element name="ROOT" type="boolean" nillable="true"/>  
</schema>'  
go  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- following OK  
insert into T values ('<ROOT xmlns="QNameXSD">true</ROOT>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare namespace a="QNameXSD";   
   if (/a:ROOT[1] eq true()) then  
       <result>Found boolean true</result>  
   else  
       <result>Found boolean false</result>')  
  
FROM T  
-- result = <result>Found boolean true</result>  
-- Clean up  
DROP TABLE T  
go  
DROP XML SCHEMA COLLECTION SC  
go  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции логического конструктора &#40; XQuery &#41;](http://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)  
  
  
