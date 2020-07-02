---
title: expanded-QName (XQuery) | Документация Майкрософт
description: Узнайте, как использовать расширенную функцию-QName (), чтобы получить URI пространства имен и часть локального имени QName.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- expanded-QName function
- fn:expanded-QName function
ms.assetid: b8377042-95cc-467b-9ada-fe43cebf4bc3
author: rothja
ms.author: jroth
ms.openlocfilehash: 88bbf5697112fd80f8ffea629a1ad2b9e99977fa
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85720042"
---
# <a name="functions-related-to-qnames---expanded-qname"></a>Функции, связанные с QName — expanded-QName
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  Возвращает значение типа xs: QName с URI пространства имен, указанным в *$paramURI* , и локальным именем, указанным в *$paramLocal*. Если *$paramURI* является пустой строкой или пустой последовательностью, она не представляет пространство имен.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
fn:expanded-QName($paramURI as xs:string?, $paramLocal as xs:string?) as xs:QName?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$paramURI*  
 URI-код пространства имен для QName.  
  
 *$paramLocal*  
 Часть локального имени QName.  
  
## <a name="remarks"></a>Примечания  
 Следующее относится к **расширенной функции-QName ()** :  
  
-   Если указанное значение *$paramLocal* не находится в правильной лексической форме для типа xs: NCName, возвращается пустая последовательность, представляющая динамическую ошибку.  
  
-   Преобразование данных типа xs:QName type к любому другому типу не поддерживается в приложении [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. По этой причине **Расширенная функция-QName ()** не может использоваться в конструкции XML. Например при создании узла, такого как `<e> expanded-QName(...) </e>`, значение должно быть нетипизированным. Это потребовало бы преобразования значения типа xs:QName, возвращаемого функцией `expanded-QName()` к типу xdt:untypedAtomic. Однако это не поддерживается. Решение приведено далее в примере в этом же подразделе.  
  
-   Можно модифицировать или сравнить существующие значения типа QName. Например, `/root[1]/e[1] eq expanded-QName("http://nsURI" "myNS")` сравнивает значение элемента <`e`> с QName, возвращаемым **расширенной функцией-QName ()** .  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] базе данных.  
  
### <a name="a-replacing-a-qname-type-node-value"></a>A. Замещение значения узла типа QName  
 Данный пример иллюстрирует изменение значения узла элемента типа QName. В примере выполняются следующие действия.  
  
-   Создается коллекция XML-схем, которая определяет элемент типа QName.  
  
-   Создает таблицу со столбцом типа **XML** с помощью коллекции XML-схем.  
  
-   Экземпляр XML сохраняется в таблице.  
  
-   Использует метод **Modify ()** типа данных XML для изменения значения элемента типа QName в экземпляре. **Расширенная функция-QName ()** используется для создания нового значения типа QName.  
  
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
<Root xmlns="QNameXSD" xmlns:ns="https://myURI">  
      <ElemQN>ns:someName</ElemQN>  
</Root>')  
go  
-- Verify the insertion  
SELECT * from T  
go  
-- Result  
<Root xmlns="QNameXSD" xmlns:ns="https://myURI">  
  <ElemQN>ns:someName</ElemQN>  
</Root>   
```  
  
 В следующем запросе `ElemQN` значение элемента <> заменяется методом **Modify ()** типа данных XML и ЗАМЕЩЕНИЯ значения XML DML, как показано ниже.  
  
```  
-- the value.  
UPDATE T   
SET XmlCol.modify('  
  declare default element namespace "QNameXSD";   
  replace value of /Root[1]/ElemQN   
  with expanded-QName("https://myURI", "myLocalName") ')  
go  
-- Verify the result  
SELECT * from T  
go  
```  
  
 Результат. Обратите внимание, что элемент <`ElemQN`> типа QName теперь имеет новое значение:  
  
```  
<Root xmlns="QNameXSD" xmlns:ns="urn">  
  <ElemQN xmlns:p1="https://myURI">p1:myLocalName</ElemQN>  
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
 **Развернутая функция-QName** не может использоваться в конструкции XML. Это показано в следующем примере. Чтобы обойти это ограничение пример сначала вставляет узел, затем изменяет его.  
  
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
insert into T values ('<root xmlns:a="https://someURI">a:b</root>')  
 go  
-- Verify  
SELECT *   
FROM T  
```  
  
 Следующая попытка добавляет другой `root` элемент <>, но завершается ошибкой, поскольку Расширенная функция-QName () не поддерживается в конструкции XML.  
  
```  
update T SET xmlCol.modify('  
insert <root>{expanded-QName("http://ns","someLocalName")}</root> as last into / ')  
go  
```  
  
 Решением этой проблемы является сначала Вставка экземпляра со значением <`root`> элемента, а затем его изменение. В этом примере начальное значение nil используется при `root` вставке элемента> <. Коллекция XML-схем в этом примере допускает значение nil для элемента <`root`>.  
  
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
  
 `<root xmlns:a="https://someURI">a:b</root>`  
  
 `<root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:p1="http://ns">p1:someLocalName</root>`  
  
 Можно сравнить значение QName, как показано в следующем запросе. Запрос возвращает только <`root`> элементы, значения которых соответствуют значению типа QName, возвращаемому **расширенной функцией-QName ()** .  
  
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
 Существует одно ограничение: функция **расширенного параметра-QName ()** принимает в качестве второго аргумента пустую последовательность и возвращает пустое значение вместо возникновения ошибки времени выполнения, если второй аргумент неверен.  
  
## <a name="see-also"></a>См. также  
 [Функции, связанные с QName &#40;XQuery&#41;](https://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
