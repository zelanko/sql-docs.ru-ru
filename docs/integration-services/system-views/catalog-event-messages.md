---
title: catalog.event_messages | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: a31a654f-31e9-4da1-aabf-182b07848e36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ac1c56583d59c44d77a3fe6e35454f0527d94c30
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47808782"
---
# <a name="catalogeventmessages"></a>catalog.event_messages
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Показывает сведения о сообщениях, которые были зарегистрированы в ходе операций.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|Event_message_ID|BIGINT|Уникальный идентификатор сообщения о событии.|  
|Operation_id|BIGINT|Тип операции.<br /><br /> Список типов операций см. в разделе [catalog.operations (база данных SSISDB)](../../integration-services/system-views/catalog-operations-ssisdb-database.md).|  
|Message_time|datetimeoffset(7)|Время создания сообщения.|  
|Message_type|SMALLINT|Тип отображаемого сообщения. Дополнительные сведения о типах сообщений см. в разделе [catalog.operation_messages &#40;база данных SSISDB&#41;](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md).|  
|Message_source_type|SMALLINT|Источник сообщения.|  
|message|nvarchar(max)|Текст сообщения.|  
|Extended_info_id|BIGINT|Идентификатор дополнительных сведений, которые относятся к сообщению об операции и находятся в представлении [catalog.extended_operation_info &#40;база данных SSISDB&#41;](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md).|  
|Package_name|nvarchar(260)|Имя файла пакета.|  
|Event_name|nvarchar(1024)|Событие времени выполнения, связанное с сообщением.|  
|Message_source_name|nvarchar(4000)|Компонент пакета, являющийся источником сообщения.|  
|Message_source_id|nvarchar(38)|Уникальный идентификатор источника сообщения.|  
|Subcomponent_name|nvarchar(4000)|Компонент потока данных, являющийся источником сообщения.<br /><br /> Если сообщения возвращаются ядром [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], в этом столбце появляется SSIS.Pipeline.|  
|Package_path|nvarchar(max)|Уникальный путь к компоненту внутри пакета.|  
|Execution_path|nvarchar(max)|Полный путь от родительского пакета до точки выполнения компонента.<br /><br /> Этот путь также включает повторения компонента.|  
|threadID|ssNoversion|Идентификатор потока, который выполняется при регистрации сообщения.|  
|Message_code|ssNoversion|Код, связанный с этим сообщением.|  
  
## <a name="remarks"></a>Remarks  
 В этом представлении отображаются следующие типы источников сообщений.  
  
|**message_source_type**|Описание|  
|-------------------------------|-----------------|  
|10|Начальные API-интерфейсы, такие как T-SQL и хранимые процедуры CLR|  
|20|Внешний процесс, используемый для запуска пакета (ISServerExec.exe)|  
|30|Объекты уровня пакета|  
|40|Задачи потока управления|  
|50|Контейнеры потока управления|  
|60|Задача потока данных|  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ по отношению к операции  
  
-   Членство в роли базы данных **ssis_admin**.  
  
-   Членство в роли сервера **sysadmin**.  
  
## <a name="see-also"></a>См. также:  
 [catalog.event_message_context](../../integration-services/system-views/catalog-event-message-context.md)  
  
  
