---
title: sys.dm_server_memory_dumps (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_server_memory_dumps_TSQL
- dm_server_memory_dumps_TSQL
- dm_server_memory_dumps
- sys.dm_server_memory_dumps
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_memory_dumps dynamic management view
ms.assetid: 41782719-f54d-4e11-941a-c050c7576e23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7c385bfc4fd977efd695020dedf9669dff6eebf0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47714352"
---
# <a name="sysdmservermemorydumps-transact-sql"></a>sys.dm_server_memory_dumps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает одну строку для каждого файла дампа памяти, созданного [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. При помощи этого динамического административного представления можно устранять потенциальные неполадки.  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Имя файла**|**nvarchar(256)**|Полный путь и имя файла дампа памяти. Не может иметь значение null.|  
|**creation_time**|**datetimeoffset(7)**|Дата и время создания файла. Не может иметь значение null.|  
|**size_in_bytes**|**bigint**|Размер файла (в байтах). Допускает значение NULL.|  
  
## <a name="general-remarks"></a>Общие замечания  
 Дамп может представлять собой минидамп, дамп всех потоков или полный дамп памяти. Файлы дампа имеют расширение .mdmp.  
  
## <a name="security"></a>безопасность  
 Файлы дампа могут содержать конфиденциальные сведения. Чтобы защитить конфиденциальные сведения, можно ограничить доступ к этим файлам с помощью списка управления доступом (ACL) или скопировать их в папку, доступ к которой ограничен. Например, перед отправкой отладочных файлов в службу технической поддержки Майкрософт рекомендуется удалить из них все конфиденциальные сведения.  
  
### <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW SERVER STATE.  
  
  
