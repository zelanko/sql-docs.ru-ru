---
title: Резервное копирование и восстановление таблицы (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system tables [SQL Server], backup tables
- backup system tables [SQL Server]
- system tables [SQL Server], restore tables
- restore system tables [SQL Server]
ms.assetid: aa615add-54e6-40f5-8b55-3728b26884ee
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 021077a7e127f9c93ee752dea7f87aa12e792d02
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62471387"
---
# <a name="backup-and-restore-tables-transact-sql"></a>Таблицы резервного копирования и восстановления (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Подразделы данного раздела описывают системные таблицы, которые хранят сведения, необходимые для операций резервного копирования и восстановления базы данных.  
  
## <a name="in-this-section"></a>в этом разделе  
 [backupfile;](../../relational-databases/system-tables/backupfile-transact-sql.md)  
 Содержит по одной строке для всех данных или файла журнала базы данных.  
  
 [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
 Содержит по одной строке для каждой файловой группы во время резервного копирования.  
  
 [backupmediafamily;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
 Содержит по одной строке для каждого семейства носителей.  
  
 [backupmediaset;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
 Содержит по одной строке для каждого резервного набора носителей.  
  
 [backupset;](../../relational-databases/system-tables/backupset-transact-sql.md)  
 Содержит по одной строке для каждого резервного набора данных.  
  
 [logmarkhistory](../../relational-databases/system-tables/logmarkhistory-transact-sql.md)  
 Содержит одну строку для каждой зафиксированной помеченной транзакции.  
  
 [restorefile;](../../relational-databases/system-tables/restorefile-transact-sql.md)  
 Содержит по одной строке для каждого восстановленного файла. Включены и файлы, восстановленные неявно по имени файловой группы.  
  
 [restorefilegroup;](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)  
 Содержит по одной строке для каждой восстановленной файловой группы.  
  
 [restorehistory.](../../relational-databases/system-tables/restorehistory-transact-sql.md)  
 Содержит по одной строке для каждой операции восстановления.  
  
 [suspect_pages](../../relational-databases/system-tables/suspect-pages-transact-sql.md)  
 Содержит одну строку на таблицу, возвратившую ошибку с кодом 824 (с ограничением в 1000 строк).  
  
 [sysopentapes](../../relational-databases/system-tables/sysopentapes-transact-sql.md)  
 Содержит по одной строке для каждого из открытых ленточных устройств.  
  
  
