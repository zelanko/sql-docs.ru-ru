---
title: Таблицы системы отслеживания измененных данных (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a4372d0b-50ca-4e58-80f6-2ed3cb52a84a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7d6d87ee8b2aa05c3156acb2db9c6604380db887
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68082686"
---
# <a name="change-data-capture-tables-transact-sql"></a>Таблицы системы отслеживания измененных данных (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Система отслеживания измененных данных позволяет отслеживать изменения в таблицах так, что изменения на языках DML и DDL, вносимые в таблицы, постепенно загружались в хранилище данных. Подразделы настоящего раздела описывают системные таблицы, которые хранят сведения, необходимые для операций системы отслеживания измененных данных.  
  
## <a name="in-this-section"></a>В этом разделе  
 [CDC. <capture_instance>_CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)  
 Возвращает одну строку для каждого изменения, сделанного в отслеживаемом столбце в связанной исходной таблице.  
  
 [cdc.captured_columns](../../relational-databases/system-tables/cdc-captured-columns-transact-sql.md)  
 Возвращает по одной строке для каждого столбца, отслеживаемого в экземпляре отслеживания.  
  
 [cdc.change_tables](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
 Возвращает по одной строке для каждой таблицы изменений в базе данных.  
  
 [cdc.ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md)  
 Возвращает одну строку для каждого изменения языка DDL, внесенного в таблицы, поддерживающие систему отслеживания измененных данных.  
  
 [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)  
 Возвращает по одной строке для каждой транзакции, имеющей строки в таблице изменений. Эта таблица используется, чтобы сопоставить значения номера LSN фиксации и время фиксации транзакции.  
  
 [cdc.index_columns](../../relational-databases/system-tables/cdc-index-columns-transact-sql.md)  
 Возвращает по одной строке для каждого столбца индекса, связанного с таблицей изменений.  
  
 [dbo. cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
 Возвращает параметры конфигурации для заданий агента системы отслеживания измененных данных.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры системы отслеживания измененных данных &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)   
 [Функции системы отслеживания измененных данных (Transact-SQL)](../../relational-databases/system-functions/change-data-capture-functions-transact-sql.md)  
  
  
