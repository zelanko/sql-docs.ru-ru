---
title: "Дополнительные сведения о сохраняемости набора записей | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: a9b287f5-04b0-4514-8143-f67879ca9842
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8baac18c8d27face9438a85a2c35db57348836a3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="more-about-recordset-persistence"></a>Дополнительные сведения о сохраняемости набора записей
Объект набора записей ADO поддерживает хранение содержимого **записей** объекту в файле с помощью его [Сохранить](../../../ado/reference/ado-api/save-method.md) метод. Постоянно хранимых файл может существовать на локальном диске сервера, или как URL-адрес, на веб-сайта. С помощью более поздней версии, можно восстановить файл [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод **набора записей** объекта или [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) метод [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объект.  
  
 Кроме того [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) метод преобразует **записей** объекта в форму, в котором столбцы и строки разделяются символами.  
  
 Для сохранения **записей**, перед началом преобразования его в форму, могут храниться в файле. **Набор записей** объекты могут храниться в собственный формат дополнительные данные TableGram (ADTG) или в открытом формате расширяемого языка разметки (XML). В следующем разделе приведены примеры ADTG. Дополнительные сведения о сохраняемости XML см. в разделе [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md).  
  
 Сохраните все ожидающие изменения в сохраненный файл. Таким образом позволяет выдавать запрос, возвращающий **набора записей** объект, изменения **набора записей**, сохраняет его и ожидающие изменения, позднее восстанавливает **набора записей**, а затем обновляет источник данных, сохраненные с ожидающими изменениями.  
  
 Сведения о хранении постоянно **поток** объектов, в разделе [потоки и сохраняемость](../../../ado/guide/data/streams-and-persistence.md).  
  
 Пример **записей** сохраняемости, ознакомиться со сценарием сохраняемости XML набор записей.  
  
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
  
 Кроме того Если **записей** does имеет активное подключение, вы можете принять параметры по умолчанию и программировать следующие:  
  
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
  
### <a name="open-a-persisted-file-with-rdsdatacontrol"></a>Откройте сохраненный файл с RDS. DataControl:  
 В этом случае **сервера** свойство не задано.  
  
```  
Dim dc as New RDS.DataControl  
dc.Connection = "Provider=MSPersist"  
dc.SQL = "c:\yourFile.adtg"  
dc.Refresh  
```  
  
## <a name="see-also"></a>См. также:  
 [Метод GetString (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)   
 [Поставщик Microsoft OLE DB сохраняемости (поставщик службы ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)   
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Потоки и сохраняемости](../../../ado/guide/data/streams-and-persistence.md)

