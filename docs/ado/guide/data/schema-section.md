---
title: "Раздел схемы | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Schema section [ADO]
ms.assetid: 4ac6e524-2c92-48e8-b871-0a4b5c8fda18
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 65b56003d7fd7723dce57a0c8c6fae2ecee6da06
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="schema-section"></a>Раздел схемы
Раздел схемы является обязательным. Как показано в предыдущем примере, ADO записывает подробные метаданные о каждом столбце, чтобы сохранить семантику значений данных, насколько возможно, для обновления. Тем не менее для загрузки в XML, ADO требуется только имена столбцов и строк, к которому они принадлежат. Ниже приведен пример минимальной схемой:  
  
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
  
 В предыдущем примере ADO рассматривать данные как строки переменной длины, так как отсутствует информация о типе, включены в схему.  
  
## <a name="creating-aliases-for-column-names"></a>Создание псевдонимов для имен столбцов  
 Rs: имя атрибута можно создать псевдоним для имени столбца, чтобы понятное имя может появиться в сведения о столбцах, предоставленных набором строк, и более короткое имя, которые могут быть использованы в секции данных. Например предыдущей схемы может быть изменено для сопоставления ShipperID s1 CompanyName на s2, телефона для s3 следующим образом:  
  
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
  
 Затем в разделе данных строки использовать атрибут "name" (rs: имя) для ссылки на этот столбец:  
  
```  
"<row s1="1" s2="Speedy Express" s3="(503) 555-9831"/>  
```  
  
 Создание псевдонимов для имен столбцов является обязательным, каждый раз, когда имя столбца не является допустимым атрибутом или имени тега в XML. Например, «Фамилия» имеет псевдоним из-за недопустимых атрибутов имен, содержащее пробелы. Следующая строка будет не обрабатываться правильно средство синтаксического анализа XML, необходимо создать псевдоним с другим именем, который имеет внедренный пробел.  
  
```  
<row last name="Jones"/>  
```  
  
 Любое значение, используемое для атрибута имени должен постоянно использоваться в разных местах, что ссылки на столбец в разделах схему и данные XML-документа. В следующем примере показано использование согласованного s1:  
  
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
  
 Аналогичным образом, так как отсутствует псевдоним не определен для `CompanyName` в предыдущем примере `CompanyName` должен постоянно использоваться во всем документе.  
  
## <a name="data-types"></a>Типы данных  
 Тип данных можно применить к столбцу, атрибут dt: Type. Полное руководство по разрешенных типов XML, см в разделе типы данных [спецификации W3C XML-Data](http://www.w3.org/TR/1998/NOTE-XML-data/). Тип данных можно указать двумя способами: указать атрибут dt: Type непосредственно на само определение столбца или используйте конструкцию s:datatype как вложенный элемент определения столбца. Например,  
  
```  
<s:AttributeType name="Phone" >  
  <s:datatype dt:type="string"/>  
</s:AttributeType>  
```  
  
 эквивалентно  
  
```  
<s:AttributeType name="Phone" dt:type="string"/>  
```  
  
 Если опустить атрибут dt: Type из определения строки по умолчанию, тип столбца представляет собой строку переменной длины.  
  
 Если у вас есть Дополнительные сведения о типе, чем просто имя типа (например, DT: MaxLength), это позволяет более удобном для чтения, чтобы использовать s:datatype дочерний элемент. Это просто правилом, тем не менее и не является обязательным.  
  
 В следующих примерах дальнейшей как включать сведения о типе в схеме.  
  
```  
<!-- 1. String with no max length -->  
<s:AttributeType name="title_id"/>  
<!—or -->  
<s:AttributeType name="title_id" dt:type="string"/>  
  
<!—- 2. Fixed length string with max length of 6 -->  
<s:AttributeType name="title_id">  
    <s:datatype dt:type="string" dt:maxLength="6" rs:fixedlength="true" />  
</s:AttributeType>  
  
<!—- 3. Variable length string with max length of 6 -->  
<s:AttributeType name="title_id">  
    <s:datatype dt:type="string" dt:maxLength="6" />  
</s:AttributeType>  
  
<!—- 4. Integer -->  
<s:AttributeType name="title_id" dt:type="int"/>  
```  
  
 Есть небольшие использования атрибута rs: fixedlength во втором примере. Столбец с атрибутом rs: fixedlength присвоено значение true означает, что данные должны иметь длину, определенным в схеме. В этом случае является допустимым значением для title_id является «123456», как «123». Тем не менее «123» не будет действителен, так как его длина равна 3, не 6. См. Руководство программиста OLE DB для более полное описание свойств fixedlength.  
  
## <a name="handling-nulls"></a>Обработка значений NULL  
 Значения NULL обрабатываются с помощью атрибута rs: maybenull. Если этот атрибут имеет значение true, содержимое столбца может содержать значение null. Кроме того Если столбец не найден в строке данных, чтение данных из набора строк пользователь получит значение null, состояние из IRowset::GetData(). Рассмотрим следующие определения столбца из таблицы «Поставщики».  
  
```  
<s:AttributeType name="ShipperID">  
  <s:datatype dt:type="int" dt:maxLength="4"/>  
</s:AttributeType>  
<s:AttributeType name="CompanyName">  
  <s:datatype dt:type="string" dt:maxLength="40" rs:maybenull="true"/>  
</s:AttributeType>  
```  
  
 В определении разрешены `CompanyName` должен иметь значение null, но `ShipperID` не может содержать значение null. Если раздел данных содержит следующую строку, поставщик сохраняемости задать состояние данных для `CompanyName` столбца константе состояния DBSTATUS_S_ISNULL OLE DB:  
  
```  
<z:row ShipperID="1"/>  
```  
  
 Если строка полностью пуст, как показано ниже, поставщик сохраняемости вернет состояние DBSTATUS_E_UNAVAILABLE для OLE DB `ShipperID` и DBSTATUS_S_ISNULL для CompanyName.  
  
```  
<z:row/>   
```  
  
 Обратите внимание, что строку нулевой длины не является таким же, как значение null.  
  
```  
<z:row ShipperID="1" CompanyName=""/>  
```  
  
 Для предыдущей строке поставщик сохраняемости вернет OLE DB состояние DBSTATUS_S_OK для обоих столбцов. `CompanyName` В данном случае является просто «» (пустую строку).  
  
 Дополнительные сведения о OLE DB конструкции доступны для использования в схеме XML-документа для OLE DB, в разделе Определение «urn: schemas-microsoft-com:rowset» и руководство программиста OLE DB.  
  
## <a name="see-also"></a>См. также:  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
