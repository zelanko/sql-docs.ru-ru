---
title: "Шаг 2: Вызвать программу Server (учебник служб удаленных рабочих СТОЛОВ) | Документы Microsoft"
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
helpviewer_keywords: RDS tutorial [ADO], invoking server program
ms.assetid: 5e74c2da-65ee-4de4-8b41-6eac45c3632e
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b2686f9206b49cd193cda9970aad72a10d75c482
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="step-2-invoke-the-server-program-rds-tutorial"></a>Шаг 2: Вызвать программу Server (служб удаленных рабочих СТОЛОВ учебник)
При вызове метода на клиенте *прокси-сервера*, самой программы на сервере выполняется метод. На этом шаге будет выполнить запрос на сервере.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 **Часть** Если вы не использовали [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) в этом учебнике будет использовать наиболее удобным способом для выполнения этого шага [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта. **RDS. DataControl** объединяет предыдущий шаг создания прокси-сервера, с помощью этого этапа, выполняющего запрос.  
  
 Задать **RDS. DataControl** объекта [сервера](../../../ado/reference/rds-api/server-property-rds.md) свойство для идентификации, где должен создаваться серверной программы; [Connect](../../../ado/reference/rds-api/connect-property-rds.md) свойство, чтобы указать строку соединения для доступа к источнику данных; и [SQL](../../../ado/reference/rds-api/sql-property.md) свойство, чтобы указать текст команды запроса. Затем выдать [обновление](../../../ado/reference/rds-api/refresh-method-rds.md) метод, чтобы вызвать программу сервера для подключения к источнику данных, получения строк, указанных в запросе и возвращают **записей** объект клиенту.  
  
 Этот учебник не использует **RDS. DataControl**, но он будет выглядеть случае:  
  
```  
Sub RDSTutorial2A()  
   Dim DC as New RDS.DataControl  
   DC.Server = "http://yourServer"  
   DC.Connect = "DSN=Pubs"  
   DC.SQL = "SELECT * FROM Authors"  
   DC.Refresh  
...  
```  
  
 Ни учебника вызывают служб удаленных рабочих СТОЛОВ с объектами ADO, но он будет выглядеть случае:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "SELECT * FROM Authors","Provider=MS Remote;Data Source=Pubs;" & _  
        "Remote Server=http://yourServer;Remote Provider=SQLOLEDB;"  
```  
  
 **Часть Б** общий метод выполнения этого этапа заключается в вызове **RDSServer.DataFactory** объекта [запроса](../../../ado/reference/rds-api/query-method-rds.md) метод. Этот метод принимает строку подключения, которая используется для подключения к источнику данных, и текст команды, который используется для указания удаляемых строк, возвращаемых из источника данных.  
  
 В этом учебнике используется **DataFactory** объекта **запроса** метод:  
  
```  
Sub RDSTutorial2B()  
   Dim DS as New RDS.DataSpace  
   Dim DF  
   Dim RS as ADODB.Recordset  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>См. также:  
 [Шаг 3: Сервер получает набор записей (учебник служб удаленных рабочих СТОЛОВ)](../../../ado/guide/remote-data-service/step-3-server-obtains-a-recordset-rds-tutorial.md)   
 [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
