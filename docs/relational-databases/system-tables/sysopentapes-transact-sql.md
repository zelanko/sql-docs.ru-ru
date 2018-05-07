---
title: sysopentapes (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysopentapes
- sysopentapes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup media [SQL Server], sysopentapes system table
- sysopentapes system table
ms.assetid: c066ca9b-9cfd-46b1-90a3-5c8dc9e7b6ae
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c6f368356df76c68594443ac5a981ebf8f20bec2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sysopentapes-transact-sql"></a>sysopentapes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого из открытых ленточных устройств. Это представление хранится в **master** базы данных.  
  
> [!IMPORTANT]  
>  Данная системная таблица включена в качестве представления только для целей обратной совместимости. Вместо этого используйте [sys.dm_io_backup_tapes &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md) динамическое административное представление.  
  
> [!NOTE]  
>  Не удалось удалить **sysopentapes** представления.  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**openTape**|**nvarchar(64)**|Физическое имя файла открытого ленточного устройства. Дополнительные сведения об открытии и освобождении ленточных устройств см. в разделе [резервного КОПИРОВАНИЯ &#40;Transact-SQL&#41; ](../../t-sql/statements/backup-transact-sql.md) и [ВОССТАНОВИТЬ &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md).|  
  
## <a name="permissions"></a>Разрешения  
 Пользователю необходимо разрешение VIEW SERVER STATE на сервере.  
  
  
