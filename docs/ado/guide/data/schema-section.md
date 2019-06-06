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
manager: jroth
ms.openlocfilehash: bb09e954640554c5375539b4104ab58ae71ddaab
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700405"
---
# <a name="schema-section"></a>Раздел схемы
Раздел схемы является обязательным. Как показано в предыдущем примере ADO записывает подробные метаданные о каждом столбце, чтобы сохранить семантику значений данных, насколько это возможно, для обновления. Тем не менее чтобы загрузить в XML, ADO требуется только имена столбцов и строк, к которому они принадлежат. Ниже приведен пример минимальную схему:  
  
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
  
 В предыдущем примере ADO будет рассматривать данные как строки переменной длины, так как сведения о типе не включается в схеме.  
  
## <a name="creating-aliases-for-column-names"></a>Создание псевдонимов для имен столбцов  
 Rs: имя атрибута можно создать псевдоним для имени столбца, чтобы сведения о столбцах, предоставленных набором строк, может быть указано понятное имя и в разделе данных можно использовать более короткое имя. Например можно изменить предыдущую схему для сопоставить ShipperID s1, CompanyName на уровень s2, а телефона для s3, как показано ниже:  
  
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
  
 Затем в разделе данных строки использовать атрибут name (rs: имя) для обращения к этому столбцу:  
  
```  
"<row s1="1" s2="Speedy Express" s3="(503) 555-9831"/>  
```  
  
 Создание псевдонимов для имен столбцов является обязательным, каждый раз, когда имя столбца не является допустимым атрибутом или имени тега в XML. Например, «LastName» должен включать псевдоним так, как пробелы, называются недопустимые атрибуты. Следующая строка не обрабатывается правильно средством синтаксического анализа XML, поэтому вам необходимо создать псевдоним для другое имя, которое не имеет внедренный пробел.  
  
```  
<row last name="Jones"/>  
```  
  
 Любое значение, используйте для атрибута name необходимо согласованно использовать в каждом месте, что столбец имеется ссылка в разделах схемы и данных XML-документа. В следующем примере показано согласованное использование s1:  
  
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
  
 Аналогичным образом, так как отсутствует псевдоним не определен для `CompanyName` в предыдущем примере, `CompanyName` должен последовательно использоваться всей документа.  
  
## <a name="data-types"></a>Типы данных  
 Тип данных можно применить к столбец с атрибутом DT: Type. Полное руководство по допустимых типов XML, см. в разделе типы данных из [спецификации W3C XML-данных](http://www.w3.org/TR/1998/NOTE-XML-data/). Тип данных можно указать двумя способами: указать атрибут dt: Type непосредственно на само определение столбца или использовать конструкцию s:datatype в виде вложенных элементов определения столбца. Например,  
  
```  
<s:AttributeType name="Phone" >  
  <s:datatype dt:type="string"/>  
</s:AttributeType>  
```  
  
 эквивалентно  
  
```  
<s:AttributeType name="Phone" dt:type="string"/>  
```  
  
 Если опустить атрибут dt: Type из определения строки, по умолчанию, тип столбца будет строка переменной длины.  
  
 Если у вас есть Дополнительные сведения о типе, чем просто имя типа (например, DT: MaxLength), он делает более удобном для чтения, для использования s:datatype дочернего элемента. Это просто соглашение о вызовах, тем не менее и не является обязательным.  
  
 В следующих примерах дальнейшей как включать сведения о типе в схеме.  
  
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
  
 Есть малозаметные использования атрибута rs: fixedlength во втором примере. Столбец с атрибутом rs: fixedlength присвоено значение true означает, что данные должны иметь длину, определенных в схеме. В этом случае является допустимым значением для title_id является «123456», так как «123». Тем не менее «123» не будет допустимым, поскольку его длина равна 3, не 6. См. в руководстве программиста OLE DB более полное описание свойств fixedlength.  
  
## <a name="handling-nulls"></a>Обработка значений NULL  
 Значения NULL обрабатываются с помощью атрибута rs: maybenull. Если этот атрибут имеет значение true, содержимое столбца может содержать значение null. Кроме того Если столбец не найден в строке данных, чтение данных из набора строк пользователь получит состоянии null из IRowset::GetData(). Рассмотрим следующие определения столбцов из таблицы «Поставщики».  
  
```  
<s:AttributeType name="ShipperID">  
  <s:datatype dt:type="int" dt:maxLength="4"/>  
</s:AttributeType>  
<s:AttributeType name="CompanyName">  
  <s:datatype dt:type="string" dt:maxLength="40" rs:maybenull="true"/>  
</s:AttributeType>  
```  
  
 В определении разрешены `CompanyName` должен иметь значение null, но `ShipperID` не может содержать значение null. Если раздел данных содержит следующую строку, поставщик сохраняемости устанавливал состояние данных для `CompanyName` столбца константе состояние DBSTATUS_S_ISNULL OLE DB:  
  
```  
<z:row ShipperID="1"/>  
```  
  
 Если строка полностью пуст, как показано ниже, поставщик сохраняемости вернет состояние DBSTATUS_E_UNAVAILABLE для OLE DB `ShipperID` и DBSTATUS_S_ISNULL для CompanyName.  
  
```  
<z:row/>   
```  
  
 Обратите внимание на то, что строка нулевой длины не так же, как значение null.  
  
```  
<z:row ShipperID="1" CompanyName=""/>  
```  
  
 Для предыдущей строке поставщик сохраняемости будет возвращать статусом DBSTATUS_S_OK OLE DB для обоих столбцов. `CompanyName` В данном случае является просто «» (пустая строка).  
  
 Дополнительные сведения о OLE DB конструкции доступны для использования в схеме XML-документа для OLE DB, см. в разделе Определение «urn: schemas-microsoft-com:rowset» и руководство программиста OLE DB.  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
