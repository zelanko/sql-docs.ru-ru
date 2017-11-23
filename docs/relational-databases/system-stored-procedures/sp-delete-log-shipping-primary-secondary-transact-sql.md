---
title: "sp_delete_log_shipping_primary_secondary (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_delete_log_shipping_primary_secondary_TSQL
- sp_delete_log_shipping_primary_secondary
dev_langs: TSQL
helpviewer_keywords: sp_delete_log_shipping_primary_secondary
ms.assetid: d6f71a12-f7b1-4a1c-9639-a533b8287b0c
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0a357b66c3aae034503d302db462fc53b7e2b74
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="spdeletelogshippingprimarysecondary-transact-sql"></a>sp_delete_log_shipping_primary_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет запись базы данных-получателя на сервере-источнике.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_log_shipping_primary_secondary  
    [ @primary_database = ] 'primary_database',   
    [ @secondary_server = ] 'secondary_server',   
    [ @secondary_database = ] 'secondary_database'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@primary_database =** ] **"***primary_database***"**  
 Имя базы данных на сервере-источнике. *primary_database* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@secondary_server =** ] **"***сервер_получатель***"**  
 Имя сервера-получателя. *сервер_получатель* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@secondary_database =** ] **"***secondary_database***"**  
 Имя базы данных-получателя. *secondary_database* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="remarks"></a>Замечания  
 **sp_delete_log_shipping_primary_secondary** должна запускаться из **master** базы данных на сервере-источнике. Эта хранимая процедура удаляет запись из базы данных-получателя **log_shipping_primary_secondaries** на основном сервере.  
  
## <a name="permissions"></a>Permissions  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере хранимая процедура `sp_delete_log_shipping_primary_secondary` используется для удаления базы данных-получателя `LogShipAdventureWorks` с сервера-получателя `FLATIRON`.  
  
```  
EXEC master.dbo.sp_delete_log_shipping_primary_secondary  
@primary_database = N'AdventureWorks'  
,@secondary_server = N'FLATIRON'  
,@secondary_database = N'LogShipAdventureWorks';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Сведения о доставке журналов (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
