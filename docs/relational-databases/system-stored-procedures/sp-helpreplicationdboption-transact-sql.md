---
title: "sp_helpreplicationdboption (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- sp_helpreplicationdboption_TSQL
- sp_helpreplicationdboption
helpviewer_keywords:
- sp_helpreplicationdboption
ms.assetid: 143ce689-108b-49d7-9892-fd3a86897f38
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d53bf08bf26d8682093d72e55f290701d0b3c625
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpreplicationdboption-transact-sql"></a>sp_helpreplicationdboption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает, доступны ли для репликации базы данных на издателе. Эта хранимая процедура выполняется на подписчике в любой базе данных. *Не поддерживается для издателей Oracle.*  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpreplicationdboption [ [ @dbname =] 'dbname' ]  
    [ , [ @type = ] 'type' ]  
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@dbname=**] **"***dbname***"**  
 Имя базы данных. *DBName* — **sysname**, значение по умолчанию  **%** . Если  **%** , результирующий набор содержит все базы данных на издателе, в противном случае только в указанной базе данных возвращаются сведения. Данные не возвращаются для тех баз данных, где у пользователя нет соответствующих описанных ниже разрешений.  
  
 [  **@type=**] **"***тип***"**  
 Ограничивает результирующий набор содержит только базы данных, на котором указанный аргумент репликации *тип* включен. *Тип* — **sysname**, и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Публикация**|Разрешена репликация транзакций.|  
|**публикации слиянием**|Разрешена репликация слиянием.|  
|**разрешена репликация** (по умолчанию)|Разрешена репликация транзакций или репликация слиянием.|  
  
 [  **@reserved=** ] *зарезервированные*  
 Указывает, возвращаются ли данные о существующих публикациях и подписках. *зарезервированные* — **бит**, значение по умолчанию 0. Если **1**, результирующий набор включает данные о имеет ли указанная база данных все существующие публикации или подписки.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя базы данных.|  
|**идентификатор**|**int**|Идентификатор базы данных.|  
|**transpublish**|**bit**|Если база данных была включена для публикации моментальных снимков или публикации транзакций; При задании значения **1** означает, что включена публикация транзакций или моментальных снимков.|  
|**mergepublish**|**bit**|Если база данных была включена публикация слиянием; При задании значения **1** означает, что публикация слиянием включен.|  
|**dbowner**|**bit**|Если пользователь является членом **db_owner** предопределенной роли базы данных; значение **1** указывает, что пользователь является членом этой роли.|  
|**dbreadonly**|**bit**|— Если база данных помечена как только для чтения. При задании значения **1** означает, что база данных доступна только для чтения.|  
|**haspublications**|**bit**|Если база данных имеет все существующие публикации; При задании значения **1** означает, что публикации существуют.|  
|**haspullsubscriptions**|**bit**|Если база данных имеет любые существующие подписки по запросу; При задании значения **1** означает, что существуют подписки по запросу.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_helpreplicationdboption** используется в моментальных снимков, транзакций и репликации слиянием.  
  
## <a name="permissions"></a>Permissions  
 Члены **sysadmin** предопределенной роли сервера могут выполнять **sp_helpreplicationdboption** для любой базы данных. Члены **db_owner** предопределенной роли базы данных могут выполнять **sp_helpreplicationdboption** для этой базы данных.  
  
## <a name="see-also"></a>См. также:  
 [sp_replicationdboption &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
