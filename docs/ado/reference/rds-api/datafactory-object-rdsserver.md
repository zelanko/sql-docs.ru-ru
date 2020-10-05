---
description: Объект DataFactory (RDSServer)
title: Объект фактического объекта (RDSServer) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataFactory object [ADO]
ms.assetid: e75240c2-b749-471e-b6ea-98cae232efbe
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e31d39f0820a485d4954d789fe2dfb398d8490b
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91720985"
---
# <a name="datafactory-object-rdsserver"></a>Объект DataFactory (RDSServer)
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](/dotnet/framework/wcf/).  
  
 Этот бизнес-объект на стороне сервера по умолчанию реализует методы, предоставляющие доступ к данным для чтения и записи к указанным источникам данных для клиентских приложений.  
  
 Объект **RDSServer.** DataObject разработан как объект автоматизации на стороне сервера, который получает клиентские запросы. В реализации Интернета она находится на веб-сервере и создается экземпляром компонента АДИСАПИ. Объект **RDSServer.** DataObject предоставляет доступ на чтение и запись к указанным источникам данных, но не содержит логику проверки или бизнес-правил.  
  
 При использовании метода, доступного как в **RDSServer.** , так и в [RDS. Объекты элементов управления](./datacontrol-object-rds.md) данными, служба удаленных данных использует **RDS. Версия элемента управления** по умолчанию. По умолчанию предполагается базовый сценарий программирования, где **RDSServer.** DataObject выступает в качестве универсального бизнес-объекта на стороне сервера.  
  
 Если вы хотите, чтобы веб-приложение обрабатывал обработку на стороне сервера для конкретной задачи, можно заменить **RDSServer.** DataObject на пользовательский бизнес-объект.  
  
 Можно создавать бизнес-объекты на стороне сервера, вызывающие методы **RDSServer.** , такие как [Query](./query-method-rds.md) и [CreateRecordset](./createrecordset-method-rds.md). Это полезно, если необходимо добавить функциональные возможности в бизнес-объекты, но воспользоваться преимуществами существующих технологий удаленной службы данных.  
  
 Объект **факта** не является надежным для скриптов, выполняемых на стороне клиента.  
  
 Идентификатор класса для объекта **RDSServer.** DataObject 9381D8F5-0288-11D0-9501-00AA00B911A5.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта DataFactory (RDSServer)](./datafactory-object-rdsserver-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры объекта DataFactory, а также методов Query и CreateObject (VBScript)](./datafactory-object-query-method-and-createobject-method-example-vbscript.md)