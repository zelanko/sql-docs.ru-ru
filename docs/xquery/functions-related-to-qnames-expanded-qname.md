---
title: expanded-QName (XQuery) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.service: ''
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- expanded-QName function
- fn:expanded-QName function
ms.assetid: b8377042-95cc-467b-9ada-fe43cebf4bc3
caps.latest.revision: 19
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7d5f3bfcdcca66e5d4d6892dc1ec0e256d480ba5
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="functions-related-to-qnames---expanded-qname"></a>Функции, связанные с QNames - expanded-QName
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает значение типа xs: QName с пространством имен URI, заданный в *$paramURI* и локального имени, указанного в *$paramLocal*. Если *$paramURI* является пустой строкой или пустой последовательностью, он не представляет никакого пространства имен.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
fn:expanded-QName($paramURI as xs:string?, $paramLocal as xs:string?) as xs:QName?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$paramURI*  
 URI-код пространства имен для QName.  
  
 *$paramLocal*  
 Часть локального имени QName.  
  
## <a name="remarks"></a>Замечания  
 Приведенные ниже сведения относятся к **expanded-QName()** функции:  
  
-   Если *$paramLocal* указано недопустимое значение в правильной лексической формой для типа xs: NCName, возвращается пустая последовательность и отображается динамическая ошибка.  
  
-   Преобразование данных типа xs:QName type к любому другому типу не поддерживается в приложении [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. По этой причине **expanded-QName()** функцию нельзя использовать в конструкции XML. Например при создании узла, такого как `<e> expanded-QName(…) </e>`, значение должно быть нетипизированным. Это потребовало бы преобразования значения типа xs:QName, возвращаемого функцией `expanded-QName()` к типу xdt:untypedAtomic. Однако это не поддерживается. Решение приведено далее в примере в этом же подразделе.  
  
-   Можно модифицировать или сравнить существующие значения типа QName. Например `/root[1]/e[1] eq expanded-QName("http://nsURI" "myNS")` сравнивает значение элемента <`e`>, с QName, возвращаемым функцией **expanded-QName()** функции.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** -столбцов в [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] базы данных.  
  
### <a name="a-replacing-a-qname-type-node-value"></a>A. Замещение значения узла типа QName  
 Данный пример иллюстрирует изменение значения узла элемента типа QName. В примере выполняются следующие действия.  
  
-   Создается коллекция XML-схем, которая определяет элемент типа QName.  
  
-   Создает таблицу с **xml** столбец типа с помощью коллекции XML-схем.  
  
-   Экземпляр XML сохраняется в таблице.  
  
-   Использует **modify()** метода типа данных xml для изменения значения элемента типа QName в экземпляре. **Expanded-QName()** функция используется для создания нового значения типа QName.  
  
```  
-- If XML schema collection (if exists)  
-- drop xml schema collection SC  
-- go  
-- Create XML schema collection  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema"   
    targetNamespace="QNameXSD"   
      xmlns:xqo="QNameXSD" elementFormDefault="qualified">  
      <element name="Root" type="xqo:rootType" />  
      <complexType name="rootType">  
            <sequence minOccurs="1" maxOccurs="1">  
                        <element name="ElemQN" type="xs:QName" />  
            </sequence>  
      </complexType>  
</schema>'  
go  
-- Create table.  
CREATE TABLE T( XmlCol xml(SC) )  
-- Insert sample XML instnace  
INSERT INTO T VALUES ('  
<Root xmlns="QNameXSD" xmlns:ns="http://myURI">  
      <ElemQN>ns:someName</ElemQN>  
</Root>')  
go  
-- Verify the insertion  
SELECT * from T  
go  
-- Result  
<Root xmlns="QNameXSD" xmlns:ns="http://myURI">  
  <ElemQN>ns:someName</ElemQN>  
</Root>   
```  
  
 В следующем запросе <`ElemQN`> заменяется значение элемента, с помощью **modify()** метода типа данных xml и замещает значение XML DML, как показано.  
  
```  
-- the value.  
UPDATE T   
SET XmlCol.modify('  
  declare default element namespace "QNameXSD";   
  replace value of /Root[1]/ElemQN   
  with expanded-QName("http://myURI", "myLocalName") ')  
go  
-- Verify the result  
SELECT * from T  
go  
```  
  
 Результат. Теперь элемент <`ElemQN`> типа QName имеет другое значение:  
  
```  
<Root xmlns="QNameXSD" xmlns:ns="urn">  
  <ElemQN xmlns:p1="http://myURI">p1:myLocalName</ElemQN>  
</Root>  
```  
  
 Следующие инструкции удаляют объекты, используемые в примере.  
  
```  
-- Cleanup  
DROP TABLE T  
go  
drop xml schema collection SC  
go  
```  
  
### <a name="b-dealing-with-the-limitations-when-using-the-expanded-qname-function"></a>Б. Работа с ограничениями при использовании функции expanded-QName()  
 **Expanded-QName** функцию нельзя использовать в конструкции XML. Это показано в следующем примере. Чтобы обойти это ограничение пример сначала вставляет узел, затем изменяет его.  
  
```  
-- if exists drop the table T  
--drop table T  
-- go  
-- Create XML schema collection  
-- DROP XML SCHEMA COLLECTION SC  
-- go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
      <element name="root" type="QName" nillable="true"/>  
</schema>'  
go  
 -- Create table T with a typed xml column (using the XML schema collection)  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- Insert an XML instance.  
insert into T values ('<root xmlns:a="http://someURI">a:b</root>')  
 go  
-- Verify  
SELECT *   
FROM T  
```  
  
 В нижеследующем примере иллюстрируется попытка добавить другой элемент <`root`>, но попытка завершается неудачей, так как функция expanded-QName() не поддерживается в XML-конструкции.  
  
```  
update T SET xmlCol.modify('  
insert <root>{expanded-QName("http://ns","someLocalName")}</root> as last into / ')  
go  
```  
  
 Решением является вставка в экземпляр значения элемента <`root`> и его последующая модификация. В этом примере используется начальное значение нуль при добавлении элемента <`root`>. Коллекция XML-схем в этом примере разрешает значение нуль для элемента <`root`>.  
  
```  
update T SET xmlCol.modify('  
insert <root xsi:nil="true"/> as last into / ')  
go  
-- now replace the nil value with another QName.  
update T SET xmlCol.modify('  
replace value of /root[last()] with expanded-QName("http://ns","someLocalName") ')  
go  
 -- verify   
SELECT * FROM T  
go  
-- result  
<root>b</root>  
```  
  
 `<root xmlns:a="http://someURI">a:b</root>`  
  
 `<root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:p1="http://ns">p1:someLocalName</root>`  
  
 Можно сравнить значение QName, как показано в следующем запросе. Запрос возвращает только <`root`> другие элементы, значения которых соответствуют QName типа значения, возвращенного **expanded-QName()** функции.  
  
```  
SELECT xmlCol.query('  
    for $i in /root  
    return  
       if ($i eq expanded-QName("http://ns","someLocalName") ) then  
          $i  
       else  
          ()')  
FROM T  
```  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существует одно ограничение: **expanded-QName()** функция принимает пустую последовательность в качестве второго аргумента и возвращает пустой не вызывает ошибку времени выполнения, если второй аргумент недопустимый.  
  
## <a name="see-also"></a>См. также  
 [Функции, связанные с QNames &#40;XQuery&#41;](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
