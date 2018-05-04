---
title: Поставщик WMI для событий сервера классы и свойства | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- event classes [WMI]
- WMI Provider for Server Events, events listed
- classes [WMI]
ms.assetid: e2916cd7-a3ed-41e6-97b4-2ee060754cbe
caps.latest.revision: 33
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f005b3b5f6bce5d3ce5884b5209ba1882fa245da
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="wmi-provider-for-server-events-classes-and-properties"></a>Поставщик инструментария WMI для классов событий и свойств сервера
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Следующие события сервера образуют программную модель поставщика WMI для событий сервера. Существует две основные категории событий, которые могут быть опрошены с помощью запросов WQL к поставщику. Это события языка описания данных DDL и события трассировки. Запрос также можно выполнять к событиям компонента Service Broker QUEUE_ACTIVATION и BROKER_QUEUE_DISABLED. Обратите внимание на вложенную природу следующих диаграмм. Например, событие DDL_ASSEMBLY_EVENTS включает любое из событий ALTER_ASSEMBLY, CREATE_ASSEMBLY и DROP_ASSEMBLY. Аналогично, событие TRC_FULL_TEXT включает любое из событий FT_CRAWL_ABORTED, FT_CRAWL_STARTED и FT_CRAWL_STOPPED. Событие ALL_EVENTS охватывает все DDL-события, события трассировки, QUEUE_ACTIVATION и BROKER_QUEUE_DISABLED.  
  
 Сведения о том, к каким свойствам может быть выполнен запрос из события или группы событий, см. в схеме события. По умолчанию схема события устанавливается в следующий каталог: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd.  
  
 Кроме того, можно ссылаться на схемы событий опубликованы по адресу [ http://schemas.microsoft.com/sqlserver ](http://go.microsoft.com/fwlink/?linkid=43100).  
  
 Например, путем обращения к событию ALTER_DATABASE вы узнаете, что его родительским событием является DDL_SERVER_LEVEL_EVENTS, а его свойства имеют **TSQLCommand** и **DatabaseName**. Это событие также наследует свойства **SQLInstance**, **PostTime**, **ComputerName**, **SPID**, и **LoginName** . Это событие не имеет дочерних событий.  
  
> [!NOTE]  
>  Системные хранимые процедуры, выполняющие DDL-подобные операции, также могут запускать уведомления о событиях. Протестируйте свои уведомления о событиях, чтобы определить их реакцию на системные хранимые процедуры. Например, инструкция CREATE TYPE и **sp_addtype** хранимой процедуры вызывают срабатывание уведомления о событии, созданного на событии CREATE_TYPE. Дополнительные сведения см. в разделе[DDL-события](../../relational-databases/triggers/ddl-events.md).  
  
 **События языка описания данных и группы событий**  
  
 ![Поставщик WMI для дерево событий сервера событий](../../relational-databases/wmi-provider-server-events/media/sql-wmi-ddl-events-ktm.gif "поставщик WMI для дерево событий для событий сервера")  
  
 **События трассировки и их группы**  
  
 ![Трассировка событий и групп событий](../../relational-databases/wmi-provider-server-events/media/sql-wmi-trc-all-events.gif "трассировки события и их группы")  
  
## <a name="see-also"></a>См. также  
 [Поставщик WMI для событий принципы работы сервера](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)   
 [Использование WQL с поставщиком WMI для событий сервера](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
  
  
