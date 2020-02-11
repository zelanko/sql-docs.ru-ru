---
title: Раздел схемы | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Schema section [ADO]
ms.assetid: 4ac6e524-2c92-48e8-b871-0a4b5c8fda18
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5b6e591ecc9f366f3914986b0ae11e0e301b782d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924294"
---
# <a name="schema-section"></a>Раздел схемы
Требуется раздел схемы. Как показано в предыдущем примере, ADO записывает подробные метаданные о каждом столбце, чтобы сохранить семантику значений данных, насколько это возможно для обновления. Однако для загрузки в XML ADO требуются только имена столбцов и набор строк, к которому они относятся. Ниже приведен пример минимальной схемы.  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"  
    xmlns:rs="urn:schemas-microsoft-com:rowset"  
    xmlns:z="#RowsetSchema">  
  <s:Schema id="RowsetSchema">  
    <s:ElementType name="row" content="eltOnly">  
      <s:AttributeType name="ShipperID"/>  
      <s:AttributeType name="CompanyName"/>  
      <s:AttributeType name="Phone"/>  
      <s:Extends type="rs:rowbase"/>  
    </s:ElementType>  
  </s:Schema>  
  <rs:data>  
...  
  </rs:data>  
</xml>  
```  
  
 В предыдущем примере ADO будет обрабатывать данные как строки переменной длины, поскольку в схему не включаются сведения о типе.  
  
## <a name="creating-aliases-for-column-names"></a>Создание псевдонимов для имен столбцов  
 Атрибут RS: Name позволяет создать псевдоним для имени столбца, чтобы понятное имя отображалось в сведениях о столбцах, предоставляемых набором строк, а в разделе данных можно использовать более короткое имя. Например, Предыдущая схема может быть изменена, чтобы сопоставлять Шипперид с S1, CompanyName и S2, а также по телефону для S3 следующим образом:  
  
```  
<s:Schema id="RowsetSchema">   
<s:ElementType name="row" content="eltOnly" rs:updatable="true">   
<s:AttributeType name="s1" rs:name="ShipperID" rs:number="1" ...>   
...  
</s:AttributeType>   
<s:AttributeType name="s2" rs:name="CompanyName" rs:number="2" ...>   
...  
</s:AttributeType>   
<s:AttributeType name="s3" rs:name="Phone" rs:number="3" ...>   
...  
</s:AttributeType>   
...  
</s:ElementType>   
</s:Schema>  
```  
  
 Затем в разделе данных в строке будет использоваться атрибут Name (не RS: Name), ссылающийся на этот столбец:  
  
```  
"<row s1="1" s2="Speedy Express" s3="(503) 555-9831"/>  
```  
  
 Создание псевдонимов для имен столбцов требуется, если имя столбца не является допустимым атрибутом или именем тега в XML. Например, "LastName" должен иметь псевдоним, так как имена с пробелами являются недопустимыми атрибутами. Следующая строка не будет правильно обработана синтаксическим анализатором XML, поэтому необходимо создать псевдоним для другого имени, не имеющего внедренного пробела.  
  
```  
<row last name="Jones"/>  
```  
  
 Любое значение, используемое для атрибута Name, должно постоянно использоваться в каждом месте, где ссылка на столбец содержится в разделах схемы и данных XML-документа. В следующем примере показано единообразное использование S1:  
  
```  
<s:Schema id="RowsetSchema">  
  <s:ElementType name="row" content="eltOnly">  
    <s:attribute type="s1"/>  
    <s:attribute type="CompanyName"/>  
    <s:attribute type="s3"/>  
    <s:extends type="rs:rowbase"/>  
  </s:ElementType>  
  <s:AttributeType name="s1" rs:name="ShipperID" rs:number="1"   
    rs:maydefer="true" rs:writeunknown="true">  
    <s:datatype dt:type="i4" dt:maxLength="4" rs:precision="10"   
      rs:fixedlength="true" rs:maybenull="true"/>  
  </s:AttributeType>  
</s:Schema>  
<rs:data>  
  <z:row s1="1" CompanyName="Speedy Express" s3="(503) 555-9831"/>  
</rs:data>  
```  
  
 Аналогично, поскольку `CompanyName` в предыдущем примере псевдоним не определен, `CompanyName` должен использоваться единообразно во всем документе.  
  
## <a name="data-types"></a>Типы данных  
 К столбцу можно применить тип данных с помощью атрибута dt: Type. Полное описание разрешенных типов XML см. в разделе Типы данных [спецификации W3C по XML-данным](http://www.w3.org/TR/1998/NOTE-XML-data/). Тип данных можно указать двумя способами: либо указать атрибут dt: Type непосредственно в самом определении столбца, либо использовать конструкцию с:дататипе в качестве вложенного элемента определения столбца. Например,  
  
```  
<s:AttributeType name="Phone" >  
  <s:datatype dt:type="string"/>  
</s:AttributeType>  
```  
  
 эквивалентно правилу  
  
```  
<s:AttributeType name="Phone" dt:type="string"/>  
```  
  
 Если опустить атрибут dt: Type целиком из определения строки, по умолчанию типом столбца будет строка переменной длины.  
  
 Если у вас больше сведений о типе, чем просто имя типа (например, DT: maxLength), оно упрощает чтение для использования дочернего элемента с:дататипе. Однако это просто соглашение, а не требование.  
  
 В следующих примерах показано, как включить сведения о типах в схему.  
  
```  
<!-- 1. String with no max length -->  
<s:AttributeType name="title_id"/>  
<!-or -->  
<s:AttributeType name="title_id" dt:type="string"/>  
  
<!-- 2. Fixed length string with max length of 6 -->  
<s:AttributeType name="title_id">  
    <s:datatype dt:type="string" dt:maxLength="6" rs:fixedlength="true" />  
</s:AttributeType>  
  
<!-- 3. Variable length string with max length of 6 -->  
<s:AttributeType name="title_id">  
    <s:datatype dt:type="string" dt:maxLength="6" />  
</s:AttributeType>  
  
<!-- 4. Integer -->  
<s:AttributeType name="title_id" dt:type="int"/>  
```  
  
 Во втором примере существует незаметное использование атрибута RS: fixedlength. Столбец с атрибутом RS: fixedlength, установленным в значение true, означает, что данные должны иметь длину, определенную в схеме. В этом случае допустимым значением для title_id является "123456", как "123". Однако "123" будет недопустимым, так как его длина равна 3, а не 6. Более подробное описание свойства fixedlength см. в OLE DBном руководством программиста.  
  
## <a name="handling-nulls"></a>Обработка значений NULL  
 Значения NULL обрабатываются атрибутом RS: майбенулл. Если этот атрибут имеет значение true, содержимое столбца может содержать значение null. Более того, если столбец не найден в строке данных, то пользователь, считывающий данные из набора строк, получает состояние NULL из метода IRowset:: GetData (). Рассмотрим следующие определения столбцов из таблицы грузоотправителей.  
  
```  
<s:AttributeType name="ShipperID">  
  <s:datatype dt:type="int" dt:maxLength="4"/>  
</s:AttributeType>  
<s:AttributeType name="CompanyName">  
  <s:datatype dt:type="string" dt:maxLength="40" rs:maybenull="true"/>  
</s:AttributeType>  
```  
  
 Определение допускает `CompanyName` значение null, но `ShipperID` не может содержать значение null. Если в разделе данных содержится следующая строка, то поставщик сохраняемости настроил состояние данных `CompanyName` столбца на OLE DB константы состояния DBSTATUS_S_ISNULL:  
  
```  
<z:row ShipperID="1"/>  
```  
  
 Если строка была полностью пустой, то после этого поставщик сохраняемости возвратит OLE DB состояние DBSTATUS_E_UNAVAILABLE для `ShipperID` и DBSTATUS_S_ISNULL для CompanyName.  
  
```  
<z:row/>   
```  
  
 Обратите внимание, что строка нулевой длины не совпадает со значением NULL.  
  
```  
<z:row ShipperID="1" CompanyName=""/>  
```  
  
 Для предыдущей строки поставщик сохраняемости возвратит OLE DB состояние DBSTATUS_S_OK для обоих столбцов. `CompanyName` В данном случае это просто "" (строка нулевой длины).  
  
 Дополнительные сведения о конструкциях OLE DB, доступных для использования в схеме XML-документа для OLE DB, см. в описании определения "urn: schemas-microsoft-com: RowSet" и руководства программиста OLE DB.  
  
## <a name="see-also"></a>См. также:  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
