---
title: Объект фактического объекта (RDSServer) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 38b07258488539638729c55cef65770b0788a1c8
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82752616"
---
# <a name="datafactory-object-rdsserver"></a>Объект DataFactory (RDSServer)
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Этот бизнес-объект на стороне сервера по умолчанию реализует методы, предоставляющие доступ к данным для чтения и записи к указанным источникам данных для клиентских приложений.  
  
 Объект **RDSServer.** DataObject разработан как объект автоматизации на стороне сервера, который получает клиентские запросы. В реализации Интернета она находится на веб-сервере и создается экземпляром компонента АДИСАПИ. Объект **RDSServer.** DataObject предоставляет доступ на чтение и запись к указанным источникам данных, но не содержит логику проверки или бизнес-правил.  
  
 При использовании метода, доступного как в **RDSServer.** , так и в [RDS. Объекты элементов управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) данными, служба удаленных данных использует **RDS. Версия элемента управления** по умолчанию. По умолчанию предполагается базовый сценарий программирования, где **RDSServer.** DataObject выступает в качестве универсального бизнес-объекта на стороне сервера.  
  
 Если вы хотите, чтобы веб-приложение обрабатывал обработку на стороне сервера для конкретной задачи, можно заменить **RDSServer.** DataObject на пользовательский бизнес-объект.  
  
 Можно создавать бизнес-объекты на стороне сервера, вызывающие методы **RDSServer.** , такие как [Query](../../../ado/reference/rds-api/query-method-rds.md) и [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md). Это полезно, если необходимо добавить функциональные возможности в бизнес-объекты, но воспользоваться преимуществами существующих технологий удаленной службы данных.  
  
 Объект **факта** не является надежным для скриптов, выполняемых на стороне клиента.  
  
 Идентификатор класса для объекта **RDSServer.** DataObject 9381D8F5-0288-11D0-9501-00AA00B911A5.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры объекта DataFactory, а также методов Query и CreateObject (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


