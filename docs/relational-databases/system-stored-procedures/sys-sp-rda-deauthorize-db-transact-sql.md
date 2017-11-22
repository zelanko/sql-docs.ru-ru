---
title: "sys.sp_rda_deauthorize_db (Transact-SQL) | Документы Microsoft"
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
f1_keywords:
- sys.sp_rda_deauthorize_db
- sys.sp_rda_deauthorize_db_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.sp_rda_deauthorize_db stored procedure
ms.assetid: 2e362e15-2cd5-4856-9f0b-54df56b0866b
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6524ced433a0b4b58de1fd857ce32f02cfb64923
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="syssprdadeauthorizedb-transact-sql"></a>sys.sp_rda_deauthorize_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Удаляет безопасного подключения между локальной базы данных с включенным Stretch и удаленной базе данных Azure. Запустите **sp_rda_deauthorize_db** при удаленной базы данных недоступен или находится в несогласованном состоянии, и вы хотите изменить поведение запросов для таблиц с поддержкой Stretch в базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_rda_deauthorize_db   
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или >0 (неуспешное завершение)  
  
## <a name="permissions"></a>Permissions  
 Требуются права db_owner.  
  
## <a name="remarks"></a>Замечания  
 После запуска **sp_rda_deauthorize_db** , все запросы, адресованные баз данных с поддержкой Stretch и таблицы ошибкой. То есть режим запроса имеет значение DISABLED. Чтобы выйти из этого режима, выполните одно из следующих действий.  
  
-   Запустите [sys.sp_rda_reauthorize_db &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) для повторного подключения к удаленной базе данных Azure. Эта операция автоматически сбрасывает режиме запроса LOCAL_AND_REMOTE, что является поведением по умолчанию для базы данных Stretch. То есть запросы возвращают результаты из локальных и удаленных данных.  
  
-   Запустите [sys.sp_rda_set_query_mode &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) с аргументом LOCAL_ONLY, чтобы разрешить запросы продолжают выполняться только локальные данные.  
  
## <a name="see-also"></a>См. также:  
 [sys.sp_rda_set_query_mode &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md)   
 [sys.sp_rda_reauthorize_db &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
