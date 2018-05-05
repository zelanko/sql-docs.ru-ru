---
title: Резервное копирование и восстановление таблицы (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system tables [SQL Server], backup tables
- backup system tables [SQL Server]
- system tables [SQL Server], restore tables
- restore system tables [SQL Server]
ms.assetid: aa615add-54e6-40f5-8b55-3728b26884ee
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: de2fb96afe4fb24cc7fe6455c880027d61d43ddb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="backup-and-restore-tables-transact-sql"></a>Таблицы резервного копирования и восстановления (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Подразделы данного раздела описывают системные таблицы, которые хранят сведения, необходимые для операций резервного копирования и восстановления базы данных.  
  
## <a name="in-this-section"></a>В этом разделе  
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
  
  
