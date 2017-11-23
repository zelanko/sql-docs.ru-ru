---
title: "Расширенные хранимые процедуры (Transact-SQL) база данных Stretch | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: Stretch Database, stored procedures
ms.assetid: bda29952-4b8b-4295-ab78-f24dcb0b03c6
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3f71e898f656b1177c8b7ea0630b87babd5a0a82
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stretch-database-extended-stored-procedures-transact-sql"></a>База данных Stretch, расширенные хранимые процедуры (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 В этом разделе описываются расширенные хранимые процедуры, связанные с базой данных Stretch.  
  
## <a name="in-this-section"></a>В этом разделе  
[sys.sp_rda_deauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md) удаляет безопасного подключения между локальной базы данных с включенным Stretch и удаленной базе данных Azure.

[sys.sp_rda_get_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md) возвращает число перенесенных данных, SQL Server сохраняет в промежуточную таблицу, чтобы обеспечить полное восстановление удаленной базы данных Azure, если восстановление не требуется.
  
 [sys.sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) восстанавливает безопасного подключения между локальной базы данных включена для Stretch и удаленной базе данных.
  
 [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md)  
 Согласовывает идентификатор пакета, который хранится в таблице с включенным Stretch SQL Server для наиболее недавно переносимых данных с Идентификатором пакета, хранимые в удаленной таблице Azure. 
 
[sys.sp_rda_reconcile_columns](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-columns-transact-sql.md) согласовывает столбцов удаленной таблицы Azure со столбцами в таблице с включенным Stretch SQL Server.
 
 [sys.sp_rda_reconcile_indexes](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-indexes-transact-sql.md) помещает в очередь задачи схемы для выверки индексов в удаленной таблице.
 
 [sys.sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) указывает, возвращают ли запросы к текущей базе данных с включенным Stretch и его таблиц локальные и удаленные данные (по умолчанию) или только локальные данные.
 
 [sys.sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md) задает число перенесенных данных, SQL Server сохраняет в промежуточную таблицу, чтобы обеспечить полное восстановление удаленной базы данных Azure, если восстановление не требуется.
 
 [sys.sp_rda_test_connection](../../relational-databases/system-stored-procedures/sys-sp-rda-test-connection-transact-sql.md) проверяет соединение с SQL Server с удаленным сервером Azure и сообщает о проблемах, которые могут препятствовать миграции данных.
 
## <a name="see-also"></a>См. также:  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
