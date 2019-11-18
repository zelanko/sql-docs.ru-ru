---
title: Расширенные хранимые процедуры (Transact-SQL)
titleSuffix: SQL Server Stretch Database
ms.custom: seo-dt-2019
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Stretch Database, stored procedures
ms.assetid: bda29952-4b8b-4295-ab78-f24dcb0b03c6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d82b6cb9049bf5a41cfb987a55bb6d5a7147c9bd
ms.sourcegitcommit: add39e028e919df7d801e8b6bb4f8ac877e60e17
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2019
ms.locfileid: "74119270"
---
# <a name="stretch-database-extended-stored-procedures-transact-sql"></a>Stretch Database расширенные хранимые процедуры (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 В этом разделе описаны расширенные хранимые процедуры, связанные с Stretch Database.  
  
## <a name="in-this-section"></a>в этом разделе  
[sys. sp_rda_deauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md) Удаляет подключение с проверкой подлинности между локальной базой данных с поддержкой Stretch и удаленной базой данных Azure.

[sys. sp_rda_get_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md) Возвращает количество часов перенесенных данных, которые SQL Server сохранены в промежуточной таблице, чтобы обеспечить полное восстановление удаленной базы данных Azure, если восстановление необходимо.
  
 [sys. sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) Восстанавливает подключение с проверкой подлинности между локальной базой данных, для которой включено растяжение, и удаленной базой данных.
  
 [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md)  
 Согласовывает идентификатор пакета, хранящийся в таблице SQL Server с поддержкой растяжения, для последних перенесенных данных с ИДЕНТИФИКАТОРом пакета, хранящимся в удаленной таблице Azure. 
 
[sys. sp_rda_reconcile_columns](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-columns-transact-sql.md) Согласовывает столбцы в удаленной таблице Azure со столбцами в таблице SQL Server с поддержкой растяжения.
 
 [sys. sp_rda_reconcile_indexes](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-indexes-transact-sql.md) Ставит в очередь задачу схемы для согласования индексов в удаленной таблице.
 
 [sys. sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) Указывает, будут ли запросы к текущей базе данных с поддержкой растяжения и ее таблицам возвращать как локальные, так и удаленные данные (по умолчанию) или только локальные данные.
 
 [sys. sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md) Задает количество часов перенесенных данных, которые SQL Server хранить в промежуточной таблице, чтобы обеспечить полное восстановление удаленной базы данных Azure, если восстановление необходимо.
 
 [sys. sp_rda_test_connection](../../relational-databases/system-stored-procedures/sys-sp-rda-test-connection-transact-sql.md) Проверяет подключение SQL Server к удаленному серверу Azure и сообщает о проблемах, которые могут препятствовать миграции данных.
 
## <a name="see-also"></a>См. также статью  
 [база данных Stretch;](../../sql-server/stretch-database/stretch-database.md)  
  
  
