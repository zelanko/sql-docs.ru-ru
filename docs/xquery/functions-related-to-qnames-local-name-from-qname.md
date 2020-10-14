---
title: local-name-from-QName (XQuery) | Документация Майкрософт
description: Узнайте, как использовать функцию local-name-from-QName (), чтобы вернуть локальную часть имени QName.
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:local-name-from-QName function
- local-name-from-QName function
ms.assetid: fafed718-8c3c-403f-93ee-ec51fc157a6e
author: rothja
ms.author: jroth
ms.openlocfilehash: d19153bbfd3cf2483cf8dfa30358f752dd45290e
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036817"
---
# <a name="functions-related-to-qnames---local-name-from-qname"></a>Функции, связанные с QName — local-name-from-QName
[!INCLUDE[sqlserver](../includes/applies-to-version/sqlserver.md)]

  Возвращает значение типа xs: NCNAME, представляющее локальную часть QName, заданную *$arg*. Результатом является пустая последовательность, если *$arg* является пустой последовательностью.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
fn:local-name-from-QName($arg as xs:QName?) as xs:NCName?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 QName, из которого должно извлекаться локальное имя.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] базе данных.  
  
 В следующем примере используется функция **local-name-from-QName ()** для получения локальных имен и частей URI пространства имен из значения типа QName. В примере выполняются следующие действия.  
  
-   Создается коллекция XML-схемы.  
  
-   Создается таблица со столбцом типа xml. Значение для типа xml типизируется с помощью коллекции XML-схемы.  
  
-   Пример образца XML сохраняется в таблице. С помощью метода **query ()** типа данных XML выражение запроса выполняется для получения локальной части имени значения типа QName из экземпляра.  
  
```sql
DROP TABLE T  
go  
DROP XML SCHEMA COLLECTION SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="QNameXSD" >  
      <element name="root" type="QName" nillable="true"/>  
</schema>'  
go  
  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- following OK  
insert into T values ('<root xmlns="QNameXSD" xmlns:a="https://someURI">a:someLocalName</root>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare default element namespace "QNameXSD"; local-name-from-QName(/root[1])')  
FROM T  
-- Result = someLocalName  
-- You can retrieve namespace URI part from the QName using the namespace-uri-from-QName() function  
SELECT xmlCol.query('declare default element namespace "QNameXSD"; namespace-uri-from-QName(/root[1])')  
FROM T  
-- Result = https://someURI  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции, связанные с QName &#40;XQuery&#41;](./functions-related-to-qnames-expanded-qname.md)  
  
