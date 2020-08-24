---
description: Сценарий сохраняемости набора записей XML
title: Сценарий сохраняемости XML-наборов записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XML persistence [ADO], persistence scenario
ms.assetid: 353d569a-043a-4397-9ee6-564c4af8d5f6
author: rothja
ms.author: jroth
ms.openlocfilehash: 42fbc8670320761697caf4c956c1f9b64bda5c24
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88758424"
---
# <a name="xml-recordset-persistence-scenario"></a>Сценарий сохраняемости набора записей XML
В этом сценарии вы создадите приложение Active Server страниц (ASP), которое сохраняет содержимое объекта набора записей непосредственно в объекте ответа ASP.  
  
> [!NOTE]
>  В этом сценарии требуется, чтобы на сервере был установлен Internet Information Server 5,0 (IIS) или более поздней версии.  
  
 Возвращенный набор записей отображается в Internet Explorer с помощью [объекта элемента управления (RDS)](../../reference/rds-api/datacontrol-object-rds.md).  
  
 Для создания этого сценария необходимо выполнить следующие действия.  
  
-   Настройка приложения  
  
-   Получение данных  
  
-   Отправка данных  
  
-   Получение и отображение данных  
  
## <a name="step-1-set-up-the-application"></a>Шаг 1. Настройка приложения  
 Создайте виртуальный каталог IIS с именем "Ксмлперсист" и разрешениями на выполнение сценариев. Создайте два новых текстовых файла в папке, на которую указывает виртуальный каталог, с именем «Ксмлреспонсе. ASP», другим именем «Default.htm».  
  
## <a name="step-2-get-the-data"></a>Шаг 2. получение данных  
 На этом шаге будет написан код для открытия набора записей ADO и подготовки к его отправке клиенту. Откройте файл Ксмлреспонсе. ASP в текстовом редакторе, например в блокноте, и вставьте следующий код.  
  
```  
<%@ language="VBScript" %>  
  
<!-- #include file='adovbs.inc' -->  
  
<%  
  Dim strSQL, strCon  
  Dim adoRec   
  Dim adoCon   
  Dim xmlDoc   
  
  ' You will need to change "MySQLServer" below to the name of the SQL   
  ' server machine to which you want to connect.  
  strCon = "Provider=sqloledb;Data Source=MySQLServer;Initial Catalog=Pubs;Integrated Security=SSPI;"  
  Set adoCon = server.createObject("ADODB.Connection")  
  adoCon.Open strCon  
  
  strSQL = "SELECT Title, Price FROM Titles ORDER BY Price"  
  Set adoRec = Server.CreateObject("ADODB.Recordset")  
  adoRec.Open strSQL, adoCon, adOpenStatic, adLockOptimistic, adCmdText  
```  
  
 Не забудьте изменить значение `Data Source` параметра в `strCon` на имя компьютера Microsoft SQL Server.  
  
 Не закрывайте файл и переходите к следующему шагу.  
  
## <a name="step-3-send-the-data"></a>Шаг 3. Отправка данных  
 Теперь, когда у вас есть набор записей, необходимо отправить его клиенту, сохранив его в формате XML в объекте ответа ASP. Добавьте следующий код в нижнюю часть Ксмлреспонсе. ASP.  
  
```  
  Response.ContentType = "text/xml"  
  Response.Expires = 0  
  Response.Buffer = False  
  
  Response.Write "<?xml version='1.0'?>" & vbNewLine  
  adoRec.save Response, adPersistXML  
  adoRec.Close  
  Set adoRec=Nothing  
%>  
```  
  
 Обратите внимание, что в качестве места назначения для [метода Save](../../reference/ado-api/save-method.md)набора записей указан объект ответа ASP. Назначением метода Save может быть любой объект, поддерживающий интерфейс IStream, например [объект потока ADO (ADO)](../../reference/ado-api/stream-object-ado.md), или имя файла, включающее полный путь, по которому будет сохранен набор записей.  
  
 Сохраните и закройте Ксмлреспонсе. ASP перед переходом к следующему шагу. Также скопируйте файл адовбс. Inc из папки установки по умолчанию библиотеки ADO в ту же папку, где был сохранен файл Ксмлреспонсе. ASP.  
  
## <a name="step-4-receive-and-display-the-data"></a>Шаг 4. получение и отображение данных  
 На этом шаге вы создадите HTML-файл с внедренным объектом [элемента управления данными (RDS)](../../reference/rds-api/datacontrol-object-rds.md) , который указывает на файл ксмлреспонсе. ASP, который будет получать набор записей. Откройте default.htm с помощью текстового редактора, например Блокнота, и добавьте следующий код. Замените "SQLServer" в URL-адресе именем сервера.  
  
```  
<HTML>  
<HEAD><TITLE>ADO Recordset Persistence Sample</TITLE></HEAD>  
<BODY>  
  
<TABLE DATASRC="#RDC1" border="1">  
  <TR>  
<TD><SPAN DATAFLD="title"></SPAN></TD>  
<TD><SPAN DATAFLD="price"></SPAN></TD>  
  </TR>  
</TABLE>  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="RDC1">  
   <PARAM NAME="URL" VALUE="XMLResponse.asp">  
</OBJECT>  
  
</BODY>  
</HTML>  
```  
  
 Закройте файл default.htm и сохраните его в той же папке, где сохранен Ксмлреспонсе. ASP. В Internet Explorer 4,0 или более поздней версии откройте URL-адрес https://*SQLServer*/ксмлперсист/default.htm и просмотрите результаты. Данные отображаются в связанной таблице DHTML. Теперь откройте URL-адрес https:// *SQLServer* /ксмлперсист/ксмлреспонсе.АСП и просмотрите результаты. Отобразится XML.  
  
## <a name="see-also"></a>См. также  
 [Метод Save](../../reference/ado-api/save-method.md)   
 [Сохранение записей в формате XML](./persisting-records-in-xml-format.md)