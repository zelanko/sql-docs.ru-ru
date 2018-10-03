---
title: sys.sp_rda_set_query_mode (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_query_mode
- sys.sp_rda_set_query_mode_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_query_mode stored procedure
ms.assetid: 65a0b390-cf87-4db7-972a-1fdf13456c88
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c6b2fd8fd64bd8d7df6429a21c3f27266657964e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740552"
---
# <a name="syssprdasetquerymode-transact-sql"></a>sys.sp_rda_set_query_mode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Указывает, возвращают ли запросы к текущей базе данных с поддержкой Stretch и его таблиц локальных и удаленных данных (по умолчанию) или только локальные данные.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_set_query_mode [ @mode = ] @mode   
    [ , [ @force = ]  @force ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @mode = ] *@mode*  
 Является одним из следующих значений.  
  
-   **ОТКЛЮЧЕННЫЕ** ошибкой все запросы к таблицам с поддержкой Stretch.  
  
-   **LOCAL_ONLY** запросы к таблицам с поддержкой Stretch возвращать только локальные данные.  
  
-   **LOCAL_AND_REMOTE** запросы к таблицам с поддержкой Stretch возвращают локальные и удаленные данные. Это поведение по умолчанию.  
  
 [ @force = ]  *@force*  
 Является необязательным бита, можно установить в значение 1, если вы хотите изменить режим запросов без проверки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или >0 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Требуются права db_owner.  
  
## <a name="remarks"></a>Примечания  
 Расширенные хранимые процедуры также задать режим запроса для базы данных с поддержкой Stretch.  
  
-   **sp_rda_deauthorize_db**  
  
     После того, как **sp_rda_deauthorize_db** , все запросы, адресованные баз данных с поддержкой Stretch и таблицы ошибкой. Это значит режим запроса устанавливается значение отключено. Чтобы выйти из этого режима, выполните одно из следующих действий.  
  
    -   Запустите [sys.sp_rda_reauthorize_db &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) для повторного подключения к удаленной базе данных Azure. Эта операция автоматически восстанавливает режим запроса LOCAL_AND_REMOTE, что является поведением по умолчанию для Stretch Database. То есть запросы возвращают результаты из локальных и удаленных данных.  
  
    -   Запустите [sys.sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) с аргументом LOCAL_ONLY запросов продолжать работать с только локальные данные.  
  
-   **sp_rda_reauthorize_db**  
  
     При запуске [sys.sp_rda_reauthorize_db &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) для повторного подключения к удаленной базе данных Azure, эта операция автоматически восстанавливает режим запроса LOCAL_AND_REMOTE, что является поведением по умолчанию для Stretch Database. То есть запросы возвращают результаты из локальных и удаленных данных.  
  
## <a name="see-also"></a>См. также  
 [sys.sp_rda_deauthorize_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
