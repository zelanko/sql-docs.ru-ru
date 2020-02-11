---
title: Поставщик WMI для классов и свойств событий сервера | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- event classes [WMI]
- WMI Provider for Server Events, events listed
- classes [WMI]
ms.assetid: e2916cd7-a3ed-41e6-97b4-2ee060754cbe
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 24624a5071bad5403afc15259d97754a7feffdcf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63288468"
---
# <a name="wmi-provider-for-server-events-classes-and-properties"></a>Поставщик инструментария WMI для классов событий и свойств сервера
  Следующие события сервера образуют программную модель поставщика WMI для событий сервера. Существует две основные категории событий, которые могут быть опрошены с помощью запросов WQL к поставщику. Это события языка описания данных DDL и события трассировки. Запрос также можно выполнять к событиям компонента Service Broker QUEUE_ACTIVATION и BROKER_QUEUE_DISABLED. Обратите внимание на вложенную природу следующих диаграмм. Например, событие DDL_ASSEMBLY_EVENTS включает любое из событий ALTER_ASSEMBLY, CREATE_ASSEMBLY и DROP_ASSEMBLY. Аналогично, событие TRC_FULL_TEXT включает любое из событий FT_CRAWL_ABORTED, FT_CRAWL_STARTED и FT_CRAWL_STOPPED. Событие ALL_EVENTS охватывает все DDL-события, события трассировки, QUEUE_ACTIVATION и BROKER_QUEUE_DISABLED.  
  
 Сведения о том, к каким свойствам может быть выполнен запрос из события или группы событий, см. в схеме события. По умолчанию схема событий устанавливается в следующий каталог: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd.  
  
 Кроме того, можно обратиться к схеме событий, опубликованной [https://schemas.microsoft.com/sqlserver](https://go.microsoft.com/fwlink/?linkid=43100)по адресу.  
  
 Например, при обращении к событию ALTER_DATABASE выясняется, что его родительским событием является DDL_SERVER_LEVEL_EVENTS, а свойствами — `TSQLCommand` и `DatabaseName`. Событие также наследует свойства `SQLInstance`, `PostTime`, `ComputerName`, `SPID` и `LoginName`. Это событие не имеет дочерних событий.  
  
> [!NOTE]  
>  Системные хранимые процедуры, выполняющие DDL-подобные операции, также могут запускать уведомления о событиях. Протестируйте свои уведомления о событиях, чтобы определить их реакцию на системные хранимые процедуры. Например, инструкция CREATE TYPE и хранимая процедура **sp_addtype** будут вызывать уведомление о событии, созданное для события CREATE_TYPE. Дополнительные сведения см. в разделе[DDL Events](../../relational-databases/triggers/ddl-events.md).  
  
 **События и группы событий языка описания данных DDL**  
  
 ![Дерево событий поставщика WMI для событий сервера](../../../2014/database-engine/dev-guide/media/sql-wmi-ddl-events-ktm.gif "Дерево событий поставщика WMI для событий сервера")  
  
 **События трассировки и группы событий**  
  
 ![События трассировки и группы событий](../../../2014/database-engine/dev-guide/media/sql-wmi-trc-all-events.gif "События трассировки и их группы")  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия о поставщике WMI для событий сервера](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)   
 [Использование WQL с поставщиком WMI для событий сервера](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
  
  
