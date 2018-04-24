---
title: Сценарий сохраняемости XML записей | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- XML persistence [ADO], persistence scenario
ms.assetid: 353d569a-043a-4397-9ee6-564c4af8d5f6
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4aa455c004305f1350fef0006ba1986932ea692c
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="xml-recordset-persistence-scenario"></a>Сценарий сохраняемости XML набора записей
В этом сценарии вы создадите приложение Active Server Pages (ASP), сохраняет содержимое объекта набора записей непосредственно в объекте отклика ASP.  
  
> [!NOTE]
>  Данный сценарий требует, что сервер Internet Information Server 5.0 (IIS) или более поздней версии.  
  
 Возвращаемый набор записей отображается в обозревателе Internet Explorer с помощью [DataControl объекта (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md).  
  
 Следующие шаги, необходимые для создания этого сценария:  
  
-   Настройка приложения  
  
-   Получение данных  
  
-   Отправка данных  
  
-   Получение и отображение данных  
  
## <a name="step-1-set-up-the-application"></a>Шаг 1: Настройка приложения  
 Создание виртуального каталога IIS, с именем «XMLPersist» и разрешения на выполнение сценариев. Создайте два новых текстовых файлов в папке, на которую виртуального каталога указывает, один именованный» XMLResponse.asp,» другие именованные «Default.htm».  
  
## <a name="step-2-get-the-data"></a>Шаг 2: Получение данных  
 На этом шаге вы напишете код для открытия набора записей ADO и подготовка для отправки клиенту. Откройте файл XMLResponse.asp в текстовом редакторе, таком как Блокнот и вставьте следующий код.  
  
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
  
 Не забудьте изменить значение `Data Source` параметр в `strCon` к имени компьютера с Microsoft SQL Server.  
  
 Файл остается открытой и перейдите к следующему шагу.  
  
## <a name="step-3-send-the-data"></a>Шаг 3: Отправка данных  
 Теперь, когда у вас есть набор записей, необходимо отправить его клиенту путем его сохранения в XML-ФАЙЛЕ объект ответа ASP. Добавьте следующий код в нижнюю часть XMLResponse.asp.  
  
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
  
 Обратите внимание, что объект ASP ответа указан в качестве цели для набора записей [метод Save](../../../ado/reference/ado-api/save-method.md). Метод Save пункт назначения может быть любой объект, который поддерживает интерфейс IStream, таких как ADO [поток Objects (ADO)](../../../ado/reference/ado-api/stream-object-ado.md), или имя файла, который включает в себя полный путь, к которому должен быть сохранен набор записей.  
  
 Сохраните и закройте XMLResponse.asp перед переходом к следующему шагу. Также скопируйте файл adovbs.inc из папки установки библиотеки по умолчанию ADO в ту же папку, где был сохранен файл XMLResponse.asp.  
  
## <a name="step-4-receive-and-display-the-data"></a>Шаг 4: Получение и отображение данных  
 На этом шаге вы создадите в HTML-файл с встроенный [DataControl объекта (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md) объект, указывающий на файл XMLResponse.asp, чтобы получить набор записей. Откройте файл default.htm в текстовом редакторе, таком как Блокнот и добавьте следующий код. Замените на имя вашего сервера «sqlserver» в URL-АДРЕСЕ.  
  
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
  
 Закройте файл default.htm и сохраните его в ту же папку, где был сохранен XMLResponse.asp. С помощью Internet Explorer 4.0 или более поздней версии, откройте URL-адрес http://*sqlserver*/XMLPersist/default.htm и просмотрите результаты. Данные отображаются в связанной таблицы DHTML. Теперь откройте URL-адрес http:// *sqlserver* /XMLPersist/XMLResponse.asp и просмотрите результаты. Отображается XML-код.  
  
## <a name="see-also"></a>См. также  
 [Save-метод](../../../ado/reference/ado-api/save-method.md)   
 [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
