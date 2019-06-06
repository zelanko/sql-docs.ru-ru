---
title: Сценарий сохраняемости набора записей XML | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 893921a7100ca22cae219f5a0e88d543499053b1
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66699693"
---
# <a name="xml-recordset-persistence-scenario"></a>Сценарий сохраняемости набора записей XML
В этом сценарии вы создадите приложение Active Server Pages (ASP), сохраняет содержимое объекта Recordset непосредственно в объекте отклика ASP.  
  
> [!NOTE]
>  Данный сценарий требует, что сервер Internet Information Server 5.0 (IIS) или более поздней версии.  
  
 Возвращенное подмножество записей отображается в Internet Explorer с помощью [объекта DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md).  
  
 Чтобы создать этот сценарий необходимы следующие действия:  
  
-   Настройка приложения  
  
-   Получить данные  
  
-   Отправка данных  
  
-   Получение и отображение данных  
  
## <a name="step-1-set-up-the-application"></a>Шаг 1. Настройка приложения  
 Создайте виртуальный каталог IIS, с именем «XMLPersist» и внести в скрипт разрешения. Создайте два новых текстовых файлов в папке, на который виртуального каталога указывает, один именованный «XMLResponse.asp,» другие именованные «Default.htm».  
  
## <a name="step-2-get-the-data"></a>Шаг 2. Получить данные  
 На этом шаге вы напишете код, чтобы открыть набор записей ADO и Подготовка к отправить его клиенту. Откройте файл XMLResponse.asp в текстовом редакторе, таком как Блокнот и вставьте следующий код.  
  
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
  
 Не забудьте изменить значение `Data Source` параметр в `strCon` имя компьютера с Microsoft SQL Server.  
  
 Оставьте файл открытым и переходите к следующему шагу.  
  
## <a name="step-3-send-the-data"></a>Шаг 3. Отправка данных  
 Теперь, когда у вас есть набор записей, его необходимо отправить клиенту, сохранив его в формате XML в объект ответа ASP. Добавьте следующий код в нижнюю часть XMLResponse.asp.  
  
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
  
 Обратите внимание на то, что объект ответа ASP указан в качестве места назначения для набора записей [метода Save](../../../ado/reference/ado-api/save-method.md). Цель-метод Save может быть любой объект, который поддерживает интерфейс IStream, таких как ADO [объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md), или имя файла, которое включает в себя полный путь, к которому он должен быть сохранен.  
  
 Сохраните и закройте XMLResponse.asp перед переходом к следующему шагу. Также скопируйте файл adovbs.inc из папки установки по умолчанию ADO библиотеки в ту же папку, где был сохранен файл XMLResponse.asp.  
  
## <a name="step-4-receive-and-display-the-data"></a>Шаг 4. Получение и отображение данных  
 На этом шаге вы создадите файл HTML с помощью встроенного [объекта DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md) объект, который указывает на файл XMLResponse.asp для получения набора записей. Откройте файл default.htm в текстовом редакторе, таком как Блокнот и добавьте следующий код. Замените на имя вашего сервера «sqlserver» в URL-адрес.  
  
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
  
 Закройте файл default.htm и сохраните его в ту же папку, где был сохранен XMLResponse.asp. С помощью Internet Explorer 4.0 или более поздней версии, откройте URL-адрес https://*sqlserver*/XMLPersist/default.htm и просмотрите результаты. Данные отображаются в связанной таблицы DHTML. Теперь откройте URL-адрес https:// *sqlserver* /XMLPersist/XMLResponse.asp и просмотрите результаты. Отображается XML-код.  
  
## <a name="see-also"></a>См. также  
 [Метод Save](../../../ado/reference/ado-api/save-method.md)   
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
