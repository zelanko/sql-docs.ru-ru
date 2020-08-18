---
description: sys.dm_server_memory_dumps (Transact-SQL)
title: sys. dm_server_memory_dumps (Transact-SQL) | Документация Майкрософт
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 636beea5b820aef3d37b8ac27f6e75c66bc6da3c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88397710"
---
# <a name="sysdm_server_memory_dumps-transact-sql"></a>sys.dm_server_memory_dumps (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает одну строку для каждого файла дампа памяти, созданного [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. При помощи этого динамического административного представления можно устранять потенциальные неполадки.  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**filename**|**nvarchar(256)**|Полный путь и имя файла дампа памяти. Не может иметь значение null.|  
|**creation_time**|**datetimeoffset(7)**|Дата и время создания файла. Не может иметь значение null.|  
|**size_in_bytes**|**bigint**|Размер файла (в байтах). Допускает значение NULL.|  
  
## <a name="general-remarks"></a>Общие замечания  
 Дамп может представлять собой минидамп, дамп всех потоков или полный дамп памяти. Файлы дампа имеют расширение .mdmp.  
  
## <a name="security"></a>Безопасность  
 Файлы дампа могут содержать конфиденциальные сведения. Чтобы защитить конфиденциальные сведения, можно ограничить доступ к этим файлам с помощью списка управления доступом (ACL) или скопировать их в папку, доступ к которой ограничен. Например, перед отправкой отладочных файлов в службу технической поддержки Майкрософт рекомендуется удалить из них все конфиденциальные сведения.  
  
### <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW SERVER STATE.  
  
  
