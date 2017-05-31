---
title: "Получение и запрос данных XML | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML data [SQL Server], retrieving
- XML instance retrieval
ms.assetid: 24a28760-1225-42b3-9c89-c9c0332d9c51
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: cff6370e1e57b4f1163100f029bd56d7bf63e552
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="retrieve-and-query-xml-data"></a>Получение и запрос XML-данных
  В этом разделе описываются параметры запроса, которые необходимо указать для запроса XML-данных. Кроме того, в нем описаны компоненты экземпляров XML, нефиксируемых при сохранении экземпляров в базах данных.  
  
##  <a name="features"></a> Компоненты экземпляра XML, которые не сохраняются  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняется содержимое экземпляра XML, но не сохраняются его аспекты, которые в модели XML-данных не рассматриваются как значительные. Это означает, что полученный экземпляр XML может отличаться от экземпляра, сохраненного на сервере, но при этом будет содержать те же самые данные.  
  
### <a name="xml-declaration"></a>XML-декларация  
 XML-декларация экземпляра не сохраняется при сохранении экземпляра в базе данных. Например:  
  
```  
CREATE TABLE T1 (Col1 int primary key, Col2 xml)  
GO  
INSERT INTO T1 values (1, '<?xml version="1.0" encoding="windows-1252" ?><doc></doc>')  
GO  
SELECT Col2  
FROM T1  
```  
  
 Результат `<doc/>`.  
  
 XML-декларация, например `<?xml version='1.0'?>`, не сохраняется при сохранении XML-данных в экземпляре типа **xml** . Это сделано намеренно. XML-декларация () и ее атрибуты (version/encoding/stand-alone) будут утеряны после того, как данные преобразуются в тип **xml**. XML-декларация обрабатывается как директива для синтаксического анализатора XML. Все данные XML внутренне хранятся в кодировке UCS-2. Все другие инструкции по обработке (PI) в экземпляре XML сохраняются.  
  
  
### <a name="order-of-attributes"></a>Порядок атрибутов  
 Порядок атрибутов экземпляра XML не сохраняется. При запросе экземпляра XML, хранящегося в столбце типа **xml** , порядок атрибутов в результирующем XML может отличаться от порядка в исходном экземпляре XML.  
  
  
### <a name="quotation-marks-around-attribute-values"></a>Кавычки вокруг значений атрибутов  
 Одинарные и двойные кавычки вокруг значений атрибутов не сохраняются. Значения атрибутов хранятся в базе данных в виде пар имени и значения. Кавычки не хранятся. При выполнении запроса XQuery к экземпляру XML результирующий XML сериализуется с использованием двойных кавычек вокруг значений атрибутов.  
  
```  
DECLARE @x xml  
-- Use double quotation marks.  
SET @x = '<root a="1" />'  
SELECT @x  
GO  
DECLARE @x xml  
-- Use single quotation marks.  
SET @x = '<root a=''1'' />'  
SELECT @x  
GO  
```  
  
 Оба запроса вернут `<root a="1" />`.  
  
  
### <a name="namespace-prefixes"></a>Префиксы пространства имен  
 Префиксы пространств имен не сохраняются. При выполнении запроса XQuery к столбцу типа **xml** для сериализации результирующего XML могут использоваться другие префиксы пространства имен.  
  
```  
DECLARE @x xml  
SET @x = '<ns1:root xmlns:ns1="abc" xmlns:ns2="abc">  
            <ns2:SomeElement/>  
          </ns1:root>'  
SELECT @x  
SELECT @x.query('/*')  
GO  
```  
  
 Префикс пространства имен в результате может быть другим. Например:  
  
```  
<p1:root xmlns:p1="abc"><p1:SomeElement/></p1:root>  
```  
  
  
##  <a name="query"></a> Задание обязательных параметров запроса  
 При запросе столбцов или переменных с типом данных **xml** с помощью методов типа данных **xml** приведенные ниже параметры должны быть установлены следующим образом.  
  
|Параметры SET|Необходимые значения|  
|-----------------|---------------------|  
|ANSI_NULLS|ON|  
|ANSI_PADDING|ON|  
|ANSI_WARNINGS|ON|  
|ARITHABORT|ON|  
|CONCAT_NULL_YIELDS_NULL|ON|  
|NUMERIC_ROUNDABORT|OFF|  
|QUOTED_IDENTIFIER|ON|  
  
 Если эти параметры не установлены, как указано, запросы и методы изменения данных типа **xml** завершатся ошибкой.  
  
  
## <a name="see-also"></a>См. также:  
 [Создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md)  
  
  
