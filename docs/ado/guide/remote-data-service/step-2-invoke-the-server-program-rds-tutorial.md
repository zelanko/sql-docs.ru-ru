---
description: Шаг 2. Вызовите программу сервера (учебник по RDS)
title: Шаг 2. вызов серверной программы (учебник по RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], invoking server program
ms.assetid: 5e74c2da-65ee-4de4-8b41-6eac45c3632e
author: rothja
ms.author: jroth
ms.openlocfilehash: 19f16da3e3501a179bfb28529a9b1a14486aad20
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759154"
---
# <a name="step-2-invoke-the-server-program-rds-tutorial"></a>Шаг 2. Вызовите программу сервера (учебник по RDS)
При вызове метода *прокси-сервера*клиента фактическая программа на сервере выполняет метод. На этом шаге вы выполните запрос на сервере.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 **Часть A** Если вы не использовали [RDSServer.](../../reference/rds-api/datafactory-object-rdsserver.md) в этом руководстве, самый удобный способ выполнить это действие — использовать [RDS. Объект элемента управления](../../reference/rds-api/datacontrol-object-rds.md) . **RDS. Элемент управления** данными объединяет предыдущий этап создания учетной записи-посредника, выполняя этот шаг, выполнив запрос.  
  
 Задайте **RDS. ** Свойство [сервера](../../reference/rds-api/server-property-rds.md) «элемент управления DataObject», которое определяет, где следует создать экземпляр программы сервера; Свойство [Connect](../../reference/rds-api/connect-property-rds.md) для указания строки подключения для доступа к источнику данных; и свойство [SQL](../../reference/rds-api/sql-property.md) для указания текста команды запроса. Затем выдайте метод [Refresh](../../reference/rds-api/refresh-method-rds.md) , чтобы программа сервера подключится к источнику данных, получала строки, указанные запросом, и возвращала клиенту объект **набора записей** .  
  
 В этом руководстве не используется **RDS. Элемент управления**данным, но это будет выглядеть, если:  
  
```vb
Sub RDSTutorial2A()  
   Dim DC as New RDS.DataControl  
   DC.Server = "https://yourServer"  
   DC.Connect = "DSN=Pubs"  
   DC.SQL = "SELECT * FROM Authors"  
   DC.Refresh  
...  
```  
  
 Кроме того, в учебнике не вызывается RDS с объектами ADO, но вот как это будет выглядеть, если:  
  
```vb
Dim rs as New ADODB.Recordset  
rs.Open "SELECT * FROM Authors","Provider=MS Remote;Data Source=Pubs;" & _  
        "Remote Server=https://yourServer;Remote Provider=SQLOLEDB;"  
```  
  
 **Часть B** Общий метод выполнения этого шага — вызов метода [запроса](../../reference/rds-api/query-method-rds.md) объекта **RDSServer.** DataObject. Этот метод принимает строку соединения, которая используется для подключения к источнику данных, и текст команды, который используется для указания строк, возвращаемых из источника данных.  
  
 В этом руководстве используется метод **запроса** объекта **факта** :  
  
```vb
Sub RDSTutorial2B()  
   Dim DS as New RDS.DataSpace  
   Dim DF  
   Dim RS as ADODB.Recordset  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "https://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>См. также  
 [Шаг 3. сервер получает набор записей (учебник по RDS)](./step-3-server-obtains-a-recordset-rds-tutorial.md)   
 [Учебник по RDS (VBScript)](./rds-tutorial-vbscript.md)