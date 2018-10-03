---
title: sp_dbmmonitorchangemonitoring (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitorchangemonitoring
- sp_dbmmonitorchangemonitoring_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbmmonitorchangemonitoring
- database mirroring [SQL Server], monitoring
ms.assetid: 17be755b-673d-4cd4-9544-6ecb4220bed3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4c8d9fe6a682a2f9d8847268c0d2a746b03ccf1e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635042"
---
# <a name="spdbmmonitorchangemonitoring-transact-sql"></a>sp_dbmmonitorchangemonitoring (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет значение параметра мониторинга зеркального отображения базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbmmonitorchangemonitoring parameter  
    , value   
```  
  
## <a name="arguments"></a>Аргументы  
 *Параметр*  
 Указывает идентификатор изменяемого параметра. На данный момент доступны только следующие параметры.  
  
 1 = период обновления  
  
 Количество минут между обновлениями таблицы состояния зеркального отображения базы данных. Значение интервала по умолчанию — 1 минута.  
  
 *value*  
 Указывает новое значение изменяемого параметра.  
  
|Параметр|Описание значения|  
|---------------|--------------------------|  
|1|Целое число в диапазоне от 1 до 120, задающее новый период обновления в минутах.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере период обновления устанавливается в 5 минут.  
  
```  
EXEC sp_dbmmonitorchangemonitoring 1, 5 ;  
```  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за зеркальным отображением базы данных (SQL Server)](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql.md)   
 [sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
