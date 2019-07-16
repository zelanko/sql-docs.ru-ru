---
title: Дополнительные сведения о сохраняемости набора записей | Документация Майкрософт
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
- updating data [ADO], persisting data
ms.assetid: a9b287f5-04b0-4514-8143-f67879ca9842
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bee7d185d5f598a2f0a086bb7e3bea49ddfff88c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924915"
---
# <a name="more-about-recordset-persistence"></a>Дополнительные сведения о сохраняемости набора записей
Объект ADO Recordset поддерживает хранение содержимого **записей** объекта в файл с помощью его [Сохранить](../../../ado/reference/ado-api/save-method.md) метод. Постоянно сохраненного файла могут существовать на локальном диске сервера, или как URL-адрес, на веб-сайта. Позже, можно восстановить файл с помощью [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод **записей** объекта или [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) метод [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объект.  
  
 Кроме того [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) метод преобразует **записей** объекта в форму, в котором столбцы и строки разделяются символами.  
  
 Для сохранения **записей**, перед началом преобразования его в форму, которые могут храниться в файле. **Набор записей** объекты могут храниться в собственный формат Advanced данных TableGram (ADTG) или формате open Extensible Markup Language (XML). В следующем разделе показаны примеры ADTG. Дополнительные сведения о сохраняемости XML, см. в разделе [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md).  
  
 Сохраните все ожидающие изменения в сохраненный файл. Это позволяет выдавать запрос, возвращающий **набор записей** объекта, изменения **набор записей**, сохраняет его и ожидающие изменения, позже восстанавливает **набор записей**, а затем обновляет источник данных с помощью сохраненного ожидающие изменения.  
  
 Сведения о хранении постоянно **Stream** объектов, см. в разделе [потоки и сохраняемость](../../../ado/guide/data/streams-and-persistence.md).  
  
 Пример **записей** сохраняемости, см. в разделе сценарий сохраняемости набора записей XML.  
  
## <a name="example"></a>Пример  
  
### <a name="save-a-recordset"></a>Сохраните набор записей:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Save "c:\yourFile.adtg", adPersistADTG  
```  
  
### <a name="open-a-persisted-file-with-recordsetopen"></a>Откройте сохраненный файл с Recordset.Open:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg", "Provider=MSPersist",,,adCmdFile  
```  
  
 При необходимости Если **записей** does имеет активное подключение, вы можете принять все значения по умолчанию и кода следующее:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg"  
```  
  
### <a name="open-a-persisted-file-with-connectionexecute"></a>Откройте сохраненный файл с Connection.Execute:  
  
```  
Dim conn as New ADODB.Connection  
Dim rs as ADODB.Recordset  
conn.Open "Provider=MSPersist"  
Set rs = conn.execute("c:\yourFile.adtg")  
```  
  
### <a name="open-a-persisted-file-with-rdsdatacontrol"></a>Откройте сохраненный файл в RDS. DataControl:  
 В этом случае **Server** свойство не задано.  
  
```  
Dim dc as New RDS.DataControl  
dc.Connection = "Provider=MSPersist"  
dc.SQL = "c:\yourFile.adtg"  
dc.Refresh  
```  
  
## <a name="see-also"></a>См. также  
 [Метод GetString (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)   
 [Поставщик Microsoft OLE DB сохраняемости (поставщик услуг ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Потоки и сохраняемость](../../../ado/guide/data/streams-and-persistence.md)
