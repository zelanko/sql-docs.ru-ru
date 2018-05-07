---
title: sys.dm_filestream_file_io_handles (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_filestream_file_io_handles
- sys.dm_filestream_file_io_handles
- dm_filestream_file_io_handles_TSQL
- sys.dm_filestream_file_io_handles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_filestream_file_io_handle catalog view
ms.assetid: e59632f4-3292-419f-9217-ca375749f1a5
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ac46de024e40f394a9b16c1ac484ab8ff7975cf2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmfilestreamfileiohandles-transact-sql"></a>sys.dm_filestream_file_io_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Показывает дескрипторы файлов, известные владельцу пространства имен (NSO). Дескрипторов FileStream, полученный с помощью клиента **OpenSqlFilestream** отображаются в данном представлении.  
  
|Столбец|Тип|Описание|  
|------------|----------|-----------------|  
|**handle_context_address**|**varbinary(8)**|Показывает адрес внутренней структуры NSO, связанной с дескриптором клиента. Допускает значение NULL.|  
|**creation_request_id**|**int**|Показывает поле из запроса ввода-вывода REQ_PRE_CREATE, используемого для создания этого дескриптора. Не допускает значение NULL.|  
|**creation_irp_id**|**int**|Показывает поле из запроса ввода-вывода REQ_PRE_CREATE, используемого для создания этого дескриптора. Не допускает значение NULL.|  
|**handle_id**|**int**|Показывает уникальный идентификатор этого дескриптора, назначенный драйвером. Не допускает значение NULL.|  
|**creation_client_thread_id**|**varbinary(8)**|Показывает поле из запроса ввода-вывода REQ_PRE_CREATE, используемого для создания этого дескриптора. Допускает значение NULL.|  
|**creation_client_process_id**|**varbinary(8)**|Показывает поле из запроса ввода-вывода REQ_PRE_CREATE, используемого для создания этого дескриптора. Допускает значение NULL.|  
|**filestream_transaction_id**|**varbinary(128)**|Показывает идентификатор транзакции, связанной с заданным дескриптором. Это значение, возвращаемое **get_filestream_transaction_context** функции. Это поле используется для присоединения к **sys.dm_filestream_file_io_requests** представления. Допускает значение NULL.|  
|**access_type**|**nvarchar(60)**|Не допускает значение NULL.|  
|**logical_path**|**nvarchar(256)**|Показывает логический путь к файлу, который открыт этим дескриптором. Это же путь, который возвращается методом **. PathName** метод **varbinary**(**max**) filestream. Допускает значение NULL.|  
|**physical_path**|**nvarchar(256)**|Показывает фактический путь к файлу в системе NTFS. Это путь возвращается методом **. PhysicalPathName** метод **varbinary**(**max**) filestream. Он включается флагом трассировки 5556. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [FileStream и динамические административные представления FileTable &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)  
  
  
