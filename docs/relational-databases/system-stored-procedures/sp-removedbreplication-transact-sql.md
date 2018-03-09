---
title: "Хранимая процедура sp_removedbreplication (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_removedbreplication
- sp_removedbreplication_TSQL
helpviewer_keywords:
- sp_removedbreplication
ms.assetid: cb98d571-d1eb-467b-91f7-a6e091009672
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e2c44063c4ab9019f191136ead3c890f50806885
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spremovedbreplication-transact-sql"></a>sp_removedbreplication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Эта хранимая процедура удаляет все объекты репликации в базе данных публикации в экземпляре издателя SQL Server или в базе данных подписки в экземпляре подписчика SQL Server. Выполняйте в соответствующей базе данных или укажите базу данных, где необходимо удалить объекты репликации, при выполнении в контексте другой базы данных в том же экземпляре. Эта процедура не удаляет объекты из других баз данных, например базы данных распространителя.  
  
> [!NOTE]  
>  Эта процедура должна использоваться только в случае, если другие методы удаления объектов репликации потерпели неудачу.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_removedbreplication [ [ @dbname = ] 'dbname' ]  
    [ , [ @type = ] type ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@dbname=**] **"***dbname***"**  
 Имя базы данных. Аргумент*dbname* имеет тип **sysname**и значение по умолчанию NULL. Если значение NULL, используется текущая база данных.  
  
 [  **@type**  =] *типа*  
 Тип репликации, для которой удаляются объекты базы данных. *Тип* — **nvarchar(5)** и может принимать одно из следующих значений.  
  
|||  
|-|-|  
|**TRAN**|Удаляет публикуемые объекты репликации транзакций.|  
|**Слияние**|Удаляет публикуемые объекты репликации слиянием.|  
|**оба** (по умолчанию)|Удаляет все публикуемые объекты репликации.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **Хранимая процедура sp_removedbreplication** используется во всех типах репликации.  
  
 **Хранимая процедура sp_removedbreplication** полезна при восстановлении реплицированной базы данных, не имеющей объектов репликации требуется восстановить.  
  
 **Хранимая процедура sp_removedbreplication** не может использоваться в базе данных, который помечен как доступный только для чтения.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_removedbreplication](../../relational-databases/replication/codesnippet/tsql/sp-removedbreplication-t_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_removedbreplication**.  
  
## <a name="example"></a>Пример  
  
```  
-- Remove replication objects from the subscription database on MYSUB.  
DECLARE @subscriptionDB AS sysname  
SET @subscriptionDB = N'AdventureWorksReplica'  
  
-- Remove replication objects from a subscription database (if necessary).  
USE master  
EXEC sp_removedbreplication @subscriptionDB  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Disable Publishing and Distribution](../../relational-databases/replication/disable-publishing-and-distribution.md)  (Отключение публикации и распространения)  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
