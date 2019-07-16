---
title: Иерархические наборы записей в формате XML | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 17ed6f29442bc55f81d0ef83bfd19473a99e9a95
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925105"
---
# <a name="hierarchical-recordsets-in-xml"></a>Иерархические наборы записей в XML
ADO обеспечивает сохраняемость объектов иерархических наборов записей в XML. С помощью объектов иерархических наборов записей значение поля в родительском объекте набора записей — другой набор записей. Такие поля отображаются в виде дочерних элементов в потоке XML, а не атрибут.  
  
## <a name="remarks"></a>Примечания  
 В следующем примере демонстрируется этот случай:  
  
```  
Rs.Open "SHAPE {select stor_id, stor_name, state from stores} APPEND ({select stor_id, ord_num, ord_date, qty from sales} AS rsSales RELATE stor_id TO stor_id)", "Provider=MSDataShape;DSN=pubs;Integrated Security=SSPI;"  
```  
  
 Ниже приведен формат XML, сохраненного набора записей.  
  
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
  
 Точный порядок столбцов в родительском объекте набора записей не очевидным при хранении таким образом. Любое поле в родительском объекте может содержать дочерний элемент набора записей. Поставщик сохраняемости сохраняет все скалярные столбцы, во-первых, как атрибуты и сохраняет все дочерние набор записей «столбцы» как дочерние элементы элемента родительской строки. Порядковый номер поля в родительском объекте набора записей можно получить, просмотрев определение схемы в наборе записей. Каждое поле имеет свойство OLE DB, rs: число, определенные в пространстве имен схемы набора записей, который содержит порядковый номер для этого поля.  
  
 Имена всех полей в дочерних записей объединяются с именем поля в родительском наборе записей, который содержит этот дочерний элемент. Это гарантирует, что не возникало конфликтов имени в случаях, где родительских и дочерних записей в наборе обе содержать поле, которое получается из двух различных таблиц, но имеет имя в отдельности.  
  
 При сохранении иерархических наборов записей в XML, необходимо учитывать следующие ограничения в ADO:  
  
-   Иерархических наборах записей с отложенные обновления не могут быть сохранены в XML.  
  
-   Иерархических наборах записей, созданные с помощью команды параметризованные фигуры не могут быть сохранены (в формате XML или ADTG).  
  
-   ADO в настоящее время сохраняет связь между родительским и дочерним наборы записей в виде больших двоичных объектов (BLOB). XML-теги для описания этого отношения еще не определены в пространстве имен схемы набора строк.  
  
-   При сохранении иерархических наборах записей, все дочерние наборы записей, сохраняются вместе с ним. Если текущий набор записей является потомком другой набор записей, его родителя не сохраняется. Все дочерние наборы записей, которые составляют поддерево текущего набора записей, сохраняются.  
  
 Когда иерархических наборах записей повторном открытии из формата XML сохраняются, необходимо иметь в виду следующие ограничения:  
  
-   Если запись дочернего элемента содержит записи, для которых нет соответствующих записей родительского, эти строки не записываются в XML-представление иерархических наборах записей. Таким образом эти строки будут потеряны при повторном открытии набора записей из сохраненного расположения.  
  
-   Если запись дочернего элемента ссылки на более чем одной родительской записи, затем при повторном открытии набора записей, дочерних записей может содержать повторяющиеся записи. Тем не менее эти дубликаты будет только видимым, если пользователь работает непосредственно с базового набора дочерних строк. Глава используется для перемещения дочернего набора записей (это единственный способ перемещения по ADO), не отображаются дубликаты.  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
