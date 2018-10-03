---
title: Формат сохраняемости XML | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XML persistence [ADO], persistence format
ms.assetid: 6e146738-ac4d-47bb-b6cd-d87b2260aead
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e70b7ab799ee0c1704c2fcd492edb434eb7c536
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842172"
---
# <a name="xml-persistence-format"></a>Формат сохраняемости XML
ADO использует кодировку UTF-8 для потока XML, он будет повторяться.  
  
 Формат ADO XML разбивается на два раздела, раздел схемы, а затем в разделе данных. Ниже приведен пример XML-файла в таблице «Поставщики» из базы данных "Борей". Различные части XML рассматриваются в следующем примере.  
  
## <a name="remarks"></a>Примечания  
  
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
  
 В схеме показано объявления пространств имен, раздел схемы и раздел данных. Раздел схемы содержит определения для строки, ShipperID, CompanyName и телефона.  
  
 Определения схемы соответствуют [спецификации W3C XML-данных](http://www.w3.org/TR/1998/NOTE-XML-data/) и могут быть полностью проверены (Хотя проверка не будет выполнена в Internet Explorer 5). XML-данных в настоящее время является форматом только поддерживаемые схемы сохраняемости набора записей.  
  
 Раздел данных содержит три строки, содержащие сведения о них. Для пустой набор строк, в разделе данных может быть пустым, но \<rs: данные > теги должен присутствовать. Без данных, можно написать сокращением тега просто \<rs: данные / >. Любому тегу, начинаются с «rs» означает, что в пространство имен, определенное urn: schemas-microsoft-com:rowset.  
  
## <a name="see-also"></a>См. также  
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
