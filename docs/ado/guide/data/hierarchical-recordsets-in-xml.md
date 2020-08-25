---
description: Иерархические наборы записей в XML
title: Иерархические наборы записей в XML | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO], in XML
ms.assetid: 5d4b11c4-c94f-4910-b99b-5b9abc50d791
author: rothja
ms.author: jroth
ms.openlocfilehash: 3e6180c8aa422c5833234afba7881a1a4c8b9049
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806015"
---
# <a name="hierarchical-recordsets-in-xml"></a>Иерархические наборы записей в XML
ADO обеспечивает сохранение иерархических объектов Recordset в XML. При использовании иерархических объектов Recordset значение поля в родительском наборе записей является еще одним набором записей. Такие поля представлены как дочерние элементы в XML-потоке, а не в атрибуте.  
  
## <a name="remarks"></a>Remarks  
 Этот случай демонстрируется в следующем примере:  
  
```  
Rs.Open "SHAPE {select stor_id, stor_name, state from stores} APPEND ({select stor_id, ord_num, ord_date, qty from sales} AS rsSales RELATE stor_id TO stor_id)", "Provider=MSDataShape;DSN=pubs;Integrated Security=SSPI;"  
```  
  
 Ниже приведен XML-формат сохраненного набора записей.  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"     xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882"     xmlns:rs="urn:schemas-microsoft-com:rowset"   
    xmlns:z="#RowsetSchema">   
  <s:Schema id="RowsetSchema">   
    <s:ElementType name="row" content="eltOnly" rs:updatable="true">   
      <s:AttributeType name="stor_id" rs:number="1"   
        rs:writeunknown="true">   
        <s:datatype dt:type="string" dt:maxLength="4"   
          rs:fixedlength="true" rs:maybenull="false"/>   
      </s:AttributeType>   
      <s:AttributeType name="stor_name" rs:number="2" rs:nullable="true"   
        rs:writeunknown="true">   
          <s:datatype dt:type="string" dt:maxLength="40"/>   
      </s:AttributeType>   
      <s:AttributeType name="state" rs:number="3" rs:nullable="true"   
        rs:writeunknown="true">   
        <s:datatype dt:type="string" dt:maxLength="2"   
          rs:fixedlength="true"/>   
      </s:AttributeType>   
      <s:ElementType name="rsSales" content="eltOnly"   
        rs:updatable="true" rs:relation="010000000100000000000000">   
        <s:AttributeType name="stor_id" rs:number="1"   
          rs:writeunknown="true">   
          <s:datatype dt:type="string" dt:maxLength="4"   
            rs:fixedlength="true" rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:AttributeType name="ord_num" rs:number="2"   
          rs:writeunknown="true">   
          <s:datatype dt:type="string" dt:maxLength="20"   
            rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:AttributeType name="ord_date" rs:number="3"   
          rs:writeunknown="true">   
            <s:datatype dt:type="dateTime" dt:maxLength="16"   
              rs:scale="3" rs:precision="23" rs:fixedlength="true"   
              rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:AttributeType name="qty" rs:number="4" rs:writeunknown="true">   
          <s:datatype dt:type="i2" dt:maxLength="2" rs:precision="5"   
            rs:fixedlength="true" rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:extends type="rs:rowbase"/>   
      </s:ElementType>   
      <s:extends type="rs:rowbase"/>   
    </s:ElementType>   
  </s:Schema>   
  <rs:data>   
    <z:row stor_id="6380" stor_name="Eric the Read Books" state="WA">   
      <rsSales stor_id="6380" ord_num="6871"   
        ord_date="1994-09-14T00:00:00" qty="5"/>   
      <rsSales stor_id="6380" ord_num="722a"   
        ord_date="1994-09-13T00:00:00" qty="3"/>   
    </z:row>   
    <z:row stor_id="7066" stor_name="Barnum's" state="CA">   
      <rsSales stor_id="7066" ord_num="A2976"   
        ord_date="1993-05-24T00:00:00" qty="50"/>   
      <rsSales stor_id="7066" ord_num="QA7442.3"   
        ord_date="1994-09-13T00:00:00" qty="75"/>   
    </z:row>   
    <z:row stor_id="7067" stor_name="News & Brews" state="CA">   
      <rsSales stor_id="7067" ord_num="D4482"   
        ord_date="1994-09-14T00:00:00" qty="10"/>   
      <rsSales stor_id="7067" ord_num="P2121"   
        ord_date="1992-06-15T00:00:00" qty="40"/>   
      <rsSales stor_id="7067" ord_num="P2121"   
        ord_date="1992-06-15T00:00:00" qty="20"/>   
      <rsSales stor_id="7067" ord_num="P2121"   
        ord_date="1992-06-15T00:00:00" qty="20"/>   
    </z:row>   
  </rs:data>   
</xml>   
```  
  
 Точный порядок столбцов в родительском наборе записей не очевидно, если он сохраняется таким образом. Любое поле в родительском объекте может содержать дочерний набор записей. Поставщик сохраняемости сохраняет все скалярные столбцы в качестве атрибутов, а затем сохраняет все "столбцы" дочерних наборов записей в качестве дочерних элементов родительской строки. Порядковый номер поля в родительском наборе записей можно получить, просмотрев определение схемы набора записей. Каждое поле имеет свойство OLE DB, RS: Number, определенное в пространстве имен схемы набора записей, которое содержит порядковый номер для этого поля.  
  
 Имена всех полей в дочернем наборе записей объединяются с именем поля в родительском наборе записей, содержащем этот дочерний элемент. Это гарантирует отсутствие конфликтов имен в случаях, когда родительские и дочерние наборы записей содержат поле, полученное из двух разных таблиц, но названы в единственном числе.  
  
 При сохранении иерархических наборов записей в XML следует учитывать следующие ограничения ADO.  
  
-   Иерархический набор записей с ожидающими обновлениями не может быть сохранен в XML.  
  
-   Иерархический набор записей, созданный с помощью параметризованной команды Shape, не может быть сохранен (в формате XML или АДТГ).  
  
-   В настоящее время ADO сохраняет связь между родительским и дочерними наборами записей в виде большого двоичного объекта (BLOB). XML-теги для описания этой связи еще не определены в пространстве имен схемы набора строк.  
  
-   При сохранении иерархического набора записей все дочерние наборы записей сохраняются вместе с ним. Если текущий набор записей является дочерним для другого набора записей, его родительский объект не сохраняется. Сохраняются все дочерние наборы записей, которые формируют поддерево текущего набора записей.  
  
 При повторном открытии иерархического набора записей из XML-сохраненного формата необходимо учитывать следующие ограничения.  
  
-   Если дочерняя запись содержит записи, для которых нет соответствующих родительских записей, эти строки не записываются в XML-представлении иерархического набора записей. Поэтому эти строки будут потеряны при повторном открытии набора записей из сохраненного расположения.  
  
-   Если дочерняя запись ссылается на более чем одну родительскую запись, то при повторном открытии набора записей дочерний набор записей может содержать дублирующиеся записи. Однако эти дубликаты будут видны, только если пользователь работает непосредственно с базовым дочерним набором строк. Если глава используется для навигации по дочернему набору записей (это единственный способ навигации по ADO), дубликаты не отображаются.  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](./persisting-records-in-xml-format.md)