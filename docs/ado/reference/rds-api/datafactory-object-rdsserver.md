---
title: Объект DataFactory (RDSServer) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataFactory object [ADO]
ms.assetid: e75240c2-b749-471e-b6ea-98cae232efbe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 512174e0a5e8e593dcfbd075d5f459cb2d92d8c9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602772"
---
# <a name="datafactory-object-rdsserver"></a>Объект DataFactory (RDSServer)
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Этот объект серверной бизнес-по умолчанию реализует методы, предоставляющие доступ к данным чтение и запись для указанного источника данных для клиентских приложений.  
  
 **RDSServer.DataFactory** объект разработано как объект автоматизации на стороне сервера, который получает запросы от клиентов. В реализации Интернета он находится на веб-сервере и создается компонентом ADISAPI. **RDSServer.DataFactory** объект обеспечивает чтение и запись для указанных данных источников, однако не содержит логику проверки или бизнес-правила.  
  
 Если вы используете метод, который доступен в обеих **RDSServer.DataFactory** и [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объектов, служба Remote Data Service использует **RDS. DataControl** версии по умолчанию. По умолчанию предполагается, что базовые сценарии программирования, где **RDSServer.DataFactory** служит в качестве универсального серверных бизнес-объекта.  
  
 Если требуется, чтобы веб-приложения для обработки задач обработки на стороне сервера, вы можете заменить **RDSServer.DataFactory** с помощью пользовательских бизнес-объекта.  
  
 Можно создавать серверной бизнес-объекты, которые вызывают **RDSServer.DataFactory** методы, такие как [запроса](../../../ado/reference/rds-api/query-method-rds.md) и [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md). Это может оказаться полезным, если вы хотите добавить функциональные возможности бизнес-объекты, но воспользоваться преимуществами существующих технологий удаленной службы данных.  
  
 **DataFactory** объект не является безопасным для сценариев, которые выполняются на стороне клиента.  
  
 Идентификатор класса для **RDSServer.DataFactory** 9381D8F5-0288-11 D 0-9501-00AA00B911A5 является объект.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события объекта DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры объекта DataFactory, а также методов Query и CreateObject (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


