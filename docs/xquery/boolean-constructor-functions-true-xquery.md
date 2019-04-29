---
title: значение true, функция (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:true function
- true function
ms.assetid: 318e370d-0444-4812-afe4-307df7ef9f3b
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 611d23ad84df3087a259cbaf60870129b841715b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63047618"
---
# <a name="boolean-constructor-functions---true-xquery"></a>Функции логического конструктора — true (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает значение True типа xs:boolean. Это равносильно `xs:boolean("1")`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
fn:true() as xs:boolean  
```  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** -столбец базы данных AdventureWorks.  
  
### <a name="a-using-the-true-xquery-boolean-function"></a>A. Применение логической функции XQuery true()  
 В следующем примере запрашивается Нетипизированная **xml** переменной. Выражение в **value()** метод возвращает логическое значение **true()** Если «aaa» является значением атрибута. **Value()** метод **xml** тип данных преобразует логическое значение в бит и возвращает его.  
  
```  
DECLARE @x XML  
SET @x= '<ROOT><elem attr="aaa">bbb</elem></ROOT>'  
select @x.value(' if ( (/ROOT/elem/@attr)[1] eq "aaa" ) then fn:true() else fn:false() ', 'bit')  
go  
-- result = 1  
```  
  
 В следующем примере задается запрос к типизированному **xml** столбца. `if` Выражение проверяет типизированное логическое значение элемента <`ROOT`> элемент и возвращает созданный XML, соответствующим образом. В примере выполняются следующие действия.  
  
-   Создает коллекцию схем XML, который определяет <`ROOT`> элемент типа xs: Boolean.  
  
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
  
## <a name="see-also"></a>См. также  
 [Функции логического конструктора &#40;XQuery&#41;](https://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)  
  
  
