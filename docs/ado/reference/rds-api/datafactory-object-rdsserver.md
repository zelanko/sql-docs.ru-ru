---
title: "Объект DataFactory (RDSServer) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- DataFactory object [ADO]
ms.assetid: e75240c2-b749-471e-b6ea-98cae232efbe
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: db11cc8488b2ca2d3083ca95ac124cbe15b5313c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="datafactory-object-rdsserver"></a>Объект DataFactory (RDSServer)
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Этот объект business на стороне сервера по умолчанию реализует методы, предоставляющие доступ к данным чтение и запись для указанного источника данных для клиентских приложений.  
  
 **RDSServer.DataFactory** как серверный объект автоматизации, которая получает запросы клиента был создан объект. В реализации Интернет он находится на веб-сервере и создается с помощью компонента ADISAPI. **RDSServer.DataFactory** обеспечивает чтение и запись в указанных данных источников, но не содержит логику проверки или бизнес-правила.  
  
 Если вы используете метод, который доступен в обеих **RDSServer.DataFactory** и [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объектов, удаленных данных служба использует **RDS. DataControl** версию по умолчанию. Значение по умолчанию предполагается базовый сценарий для программирования, где **RDSServer.DataFactory** служит в качестве универсального серверных бизнес-объекта.  
  
 Если требуется, чтобы веб-приложения для обработки определенных задач обработки на сервере, можно заменить **RDSServer.DataFactory** с пользовательский бизнес-объект.  
  
 Можно создать бизнес-серверные объекты, которые вызывают **RDSServer.DataFactory** методы, такие как [запроса](../../../ado/reference/rds-api/query-method-rds.md) и [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md). Это полезно, если вы хотите добавить функциональные возможности бизнес-объектов, но воспользоваться преимуществами существующих технологий удаленной службы данных.  
  
 **DataFactory** объект не является безопасным для сценариев, выполняемых на стороне клиента.  
  
 Идентификатор класса для **RDSServer.DataFactory** объект является 9381D8F5-0288-11 D 0-9501-00AA00B911A5.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры объекта DataFactory, а также методов Query и CreateObject (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


