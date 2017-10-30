---
title: "Catalog.event_messages | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a31a654f-31e9-4da1-aabf-182b07848e36
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a0db5ace2a95bea93189cb48378b01a4ba599942
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogeventmessages"></a>catalog.event_messages
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Показывает сведения о сообщениях, которые были зарегистрированы в ходе операций.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|Event_message_ID|bigint|Уникальный идентификатор сообщения о событии.|  
|Operation_id|bigint|Тип операции.<br /><br /> Список типов операций см. в разделе [catalog.operations &#40; База данных SSISDB &#41; ](../../integration-services/system-views/catalog-operations-ssisdb-database.md).|  
|Message_time|datetimeoffset(7)|Время создания сообщения.|  
|Message_type|smallint|Тип отображаемого сообщения. Дополнительные сведения о типах сообщений см. в разделе [catalog.operation_messages &#40; База данных SSISDB &#41; ](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md).|  
|Message_source_type|smallint|Источник сообщения.|  
|message|nvarchar(max)|Текст сообщения.|  
|Extended_info_id|bigint|Идентификатор дополнительных сведений, которые относятся к сообщению операции найден в [catalog.extended_operation_info &#40; База данных SSISDB &#41; ](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md) представления.|  
|Package_name|nvarchar(260)|Имя файла пакета.|  
|Event_name|nvarchar(1024)|Событие времени выполнения, связанное с сообщением.|  
|Message_source_name|nvarchar(4000)|Компонент пакета, являющийся источником сообщения.|  
|Message_source_id|Nvarchar(38)|Уникальный идентификатор источника сообщения.|  
|Subcomponent_name|nvarchar(4000)|Компонент потока данных, являющийся источником сообщения.<br /><br /> Если сообщения возвращаются ядром [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], в этом столбце появляется SSIS.Pipeline.|  
|Package_path|nvarchar(max)|Уникальный путь к компоненту внутри пакета.|  
|Execution_path|nvarchar(max)|Полный путь от родительского пакета до точки выполнения компонента.<br /><br /> Этот путь также включает повторения компонента.|  
|threadID|int|Идентификатор потока, который выполняется при регистрации сообщения.|  
|Message_code|int|Код, связанный с этим сообщением.|  
  
## <a name="remarks"></a>Замечания  
 В этом представлении отображаются следующие типы источников сообщений.  
  
|**message_source_type**|Description|  
|-------------------------------|-----------------|  
|10|Начальные API-интерфейсы, такие как T-SQL и хранимые процедуры CLR|  
|20|Внешний процесс, используемый для запуска пакета (ISServerExec.exe)|  
|30|Объекты уровня пакета|  
|40|Задачи потока управления|  
|50|Контейнеры потока управления|  
|60|Задача потока данных|  
  
## <a name="permissions"></a>Permissions  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ по отношению к операции  
  
-   Членство в **ssis_admin** роли базы данных.  
  
-   Членство в **sysadmin** роли сервера.  
  
## <a name="see-also"></a>См. также:  
 [catalog.event_message_context](../../integration-services/system-views/catalog-event-message-context.md)  
  
  

