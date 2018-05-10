---
title: 'Шаг 6: Изменения будут отправлены на сервер (учебник служб удаленных рабочих СТОЛОВ) | Документы Microsoft'
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
- RDS tutorial [ADO], changes sent to server
ms.assetid: b1e927d6-7d50-4978-9eef-045043cdce7a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6be2159907d58f6799a2ca7b4ffb685f524baacc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="step-6-changes-are-sent-to-the-server-rds-tutorial"></a>Шаг 6: Изменения будут отправлены на сервер (учебник служб удаленных рабочих СТОЛОВ)
Если **записей** редактирования объекта, любые изменения (строк, которые будут добавлены, изменены или удалены) могут отправляться на сервер.  
  
> [!NOTE]
>  Поведения служб удаленных рабочих СТОЛОВ по умолчанию могут вызываться неявно с объектами ADO и поставщик OLE DB удаленного взаимодействия. Запросы могут возвращать **записей**s и редактировать их **записей**s можно обновить источник данных. Этот учебник без вызова служб удаленных рабочих СТОЛОВ с объектами ADO, но он будет выглядеть случае:  
  
```  
Dim rs as New ADODB.Recordset  
rs. "SELECT * FROM Authors","=MS Remote;=Pubs;" & _  
=http://yourServer;=SQLOLEDB;"  
...              ' Edit the Recordset.  
rs.   ' The equivalent of   
...  
```  
  
 **Часть** Предположим, что для этого случая, который использовался только [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) и что **записей** объекта теперь связан с **RDS. DataControl**. [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) метод обновляет любые изменения в источнике данных **записей** объекта, если [сервера](../../../ado/reference/rds-api/server-property-rds.md) и [подключение](../../../ado/reference/rds-api/connect-property-rds.md) свойства задаются по-прежнему.  
  
```  
Sub RDSTutorial6A()  
Dim DC as New RDS.DataControl  
Dim RS as ADODB.Recordset  
DC. = "http://yourServer"  
DC. = "DSN=Pubs"  
DC. = "SELECT * FROM Authors"  
DC.  
...  
Set RS = DC.  
   ' Edit the Recordset.  
...  
DC.  
...  
```  
  
 **Часть Б** также может обновить сервер с [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта, указание соединения и **записей** объекта.  
  
```  
Sub RDSTutorial6B()  
Dim DS As New RDS.DataSpace  
Dim RS As ADODB.Recordset  
Dim DC As New RDS.DataControl  
Dim DF As Object  
Dim blnStatus As Boolean  
Set DF = DS.("RDSServer.DataFactory", "http://yourServer")  
Set RS = DF. ("DSN=Pubs", "SELECT * FROM Authors")  
DC. = RS    ' Visual controls can now bind to DC.  
    ' Edit the Recordset.  
blnStatus = DF."DSN=Pubs", RS  
End Sub  
```  
  
 **Это конец учебника.**  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также  
 [Поставщик Microsoft OLE DB удаленного взаимодействия (поставщик службы ADO)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)   
 [Учебник служб удаленных рабочих СТОЛОВ](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
