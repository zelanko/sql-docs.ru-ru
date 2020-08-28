---
description: Дополнительные сведения о сохраняемости набора записей
title: Дополнительные сведения о сохраняемости наборов записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1dca646b07c441a4fccd617723aba98536f1a7e1
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980335"
---
# <a name="more-about-recordset-persistence"></a>Дополнительные сведения о сохраняемости набора записей
Объект ADO Recordset поддерживает хранение содержимого объекта **набора записей** в файле с помощью метода [Save](../../reference/ado-api/save-method.md) . Сохраняемый файл может находиться на локальном диске, сервере или в качестве URL-адреса на веб – сайте. Позднее файл можно восстановить с помощью метода [Open](../../reference/ado-api/open-method-ado-recordset.md) объекта **Recordset** или метода [EXECUTE](../../reference/ado-api/execute-method-ado-connection.md) объекта [Connection](../../reference/ado-api/connection-object-ado.md) .  
  
 Кроме того, метод [GetString](../../reference/ado-api/getstring-method-ado.md) преобразует объект **набора записей** в форму, в которой столбцы и строки разделяются заданными символами.  
  
 Чтобы сохранить **набор записей**, начните с преобразования его в форму, которая может храниться в файле. Объекты **набора записей** могут храниться в собственном формате Advanced Data ТАБЛЕГРАМ (адтг) или в формате Open язык XML (XML). Примеры АДТГ приведены в следующем разделе. Дополнительные сведения о сохраняемости XML см. [в разделе Сохранение записей в формате XML](./persisting-records-in-xml-format.md).  
  
 Сохраните все ожидающие изменения в материализованном файле. Это позволяет выдать запрос, возвращающий объект **Recordset** , изменяя **набор записей**, сохраняя его и ожидающие изменения, позднее восстанавливает **набор записей**, а затем обновляет источник данных с помощью сохраненных ожидающих изменений.  
  
 Сведения о постоянном хранении объектов **потока** см. в разделе [потоки и сохраняемость](./streams-and-persistence.md).  
  
 Пример сохраняемости **набора записей** см. в разделе сценарий сохраняемости в XML-наборе записей.  
  
## <a name="example"></a>Пример  
  
### <a name="save-a-recordset"></a>Сохранить набор записей:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Save "c:\yourFile.adtg", adPersistADTG  
```  
  
### <a name="open-a-persisted-file-with-recordsetopen"></a>Открытие сохраненного файла с набором записей. Откройте:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg", "Provider=MSPersist",,,adCmdFile  
```  
  
 Кроме того, если **набор записей** не имеет активного подключения, можно принять все значения по умолчанию и выполнить код следующим образом:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg"  
```  
  
### <a name="open-a-persisted-file-with-connectionexecute"></a>Откройте сохраненный файл с Connection.Exeмилые:  
  
```  
Dim conn as New ADODB.Connection  
Dim rs as ADODB.Recordset  
conn.Open "Provider=MSPersist"  
Set rs = conn.execute("c:\yourFile.adtg")  
```  
  
### <a name="open-a-persisted-file-with-rdsdatacontrol"></a>Откройте сохраненный файл с помощью RDS. DataControl  
 В этом случае свойство **сервера** не задано.  
  
```  
Dim dc as New RDS.DataControl  
dc.Connection = "Provider=MSPersist"  
dc.SQL = "c:\yourFile.adtg"  
dc.Refresh  
```  
  
## <a name="see-also"></a>См. также  
 [Метод GetString (ADO)](../../reference/ado-api/getstring-method-ado.md)   
 [Поставщик сохраняемости Microsoft OLE DB (поставщик служб ADO)](../appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)   
 [Объект Recordset (ADO)](../../reference/ado-api/recordset-object-ado.md)   
 [Потоки и сохраняемость](./streams-and-persistence.md)