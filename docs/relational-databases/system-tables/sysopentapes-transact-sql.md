---
title: "sysopentapes (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysopentapes
- sysopentapes_TSQL
dev_langs: TSQL
helpviewer_keywords:
- backup media [SQL Server], sysopentapes system table
- sysopentapes system table
ms.assetid: c066ca9b-9cfd-46b1-90a3-5c8dc9e7b6ae
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bb39670ced045b6ae5f14b9225d1b46d35aef792
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysopentapes-transact-sql"></a>sysopentapes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого из открытых ленточных устройств. Это представление хранится в **master** базы данных.  
  
> [!IMPORTANT]  
>  Данная системная таблица включена в качестве представления только для целей обратной совместимости. Вместо этого используйте [sys.dm_io_backup_tapes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md) динамическое административное представление.  
  
> [!NOTE]  
>  Не удалось удалить **sysopentapes** представления.  

  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**openTape**|**nvarchar(64)**|Физическое имя файла открытого ленточного устройства. Дополнительные сведения об открытии и освобождении ленточных устройств см. в разделе [резервного КОПИРОВАНИЯ &#40; Transact-SQL &#41; ](../../t-sql/statements/backup-transact-sql.md) и [восстановления &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-transact-sql.md).|  
  
## <a name="permissions"></a>Permissions  
 Пользователю необходимо разрешение VIEW SERVER STATE на сервере.  
  
  
