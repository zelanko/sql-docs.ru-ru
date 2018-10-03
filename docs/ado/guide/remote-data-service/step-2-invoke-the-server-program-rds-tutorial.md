---
title: 'Шаг 2: Вызовите программу сервера (учебник по RDS) | Документация Майкрософт'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], invoking server program
ms.assetid: 5e74c2da-65ee-4de4-8b41-6eac45c3632e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0a2e7b62276234dcf11067395ff2512a8e93af96
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47800512"
---
# <a name="step-2-invoke-the-server-program-rds-tutorial"></a>Шаг 2. Вызовите программу сервера (учебник по RDS)
При вызове метода на клиенте *прокси-сервера*, самой программы на сервере выполняется метод. На этом шаге будет выполняться запрос на сервере.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 **Часть** Если вы не использовали [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) в этом руководстве будет использовать наиболее удобным способом для выполнения этого шага [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта. **RDS. DataControl** объединяет на предыдущем шаге создания прокси-сервер, на этом этапе, выполняющего запрос.  
  
 Задайте **RDS. DataControl** объект [Server](../../../ado/reference/rds-api/server-property-rds.md) свойство, чтобы определить, где должен создаваться программу сервера; [Connect](../../../ado/reference/rds-api/connect-property-rds.md) свойство, чтобы указать строку соединения для доступа к источнику данных; и [SQL](../../../ado/reference/rds-api/sql-property.md) свойство, чтобы указать текст команды запроса. Затем выполните [обновить](../../../ado/reference/rds-api/refresh-method-rds.md) метод, чтобы вызвать программу сервера для подключения к источнику данных, получения строк, указанных в запросе и возвращают **записей** объект клиенту.  
  
 Этом руководстве используется **RDS. DataControl**, но это, как она будет выглядеть при как:  
  
```  
Sub RDSTutorial2A()  
   Dim DC as New RDS.DataControl  
   DC.Server = "http://yourServer"  
   DC.Connect = "DSN=Pubs"  
   DC.SQL = "SELECT * FROM Authors"  
   DC.Refresh  
...  
```  
  
 Ни руководства вызывают RDS с объектами ADO, но это, как она будет выглядеть при как:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "SELECT * FROM Authors","Provider=MS Remote;Data Source=Pubs;" & _  
        "Remote Server=http://yourServer;Remote Provider=SQLOLEDB;"  
```  
  
 **Часть Б** общий метод выполнения этого этапа заключается в вызове **RDSServer.DataFactory** объект [запроса](../../../ado/reference/rds-api/query-method-rds.md) метод. Этот метод принимает строку подключения, которая используется для подключения к источнику данных, и текст команды, который используется для указания строк, возвращаемых из источника данных.  
  
 В этом руководстве используется **DataFactory** объект **запроса** метод:  
  
```  
Sub RDSTutorial2B()  
   Dim DS as New RDS.DataSpace  
   Dim DF  
   Dim RS as ADODB.Recordset  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>См. также  
 [Шаг 3: Сервер получает набор записей (учебник по RDS)](../../../ado/guide/remote-data-service/step-3-server-obtains-a-recordset-rds-tutorial.md)   
 [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
