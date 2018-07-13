---
title: sys.dm_db_rda_migration_status (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_migration_status
- sys.dm_db_rda_migration_status_TSQL
- dm_db_rda_migration_status
- dm_db_rda_migration_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_rda_migration_status dynamic management view
ms.assetid: faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e0ee1d106a9f52dd30518f9ead02847dc879ff2c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422473"
---
# <a name="stretch-database---sysdmdbrdamigrationstatus"></a>Stretch Database - sys.dm_db_rda_migration_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого пакета перенесенных данных из каждой таблицы с включенным Stretch на локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пакеты идентифицируются по их время начала и время окончания.  
  
 **sys.dm_db_rda_migration_status** ограничивается в контексте текущей базы данных. Убедитесь, что вы находитесь в контексте базы данных, поддерживающих функцию растяжения таблиц, для которых вы хотите увидеть состояние миграции.  
  
 В [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], выходные данные **sys.dm_db_rda_migration_status** ограничена 200 строк.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|Идентификатор таблицы, из которой производилось перемещение строк.|  
|**database_id**|**int**|Идентификатор базы данных, из которой производилось перемещение строк.|  
|**migrated_rows**|**bigint**|Число строк, перенесены в этом пакете.|  
|**start_time_utc**|**datetime**|Время в формате UTC, время последнего запуска пакета.|  
|**end_time_utc**|**datetime**|Время в формате UTC, по которому завершения пакета.|  
|**error_number**|**int**|Если происходит сбой пакета, номер ошибки, возникшей; в противном случае — значение null.|  
|**error_severity**|**int**|Если пакет не удается, серьезность ошибки, возникшей; в противном случае — значение null.|  
|**error_state**|**int**|Если пакет не удается, состояние ошибки, возникшей; в противном случае — значение null.<br /><br /> **Error_state** указывает условие или расположение, где произошла ошибка.|  
  
## <a name="see-also"></a>См. также  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
