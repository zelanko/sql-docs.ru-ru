---
title: sp_addtabletocontents (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addtabletocontents_TSQL
- sp_addtabletocontents
helpviewer_keywords:
- sp_addtabletocontents
ms.assetid: 2ea27001-74f4-463e-bf1b-b6b5a86b9219
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 991ee7139ae4a323a1d426d1882e4f6b3a4df871
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63049731"
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
`[ @table_name = ] 'table_name'` — Имя таблицы. *TABLE_NAME* — **sysname**, не имеет значения по умолчанию.  
  
`[ @owner_name = ] 'owner_name'` — Это имя владельца таблицы. *owner_name* — **sysname**, значение по умолчанию NULL.  
  
`[ @filter_clause = ] 'filter_clause'` Указывает предложение фильтра, определяющее строки вновь загруженных данных, которые следует добавить в таблицы отслеживания слияния. *filter_clause* — **nvarchar(4000)** , со значением по умолчанию NULL. Если *filter_clause* — **null**, все массового добавления загруженные строки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_addtabletocontents** используется только при репликации слиянием.  
  
 Строки в *table_name* ссылаются их **rowguidcol** и ссылки добавляются в таблицы отслеживания слияния. **sp_addtabletocontents** следует использовать для массового копирования данных в таблицу, которая опубликована с использованием репликации слиянием. Хранимая процедура инициирует отслеживание строк, которые были скопированы, и обеспечивает их участие в следующей синхронизации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_addtabletocontents**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
