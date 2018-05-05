---
title: Иерархические наборы записей в формате XML | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO], in XML
ms.assetid: 5d4b11c4-c94f-4910-b99b-5b9abc50d791
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64be59db3e65386eaaa267e954f63d0cf063e146
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="hierarchical-recordsets-in-xml"></a>Иерархические наборы записей в формате XML
ADO обеспечивает сохраняемость иерархических данных, представляющий объекты в XML. С объектами иерархических записей значение поля в родительском объекте набора записей — другой набор записей. Такие поля, представляются в виде дочерних элементов в XML-потока, а не атрибут.  
  
## <a name="remarks"></a>Замечания  
 В следующем примере демонстрируется в данном случае:  
  
```  
Rs.Open "SHAPE {select stor_id, stor_name, state from stores} APPEND ({select stor_id, ord_num, ord_date, qty from sales} AS rsSales RELATE stor_id TO stor_id)", "Provider=MSDataShape;DSN=pubs;Integrated Security=SSPI;"  
```  
  
 Ниже приведен формат XML, сохраненного набора записей.  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"     xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882"     xmlns:rs="urn:schemas-microsoft-com:rowset"   
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
  
 Точный порядок столбцов в родительский набор записей не является очевидным, сохранение таким образом. Любое поле в родительском объекте могут содержать дочерних записей. Поставщик сохраняемости сохраняет out все скалярные столбцы первое в виде атрибутов и сохраняет в исходящий всех дочерних записей «столбцы» в виде дочерних элементов родительской строки. Порядковый номер поля в родительском объекте набора записей можно получить, просмотрев определения схемы в наборе записей. Каждое поле имеет свойство OLE DB rs: число, определенные в пространстве имен схемы набора записей, который содержит порядковый номер для этого поля.  
  
 Имена всех полей в дочерних записей объединяются с именем поля в родительский набор записей, содержащий этот дочерний элемент. Это позволяет убедиться, что нет конфликтов имен в случаях, когда родительские и дочерние наборы записей оба содержать поле, которое получается из двух различных таблиц, но называется по отдельности.  
  
 При сохранении иерархические наборы записей в XML, необходимо учитывать следующие ограничения в ADO.  
  
-   Не удается сохранить иерархических записей с отложенные обновления в XML.  
  
-   Иерархические Recordset, который создан с помощью фигуры параметризованные команды не могут быть сохранены (в формате XML или ADTG).  
  
-   В настоящее время ADO сохраняет связь между родительскими и дочерними наборами записей как большого двоичного объекта (BLOB). XML-теги для описания этой связи еще не были определены в пространстве имен схемы набора строк.  
  
-   При сохранении иерархических записей всех дочерних наборов записей сохраняются вместе с ним. Если для текущего набора записей является дочерним для другого набора записей, его родителя не сохраняется. Все дочерние наборы записей, которые составляют поддерево текущего набора записей, сохраняются.  
  
 Если набор иерархических записей повторном открытии из формата XML сохраняются, следует иметь в виду следующие ограничения:  
  
-   Если дочерней записи содержит записи, для которых нет соответствующих записей родительского, эти строки не записываются в XML-представление иерархических набора записей. Таким образом эти строки будут потеряны при повторном открытии набора записей из сохраненного расположения.  
  
-   Если дочерней записи есть ссылки на более одной родительской записи, затем при повторном открытии набора записей, дочерних записей может содержать повторяющиеся записи. Однако эти повторяющиеся значения будет только видимым, если пользователь работает непосредственно с базовой дочерних строк. Если главу используется для перемещения дочернего набора записей (это единственный способ перемещения по ADO), они не отображаются.  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
