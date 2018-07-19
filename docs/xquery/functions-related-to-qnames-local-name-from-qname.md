---
title: local-name-from-QName (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:local-name-from-QName function
- local-name-from-QName function
ms.assetid: fafed718-8c3c-403f-93ee-ec51fc157a6e
caps.latest.revision: 16
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 691e26b9e58bbb83706fb987a06280321dc37656
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38061362"
---
# <a name="functions-related-to-qnames---local-name-from-qname"></a>Функции, связанные с QName — local-name-from-QName
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает xs: NCName, представляющее локальную часть QName, заданную *$arg*. Результат представляет собой пустую последовательность, если *$arg* является пустая последовательность.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
fn:local-name-from-QName($arg as xs:QName?) as xs:NCName?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 QName, из которого должно извлекаться локальное имя.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** -столбцов в [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] базы данных.  
  
 В следующем примере используется **local-name-from-QName()** функции для получения локального имени и URI пространства имен частей из значения типа QName. В примере выполняются следующие действия.  
  
-   Создается коллекция XML-схемы.  
  
-   Создается таблица со столбцом типа xml. Значение для типа xml типизируется с помощью коллекции XML-схемы.  
  
-   Пример образца XML сохраняется в таблице. С помощью **query()** выполнения метода типа данных xml, выражение запроса для извлечения из экземпляра в части локального имени значения типа QName.  
  
```  
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
insert into T values ('<root xmlns="QNameXSD" xmlns:a="http://someURI">a:someLocalName</root>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare default element namespace "QNameXSD"; local-name-from-QName(/root[1])')  
FROM T  
-- Result = someLocalName  
-- You can retrive namespace URI part from the QName using the namespace-uri-from-QName() function  
SELECT xmlCol.query('declare default element namespace "QNameXSD"; namespace-uri-from-QName(/root[1])')  
FROM T  
-- Result = http://someURI  
```  
  
## <a name="see-also"></a>См. также  
 [Функции, связанные с QName &#40;XQuery&#41;](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
