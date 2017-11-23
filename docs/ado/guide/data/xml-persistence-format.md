---
title: "Формат сохраняемости XML | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XML persistence [ADO], persistence format
ms.assetid: 6e146738-ac4d-47bb-b6cd-d87b2260aead
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4ef8f1495b6c790abe7b3b616e2d37908c42517b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="xml-persistence-format"></a>Формат хранения XML
ADO использует кодировку UTF-8 для XML-потока, он сохранится.  
  
 Формат ADO XML разбивается на два раздела, раздел схемы, следуют секции данных. Ниже приведен пример XML-файла для таблицы «Поставщики» из базы данных Northwind. Обсуждаются различные части XML следующий пример.  
  
## <a name="remarks"></a>Замечания  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"   
xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882"   
xmlns:rs="urn:schemas-microsoft-com:rowset"   
xmlns:z="#RowsetSchema">   
  <s:Schema id="RowsetSchema">   
    <s:ElementType name="row" content="eltOnly" rs:updatable="true">   
      <s:AttributeType name="ShipperID" rs:number="1"   
        rs:basetable="shippers" rs:basecolumn="ShipperID"  
        rs:keycolumn="true">   
        <s:datatype dt:type="int" dt:maxLength="4" rs:precision="10"   
          rs:fixedlength="true" rs:maybenull="false"/>   
      </s:AttributeType>   
      <s:AttributeType name="CompanyName" rs:number="2"   
        rs:nullable="true" rs:write="true" rs:basetable="shippers"   
        rs:basecolumn="CompanyName">   
        <s:datatype dt:type="string" dt:maxLength="40" />   
      </s:AttributeType>   
      <s:AttributeType name="Phone" rs:number="3" rs:nullable="true"   
        rs:write="true" rs:basetable="shippers"   
        rs:basecolumn="Phone">   
        <s:datatype dt:type="string" dt:maxLength="24"/>   
      </s:AttributeType>   
      <s:extends type="rs:rowbase"/>   
    </s:ElementType>   
  </s:Schema>   
  
  <rs:data>   
    <z:row ShipperID="1" CompanyName="Speedy Express"   
      Phone="(503) 555-9831"/>   
    <z:row ShipperID="2" CompanyName="United Package"   
      Phone="(503) 555-3199"/>   
    <z:row ShipperID="3" CompanyName="Federal Shipping"   
      Phone="(503) 555-9931"/>   
  </rs:data>   
</xml>  
```  
  
 В схеме показаны объявления пространств имен, раздел схемы и раздел данных. Раздел схемы содержит определения для строк, ShipperID, CompanyName и телефона.  
  
 Определения схемы соответствуют [спецификации W3C XML-Data](http://www.w3.org/TR/1998/NOTE-XML-data/) и могут быть проверены полностью (хотя и не будет выполняться проверка в Internet Explorer 5). XML-данных в настоящее время является форматом только поддерживаемые схемы для сохранения набора записей.  
  
 Раздел данных имеет три строки, содержащие сведения о них. Для пустой набор строк, раздел данных может быть пустым, но \<rs: данные > должен присутствовать тегов. Без данных можно написать сокращенное тег просто \<rs: данные / >. Любые теги, префикс «rs» указывает, что в пространстве имен, определяются urn: schemas-microsoft-com:rowset.  
  
## <a name="see-also"></a>См. также:  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
