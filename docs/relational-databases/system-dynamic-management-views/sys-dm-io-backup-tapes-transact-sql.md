---
title: "sys.dm_io_backup_tapes (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_io_backup_tapes
- dm_io_backup_tapes_TSQL
- sys.dm_io_backup_tapes_TSQL
- dm_io_backup_tapes
dev_langs: TSQL
helpviewer_keywords: sys.dm_io_backup_tapes dynamic management view
ms.assetid: 2e27489e-cf69-4a89-9036-77723ac3de66
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0d2a6365411d66238512fddf23e7f71848acf5de
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmiobackuptapes-transact-sql"></a>sys.dm_io_backup_tapes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает список ленточных устройств и сведения о состоянии запросов на подключение для резервных копий.   
 
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**physical_device_name**|**nvarchar(520)**|Имя физического устройства, на которое может выполняться резервное копирование. Не допускает значение NULL.|  
|**logical_device_name**|**nvarchar(256)**|Указанное пользователем имя для диска (из **sys.backup_devices**). NULL, если пользовательское имя не задано. Допускает значение NULL.|  
|**status**|**int**|Состояние ленточного накопителя:<br /><br /> 1 = открыто, доступно для использования;<br /><br /> 2 = ожидание подключения;<br /><br /> 3 = используется;<br /><br /> 4 = загружается.<br /><br /> **Примечание:** во время загрузки ленты (**состояние = 4**), Метка носителя еще недоступна. Столбцы, которые содержат значения меток носителей, такие как **media_sequence_number**, показывают ожидаемые значения, которые могут отличаться от фактических значений на ленте. После считывания метки **состояние** примет **3** («используется»), и столбцы меток носителей принимают фактические лента, которая загружается.<br /><br /> Не допускает значение NULL.|  
|**status_desc**|**nvarchar(520)**|Описание состояния ленточного накопителя:<br /><br /> AVAILABLE;<br /><br /> MOUNT PENDING;<br /><br /> IN USE;<br /><br /> LOADING MEDIA.<br /><br /> Не допускает значение NULL.|  
|**mount_request_time**|**datetime**|Время запроса на подключение. Значение NULL, если не ожидается монтирование (**состояние! = 2**). Допускает значение NULL.|  
|**mount_expiration_time**|**datetime**|Время действия запроса на подключение (тайм-аут). Значение NULL, если не ожидается монтирование (**состояние! = 2**). Допускает значение NULL.|  
|**database_name**|**nvarchar(256)**|База данных, резервная копия которой будет размещена на этом устройстве. Допускает значение NULL.|  
|**Идентификатор SPID**|**int**|Идентификатор сеанса. Определяет пользователя ленты. Допускает значение NULL.|  
|**команда**|**int**|Команда, с помощью которой выполняется резервное копирование. Допускает значение NULL.|  
|**command_desc**|**nvarchar(120)**|Описание команды. Допускает значение NULL.|  
|**media_family_id**|**int**|Индекс семейства носителей (1... *n* ),  *n*  число семейств носителей в наборе носителей. Допускает значение NULL.|  
|**media_set_name**|**nvarchar(256)**|Имя набора носителей, если таковое задано с помощью параметра MEDIANAME при создании набора носителей. Допускает значение NULL.|  
|**media_set_guid**|**uniqueidentifier**|Уникальный идентификатор набора носителей. Допускает значение NULL.|  
|**media_sequence_number**|**int**|Порядковый номер тома в семействе носителей (1... *n*). Допускает значение NULL.|  
|**tape_operation**|**int**|Операция, выполняемая в данный момент на магнитной ленте:<br /><br /> 1 = чтение<br /><br /> 2 = форматирование;<br /><br /> 3 = инициализация;<br /><br /> 4 = добавление.<br /><br /> Допускает значение NULL.|  
|**tape_operation_desc**|**nvarchar(120)**|Операции, выполняемые с ленточными накопителями:<br /><br /> READ<br /><br /> FORMAT<br /><br /> INIT<br /><br /> APPEND.<br /><br /> Допускает значение NULL.|  
|**mount_request_type**|**int**|Тип запроса на подключение:<br /><br /> 1 = конкретная лента. Лента, определяемая **media_\***  полей не требуется.<br /><br /> 2 = следующее семейство носителей. Требуется следующее семейство носителей для восстановления. Используется при восстановлении данных с использованием меньшего, чем количества устройств, доступных семейств носителей.<br /><br /> 3 = дополнительная лента. Семейство носителей расширяется и запрашивается дополнительная лента.<br /><br /> Допускает значение NULL.|  
|**mount_request_type_desc**|**nvarchar(120)**|Тип запроса на подключение:<br /><br /> конкретная лента;<br /><br /> следующее семейство носителей;<br /><br /> том для продолжения.<br /><br /> Допускает значение NULL.|  
  
## <a name="permissions"></a>Permissions  
 Пользователь должен иметь разрешение VIEW SERVER STATE на этом сервере.  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Я O связанные динамические административные представления и функции &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  

