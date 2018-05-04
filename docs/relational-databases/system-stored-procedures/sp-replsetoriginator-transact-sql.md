---
title: sp_replsetoriginator (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- sp_replsetoriginator
- sp_replsetoriginator_TSQL
helpviewer_keywords:
- sp_replsetoriginator
ms.assetid: 030e5226-0585-439f-b8cd-36f48367d86d
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 630f7cf858458fe657535d1d8621e7905a546fc0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spreplsetoriginator-transact-sql"></a>sp_replsetoriginator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Используется для запуска механизма распознавания замыкания на себя и управления в двунаправленной репликации транзакций. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replsetoriginator [ @server_name= ] 'server_name'   
    , [ @database_name= ] 'database_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@server_name=**] **"***имя_сервера***"**  
 Имя сервера, на котором применяется транзакция. *originating_server* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@database_name=**] **"***имя_базы_данных***"**  
 Имя базы данных, в которой применяется транзакция. *originating_db* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_replsetoriginator** выполняется агентом распространителя для записи источника транзакций, применяемых при репликации. Данные сведения используются для запуска механизма распознавания замыкания на себя для двунаправленных транзакционных подписок, которые имеют набор свойств обратной связи.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера на издателе, члены **db_owner** предопределенной роли базы данных в базе данных публикации или пользователи в списке доступа к публикации (PAL) могут выполнять процедуру **sp_replsetoriginator**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
