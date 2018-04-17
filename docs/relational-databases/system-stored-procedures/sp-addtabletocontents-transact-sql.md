---
title: sp_addtabletocontents (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addtabletocontents_TSQL
- sp_addtabletocontents
helpviewer_keywords:
- sp_addtabletocontents
ms.assetid: 2ea27001-74f4-463e-bf1b-b6b5a86b9219
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 782c63304d43b0c4d7aa1c484bb8860102b714e8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spaddtabletocontents-transact-sql"></a>sp_addtabletocontents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вставляет ссылки в таблицы отслеживания слияния для любых строк в исходной таблице, которые не включены в таблицы отслеживания. Используйте этот параметр, если при загрузке большого объема данных с помощью **bcp**, которые не вызывают срабатывание триггеров слияния. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addtabletocontents [ @table_name = ] 'table_name'  
    [ , [ @owner_name = ] 'owner_name' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@table_name=**] **"***table_name***"**  
 Имя таблицы. *имя_таблицы* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@owner_name=**] **"***owner_name***"**  
 Имя владельца таблицы. *owner_name* — **sysname**, значение по умолчанию NULL.  
  
 [  **@filter_clause=** ] **"***filter_clause***"**  
 Указывает предложение фильтра, определяющее строки вновь загруженных данных, которые следует добавить в таблицы отслеживания слияния. *filter_clause* — **nvarchar(4000)**, значение по умолчанию NULL. Если *filter_clause* — **null**, все массового добавления загруженные строки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_addtabletocontents** используется только при репликации слиянием.  
  
 Строки в *table_name* под их **rowguidcol** и ссылки добавляются в таблицы отслеживания слияния. **sp_addtabletocontents** можно использовать для массового копирования данных в таблицу, которая опубликована с использованием репликации слиянием. Хранимая процедура инициирует отслеживание строк, которые были скопированы, и обеспечивает их участие в следующей синхронизации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_addtabletocontents**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
