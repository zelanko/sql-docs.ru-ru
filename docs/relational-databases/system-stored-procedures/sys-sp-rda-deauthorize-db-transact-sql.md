---
title: sys. sp_rda_deauthorize_db (Transact-SQL) | Документация Майкрософт
description: Узнайте, как использовать sys. sp_rda_deauthorize_db для удаления прошедших проверку подлинности подключений между локальными базами данных с поддержкой Stretch и удаленными базами данных Azure.
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_deauthorize_db
- sys.sp_rda_deauthorize_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_deauthorize_db stored procedure
ms.assetid: 2e362e15-2cd5-4856-9f0b-54df56b0866b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5c8413bf0a78ea1780d0babfc6fd88abb615d4ea
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538486"
---
# <a name="syssp_rda_deauthorize_db-transact-sql"></a>sys. sp_rda_deauthorize_db (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Удаляет подключение с проверкой подлинности между локальной базой данных с поддержкой Stretch и удаленной базой данных Azure. Запустите **sp_rda_deauthorize_db**  , когда удаленная база данных недоступна или находится в непостоянном состоянии и необходимо изменить поведение запроса для всех таблиц с поддержкой Stretch в базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_rda_deauthorize_db   
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или >0 (сбой)  
  
## <a name="permissions"></a>Разрешения  
 Требуются db_owner разрешения.  
  
## <a name="remarks"></a>Примечания  
 После запуска **sp_rda_deauthorize_db** все запросы к базам данных и таблицам с поддержкой растяжения завершаются ошибкой. То есть режим запроса имеет значение ОТКЛЮЧЕНо. Чтобы выйти из этого режима, выполните одно из следующих действий.  
  
-   Выполните [sys. sp_rda_reauthorize_db &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) , чтобы повторно подключиться к удаленной базе данных Azure. Эта операция автоматически сбрасывает режим запроса на LOCAL_AND_REMOTE, что является поведением по умолчанию для Stretch Database. То есть запросы возвращают результаты как из локальных, так и удаленных данных.  
  
-   Выполните [sys. sp_rda_set_query_mode &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) с аргументом LOCAL_ONLY, чтобы разрешить выполнение запросов только для локальных данных.  
  
## <a name="see-also"></a>См. также  
 [sys. sp_rda_set_query_mode &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md)   
 [sys. sp_rda_reauthorize_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)   
 [База данных Stretch](../../sql-server/stretch-database/stretch-database.md)  
  
  
