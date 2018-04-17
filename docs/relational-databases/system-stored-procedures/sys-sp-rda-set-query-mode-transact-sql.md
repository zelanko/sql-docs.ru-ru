---
title: sys.sp_rda_set_query_mode (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_query_mode
- sys.sp_rda_set_query_mode_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_query_mode stored procedure
ms.assetid: 65a0b390-cf87-4db7-972a-1fdf13456c88
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a803ed67f498a04c56700129869140e3b8c4eda1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="syssprdasetquerymode-transact-sql"></a>sys.sp_rda_set_query_mode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Указывает, возвращают ли запросы к текущей базе данных с включенным Stretch и его таблиц локальные и удаленные данные (по умолчанию) или только локальные данные.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_set_query_mode [ @mode = ] @mode   
    [ , [ @force = ]  @force ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @mode = ] *@mode*  
 Является одним из следующих значений.  
  
-   **ОТКЛЮЧЕННЫЕ** все запросы к таблицам с поддержкой Stretch неудачей.  
  
-   **LOCAL_ONLY** запросы к таблицам с поддержкой Stretch возвращают только локальные данные.  
  
-   **LOCAL_AND_REMOTE** запросы к таблицам с поддержкой Stretch возвращают локальные и удаленные данные. Это поведение по умолчанию.  
  
 [ @force = ]  *@force*  
 Является необязательным бит значением, которое можно установить в значение 1, если вы хотите изменить режим запроса без проверки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или >0 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Требуются права db_owner.  
  
## <a name="remarks"></a>Замечания  
 Расширенные хранимые процедуры также задать режим запроса для базы данных с поддержкой Stretch.  
  
-   **sp_rda_deauthorize_db**  
  
     После запуска **sp_rda_deauthorize_db** , все запросы, адресованные баз данных с поддержкой Stretch и таблицы ошибкой. То есть режим запроса имеет значение DISABLED. Чтобы выйти из этого режима, выполните одно из следующих действий.  
  
    -   Запустите [sys.sp_rda_reauthorize_db &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) для повторного подключения к удаленной базе данных Azure. Эта операция автоматически сбрасывает режиме запроса LOCAL_AND_REMOTE, что является поведением по умолчанию для базы данных Stretch. То есть запросы возвращают результаты из локальных и удаленных данных.  
  
    -   Запустите [sys.sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) с аргументом LOCAL_ONLY, чтобы разрешить запросы продолжают выполняться только локальные данные.  
  
-   **sp_rda_reauthorize_db**  
  
     При запуске [sys.sp_rda_reauthorize_db &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) для повторного подключения к удаленной базе данных Azure, эта операция автоматически восстанавливает режим запроса LOCAL_AND_REMOTE, а это поведение по умолчанию для База данных Stretch. То есть запросы возвращают результаты из локальных и удаленных данных.  
  
## <a name="see-also"></a>См. также  
 [sys.sp_rda_deauthorize_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
