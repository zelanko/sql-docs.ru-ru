---
title: "Использование предложения WITH XMLNAMESPACES (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WITH_XMLNAMESPACES_TSQL
- WITH XMLNAMESPACES
dev_langs: TSQL
helpviewer_keywords:
- adding XML namespaces
- XML namespace declarations [SQL Server]
- clauses [SQL Server], WITH XMLNAMESPACES
- WITH XMLNAMESPACES clause
- declaring XML namespaces
ms.assetid: 3b32662b-566f-454d-b7ca-e247002a9a0b
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: db002fd372fd69972b4f150c14c95342686f85f3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="with-xmlnamespaces"></a>WITH XMLNAMESPACES
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Данное предложение объявляет одно или несколько пространств имен XML.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WITH XMLNAMESPACES ( <XML namespace declaration item>  
[ { , <XML namespace declaration item> }...] )   
  
<XML namespace declaration item> ::=  
<xml_namespace_uri> AS <xml_namespace_prefix>  
| <XML default namespace declaration item>  
<xml_namespace_uri> ::= <character string literal>  
```  
  
```  
  
<xml_namespace_prefix> ::= <identifier>  
```  
  
```  
  
<XML default namespace declaration item> ::=  
DEFAULT <xml_namespace_uri>  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *xml_namespace_uri*  
 Универсальный идентификатор ресурса (Uniform Resource Identifier, URI), определяющий объявляемое пространство имен XML. *xml_namespace_uri* является строкой SQL.  
  
 *xml_namespace_prefix*  
 Задает префикс, сопоставляемый и связываемый со значением URI пространства имен, указанным в *xml_namespace_uri*. *xml_namespace_prefix* должно быть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентификатор.  
  
## <a name="remarks"></a>Замечания  
 При использовании предложения WITH XMLNAMESPACES в инструкции, включающей также обобщенное табличное выражение, предложение WITH XMLNAMESPACES должно предшествовать этому выражению.  
  
 Ниже приведены общие синтаксические правила, которые следует соблюдать при использовании предложения WITH XMLNAMESPACES.  
  
-   Каждое объявление пространства имен XML должно включать хотя бы один элемент по умолчанию.  
  
-   Каждый префикс пространства имен XML должен быть именем без двоеточий (NCName), в котором двоеточие (:) не является частью имени.  
  
-   Определить префикс пространства имен два раза нельзя.  
  
-   Префиксы пространств имен XML и идентификаторы URI обрабатываются с учетом регистра.  
  
-   Префикс `xmlns` пространства имен XML не может быть объявлен.  
  
-   Префикс `xml` не может быть переопределен пространством имен, отличным от пространства имен с URI `'http://www.w3.org/XML/1998/namespace'`, и этому URI не может быть назначен другой префикс.  
  
-   Префикс `xsi` пространства имен XML не может быть повторно объявлен, если в запросе используется директива ELEMENTS XSINIL.  
  
-   Строковые значения URI кодируются в соответствии с кодовой страницей параметров сортировки текущей базы данных и преобразуются внутри SQL Server в Юникод.  
  
-   Пространство имен XML, URI будет пробела соответствии пробелы XSD свернуть правила, используемые для **xs: anyURI**. Имейте в виду, что преобразование символов значений URI пространств имен XML в аналогичные последовательности символов и обратно не выполняется.  
  
-   При обработке URI пространства имен XML проверяется наличие недопустимых символов для XML 1.0; при обнаружении такого символа (например, U+0007) формируется ошибка.  
  
-   После удаления всех неотображаемых символов идентификатор URI пространства имен XML не может оказаться строкой нулевой длины; в противном случае произойдет ошибка «invalid empty namespace URI» (недопустимый пустой URI-идентификатор пространства имен).  
  
-   В контексте предложения WITH ключевое слово XMLNAMESPACES является зарезервированным.  
  
## <a name="examples"></a>Примеры  
 Примеры см. в разделе [добавление пространств имен в запросы с WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку XQuery (SQL Server)](../../xquery/xquery-language-reference-sql-server.md)  
  
  
