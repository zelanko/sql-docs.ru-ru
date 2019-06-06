---
title: Сохранение записей в формате XML | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- XML persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: f3113ec4-ae31-428f-89c6-bc1024f128ea
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 783dfb43f1eaebcc823f49000f589542465b1735
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66701936"
---
# <a name="persisting-records-in-xml-format"></a>Сохранение записей в формате XML
Как и формат ADTG **набор записей** сохраняемости в формате XML реализуется с помощью Microsoft OLE DB поставщика сохраняемости. Этот поставщик создает набор строк однопроходный, только для чтения из сохраненных XML-файл или поток, содержащий данные схемы ADO. Аналогичным образом, может потребоваться ADO **записей**, создания XML-документа и сохраните его в файл или любой объект, реализующий COM **IStream** интерфейс. (На самом деле файл является лишь очередной пример применения объекта, который поддерживает **IStream**.) Для версии 2.5 и более поздних версий, ADO полагается на Microsoft XML Parser (MSXML) для загрузки XML в **записей**; поэтому msxml.dll не требуется.  
  
> [!NOTE]
>  Некоторые ограничения применяются при сохранении иерархические **наборы записей** (данные фигуры) в формат XML. Не удается сохранить в XML, если иерархическое **набор записей** содержит ожидающие обновления, и вы не можете сохранить параметризованную иерархические **набор записей**. Дополнительные сведения см. в разделе [сохранение фильтруются и иерархических наборов записей](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md).  
  
 Самый простой способ сохранить данные в XML и загрузить их обратно еще раз через ADO — с **Сохранить** и **откройте** методы, соответственно. В следующем примере кода ADO показано, как сохранить данные в **заголовки** таблицы в файл с именем titles.sav.  
  
```  
Dim rs as new Recordset  
Dim rs2 as new Recordset  
Dim c as new Connection  
Dim s as new Stream  
  
' Query the Titles table.  
c.Open "provider=sqloledb;data source=MySQLServer;initial catalog=pubs;Integrated Security='SSPI'"  
rs.cursorlocation = adUseClient  
rs.Open "select * from titles", c, adOpenStatic  
  
' Save to the file in the XML format. Note that if you don't specify   
' adPersistXML, a binary format (ADTG) will be used by default.  
rs.Save "titles.sav", adPersistXML  
  
' Save the recordset into the ADO Stream object.  
rs.save s, adPersistXML  
rs.Close  
c.Close  
  
set rs = nothing  
  
' Reopen the file.  
rs.Open "titles.sav",,,,adCmdFile  
' Open the Stream back into a Recordset.  
rs2.open s  
```  
  
 ADO всегда сохраняется весь **записей** объекта. Если вы хотите сохранить подмножество строк из **записей** , используйте **фильтра** метод, чтобы сузить список строк, или изменить предложение вашего выбора. Тем не менее, необходимо открыть **записей** объект с клиентский курсор (**CursorLocation** = **adUseClient**) для использования **фильтрации** метод для сохранения подмножества строк. Например, чтобы получить заголовки, начинающиеся с буквы «b», можно применить фильтр для открытого **записей** объекта:  
  
```  
rs.Filter "title_id like 'B*'"  
rs.Save "btitles.sav", adPersistXML  
```  
  
 ADO всегда использует ядро курсора клиента набора строк для получения прокручиваемым, bookmarkable **записей** объекта на основе последовательного данные, созданные поставщиком сохраняемости.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Формат сохраняемости XML](../../../ado/guide/data/xml-persistence-format.md)  
  
-   [Пространства имен](../../../ado/guide/data/namespaces.md)  
  
-   [Раздел схемы](../../../ado/guide/data/schema-section.md)  
  
-   [Раздел данных](../../../ado/guide/data/data-section.md)  
  
-   [Иерархические наборы записей в XML](../../../ado/guide/data/hierarchical-recordsets-in-xml.md)  
  
-   [Динамические свойства набора записей в XML](../../../ado/guide/data/recordset-dynamic-properties-in-xml.md)  
  
-   [Преобразования XSLT](../../../ado/guide/data/xslt-transformations.md)  
  
-   [Сохранение в объект DOM XML](../../../ado/guide/data/saving-to-the-xml-dom-object.md)  
  
-   [Вопросы безопасности при работе с XML](../../../ado/guide/data/xml-security-considerations.md)  
  
-   [Сценарий сохраняемости набора записей XML](../../../ado/guide/data/xml-recordset-persistence-scenario.md)
