---
title: sys. sp_rda_set_query_mode (Transact-SQL) | Документация Майкрософт
description: Используйте представление sys. sp_rda_set_query_mode, чтобы указать, должны ли запросы к текущей базе данных с поддержкой растяжения и ее таблицам возвращать локальные и удаленные данные или только локальные данные.
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b2fbef46606f182e2c9833d2ce421c61fc421105
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243338"
---
# <a name="syssp_rda_set_query_mode-transact-sql"></a>sys. sp_rda_set_query_mode (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Указывает, будут ли запросы к текущей базе данных с поддержкой растяжения и ее таблицам возвращать как локальные, так и удаленные данные (по умолчанию) или только локальные данные.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_set_query_mode [ @mode = ] @mode   
    [ , [ @force = ]  @force ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @mode =] * \@ режим*  
 Может иметь одно из следующих значений.  
  
-   **Отключено** Все запросы к таблицам с поддержкой растяжения завершаются ошибкой.  
  
-   **LOCAL_ONLY** Запросы к таблицам с поддержкой Stretch возвращают только локальные данные.  
  
-   **LOCAL_AND_REMOTE** Запросы к таблицам с поддержкой Stretch возвращают как локальные, так и удаленные данные. Это поведение по умолчанию.  
  
 [ @force =] * \@ Force*  
 Необязательное битовое значение, которое можно установить в 1, если требуется изменить режим запроса без проверки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или >0 (сбой)  
  
## <a name="permissions"></a>Разрешения  
 Требуются db_owner разрешения.  
  
## <a name="remarks"></a>Remarks  
 Следующие расширенные хранимые процедуры также устанавливают режим запроса для базы данных с поддержкой Stretch.  
  
-   **sp_rda_deauthorize_db**  
  
     После запуска **sp_rda_deauthorize_db** все запросы к базам данных и таблицам с поддержкой растяжения завершаются ошибкой. То есть режим запроса имеет значение ОТКЛЮЧЕНо. Чтобы выйти из этого режима, выполните одно из следующих действий.  
  
    -   Выполните [sys. sp_rda_reauthorize_db &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) , чтобы повторно подключиться к удаленной базе данных Azure. Эта операция автоматически сбрасывает режим запроса на LOCAL_AND_REMOTE, что является поведением по умолчанию для Stretch Database. То есть запросы возвращают результаты как из локальных, так и удаленных данных.  
  
    -   Выполните [sys. sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) с аргументом LOCAL_ONLY, чтобы разрешить выполнение запросов только для локальных данных.  
  
-   **sp_rda_reauthorize_db**  
  
     При выполнении [sys. sp_rda_reauthorize_db &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) для повторного подключения к удаленной базе данных Azure эта операция автоматически сбрасывает режим запроса на LOCAL_AND_REMOTE, что является поведением по умолчанию для Stretch Database. То есть запросы возвращают результаты как из локальных, так и удаленных данных.  
  
## <a name="see-also"></a>См. также:  
 [sys. sp_rda_deauthorize_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [База данных Stretch](../../sql-server/stretch-database/stretch-database.md)  
  
  
