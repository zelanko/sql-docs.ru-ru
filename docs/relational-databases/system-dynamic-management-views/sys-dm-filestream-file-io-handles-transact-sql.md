---
title: sys. dm_filestream_file_io_handles (Transact-SQL) | Документация Майкрософт
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e5be48c81dc5851ee43668ef8ca141409acecd7d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830611"
---
# <a name="sysdm_filestream_file_io_handles-transact-sql"></a>sys.dm_filestream_file_io_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Показывает дескрипторы файлов, известные владельцу пространства имен (NSO). Дескрипторы FILESTREAM, которые клиент получил с помощью **OpenSqlFilestream** , отображаются в этом представлении.  
  
|Столбец|Type|Описание|  
|------------|----------|-----------------|  
|**handle_context_address**|**varbinary(8)**|Показывает адрес внутренней структуры NSO, связанной с маркером клиента. Допускает значение NULL.|  
|**creation_request_id**|**int**|Показывает поле из запроса ввода-вывода REQ_PRE_CREATE, используемого для создания этого дескриптора. Не допускает значение NULL.|  
|**creation_irp_id**|**int**|Показывает поле из запроса ввода-вывода REQ_PRE_CREATE, используемого для создания этого дескриптора. Не допускает значение NULL.|  
|**handle_id**|**int**|Показывает уникальный идентификатор этого дескриптора, назначенный драйвером. Не допускает значение NULL.|  
|**creation_client_thread_id**|**varbinary(8)**|Показывает поле из запроса ввода-вывода REQ_PRE_CREATE, используемого для создания этого дескриптора. Допускает значение NULL.|  
|**creation_client_process_id**|**varbinary(8)**|Показывает поле из запроса ввода-вывода REQ_PRE_CREATE, используемого для создания этого дескриптора. Допускает значение NULL.|  
|**filestream_transaction_id**|**varbinary(128)**|Показывает идентификатор транзакции, связанной с заданным дескриптором. Это значение, возвращаемое функцией **GET_FILESTREAM_TRANSACTION_CONTEXT** . Это поле используется для присоединение к представлению **sys. dm_filestream_file_io_requests** . Допускает значение NULL.|  
|**access_type**|**nvarchar(60)**|Не допускает значение NULL.|  
|**logical_path**|**nvarchar(256)**|Показывает логический путь к файлу, который открыт этим дескриптором. Это тот же путь, который возвращается **. Метод PathName** объекта FileStream типа **varbinary**(**Max**). Допускает значение NULL.|  
|**physical_path**|**nvarchar(256)**|Показывает фактический путь к файлу в системе NTFS. Это тот же путь, который возвращает **. Метод PhysicalPathName** объекта FileStream типа **varbinary**(**Max**). Он включается флагом трассировки 5556. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления FILESTREAM и FileTable &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)  
  
  
