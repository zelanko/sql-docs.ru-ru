---
description: sysopentapes (Transact-SQL)
title: sysopentapes удалить нельзя (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5a64ea925775daacdbd44a71a945e86fe0f2c9aa
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89537910"
---
# <a name="sysopentapes-transact-sql"></a>sysopentapes (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Содержит по одной строке для каждого из открытых ленточных устройств. Это представление хранится в базе данных **master** .  
  
> [!IMPORTANT]  
>  Данная системная таблица включена в качестве представления только для целей обратной совместимости. Вместо этого используйте динамическое административное представление [sys. dm_io_backup_tapes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md) .  
  
> [!NOTE]  
>  Невозможно удалить представление **sysopentapes удалить нельзя** .  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**openTape**|**nvarchar (64)**|Физическое имя файла открытого ленточного устройства. Дополнительные сведения об открытии и освобождении ленточных устройств см. в разделе [BACKUP &#40;Transact-sql&#41;](../../t-sql/statements/backup-transact-sql.md) and [RESTORE &#40;transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md).|  
  
## <a name="permissions"></a>Разрешения  
 Пользователю необходимо разрешение VIEW SERVER STATE на сервере.  
  
  
