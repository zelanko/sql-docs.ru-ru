---
title: sys.database_automatic_tuning_options (Transact-SQL) | Документы Microsoft
description: Узнайте, как просмотреть параметры автоматической настройки в базе данных SQL
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- database_automatic_tuning_options_tsql
- database_automatic_tuning_options
- sys.database_automatic_tuning_options_tsql
- sys.database_automatic_tuning_options
dev_langs:
- TSQL
helpviewer_keywords:
- database_automatic_tuning_options catalog view
- sys.database_automatic_tuning_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
caps.latest.revision: 24
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: 6b1ddbb9fd87c91182b3e43d9ac8e89465eb77f7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdatabaseautomatictuningoptions-transact-sql"></a>sys.Database\_автоматического\_tuning_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Возвращает параметры автоматической настройки для этой базы данных.  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|Имя параметра автоматической настройки. Ссылаться на [ALTER базы данных ЗАДАЙТЕ AUTOMATIC_TUNING &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) для доступных параметров.|  
|**desired_state**|**smallint**|Указывает нужный режим для автоматической настройки, явно установленного параметра пользователем.<br />0 = выключен.<br />1 = включен;|  
|**desired_state_desc**|**nvarchar(60)**|Текстовое описание нужный режим автоматической настройки параметра.<br />OFF<br />ON|  
|**actual_state**|**smallint**|Указывает режим работы параметр автоматической настройки.<br />0 = выключен.<br />1 = включен;|  
|**actual_state_desc**|**nvarchar(60)**|Текстовое описание фактический режим автоматической настройки параметра.<br />OFF<br />ON|  
|**Причина**|**smallint**|Указывает, почему фактического от желаемого состояния, отличаются.<br />2 = ОТКЛЮЧЕНО<br />11 = QUERY_STORE_OFF<br />12 = QUERY_STORE_READ_ONLY<br />13 = NOT_SUPPORTED|   
|**reason_desc**|**nvarchar(60)**|Текстовое описание причины, почему фактического от желаемого состояния, отличаются.<br />ОТКЛЮЧИТЬ = отключен системой<br />QUERY_STORE_OFF = хранилище запросов отключено<br />QUERY_STORE_READ_ONLY = хранилище запросов находится в режиме только для чтения<br />NOT_SUPPORTED = доступно только в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition| 
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение `VIEW DATABASE STATE`.  
  
## <a name="see-also"></a>См. также  
 [Автоматической настройки](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [ALTER базы данных SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.dm_db_tuning_recommendations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 
