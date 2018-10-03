---
title: sys.dm_filestream_file_io_handles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cde19779c178b8064e6b20a3ae39bbfb7f5b96f6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47847162"
---
# <a name="sysdmfilestreamfileiohandles-transact-sql"></a>sys.dm_filestream_file_io_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Показывает дескрипторы файлов, известные владельцу пространства имен (NSO). Дескрипторов FileStream, которые клиент получил с помощью **OpenSqlFilestream** отображаются в данном представлении.  
  
|Столбец|Тип|Описание|  
|------------|----------|-----------------|  
|**handle_context_address**|**varbinary(8)**|Показывает адрес внутренней структуры NSO, связанной с дескриптором клиента. Допускает значение NULL.|  
|**creation_request_id**|**int**|Показывает поле из запроса ввода-вывода REQ_PRE_CREATE, используемого для создания этого дескриптора. Не допускает значение NULL.|  
|**creation_irp_id**|**int**|Показывает поле из запроса ввода-вывода REQ_PRE_CREATE, используемого для создания этого дескриптора. Не допускает значение NULL.|  
|**handle_id**|**int**|Показывает уникальный идентификатор этого дескриптора, назначенный драйвером. Не допускает значение NULL.|  
|**creation_client_thread_id**|**varbinary(8)**|Показывает поле из запроса ввода-вывода REQ_PRE_CREATE, используемого для создания этого дескриптора. Допускает значение NULL.|  
|**creation_client_process_id**|**varbinary(8)**|Показывает поле из запроса ввода-вывода REQ_PRE_CREATE, используемого для создания этого дескриптора. Допускает значение NULL.|  
|**filestream_transaction_id**|**varbinary(128)**|Показывает идентификатор транзакции, связанной с заданным дескриптором. Это значение, возвращенное **get_filestream_transaction_context** функции. Это поле используется для присоединения к **sys.dm_filestream_file_io_requests** представления. Допускает значение NULL.|  
|**access_type**|**nvarchar(60)**|Не допускает значение NULL.|  
|**logical_path**|**nvarchar(256)**|Показывает логический путь к файлу, который открыт этим дескриптором. Это путь, возвращаемый **. PathName** метод **varbinary**(**max**) filestream. Допускает значение NULL.|  
|**physical_path**|**nvarchar(256)**|Показывает фактический путь к файлу в системе NTFS. Это путь возвращается методом **. PhysicalPathName** метод **varbinary**(**max**) filestream. Он включается флагом трассировки 5556. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [FileStream и FileTable динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)  
  
  
