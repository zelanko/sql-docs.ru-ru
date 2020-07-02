---
title: Функция true (XQuery) | Документация Майкрософт
description: Сведения о функции XQuery true (), возвращающей логическое значение true.
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
ms.openlocfilehash: 614128995edaefae4fb5f6746d092a6d3f74c1ba
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85726764"
---
# <a name="boolean-constructor-functions---true-xquery"></a>Функции логического конструктора — true (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/applies-to-version/sqlserver.md)]

  Возвращает значение True типа xs:boolean. Это равносильно `xs:boolean("1")`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
fn:true() as xs:boolean  
```  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в базе данных AdventureWorks.  
  
### <a name="a-using-the-true-xquery-boolean-function"></a>A. Применение логической функции XQuery true()  
 В следующем примере запрашиваются нетипизированная **XML-** переменная. Выражение в методе **value ()** возвращает логическое **значение true ()** , если "AAA" является значением атрибута. Метод **value ()** типа данных **XML** преобразует логическое значение в бит и возвращает его.  
  
```  
DECLARE @x XML  
SET @x= '<ROOT><elem attr="aaa">bbb</elem></ROOT>'  
select @x.value(' if ( (/ROOT/elem/@attr)[1] eq "aaa" ) then fn:true() else fn:false() ', 'bit')  
go  
-- result = 1  
```  
  
 В следующем примере запрос задается для типизированного **XML-** столбца. `if`Выражение проверяет типизированное логическое значение `ROOT` элемента <> и возвращает сформированный XML соответствующим образом. В примере выполняются следующие действия.  
  
-   Создает коллекцию XML-схем, определяющую `ROOT` элемент <> типа xs: Boolean.  
  
-   Создает таблицу с типизированным **XML** -столбцом с помощью коллекции XML-схем.  
  
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
 [Логические функции конструктора &#40;XQuery&#41;](https://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)  
  
  
