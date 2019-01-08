---
title: sp_helpreplicationdboption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplicationdboption_TSQL
- sp_helpreplicationdboption
helpviewer_keywords:
- sp_helpreplicationdboption
ms.assetid: 143ce689-108b-49d7-9892-fd3a86897f38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 29fcbe7f5e7b2b7e72c88390df9d5fe20c0f7352
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52812036"
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
 Имя базы данных. *DBName* — **sysname**, значение по умолчанию **%**. Если **%**, то результирующий набор содержит все базы данных на издателе, в противном случае данные только относительно указанной базы данных возвращается. Данные не возвращаются для тех баз данных, где у пользователя нет соответствующих описанных ниже разрешений.  
  
 [  **@type=**] **"***тип***"**  
 Ограничивает результирующий набор должен содержать только базы данных, на котором указанный аргумент репликации *тип* включен. *Тип* — **sysname**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Публикация**|Разрешена репликация транзакций.|  
|**публикации слиянием**|Разрешена репликация слиянием.|  
|**разрешена репликация** (по умолчанию)|Разрешена репликация транзакций или репликация слиянием.|  
  
 [  **@reserved=** ] *зарезервированные*  
 Указывает, возвращаются ли данные о существующих публикациях и подписках. *зарезервированные* — **бит**, со значением по умолчанию 0. Если **1**, результирующий набор включает сведения о базе данных, указанной, имеет ли все существующие публикации или подписки.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя базы данных.|  
|**идентификатор**|**int**|Идентификатор базы данных.|  
|**transpublish**|**bit**|Если база данных была включена для моментальных снимков или публикации транзакций; где значение **1** означает, что включена публикация транзакций или моментальных снимков.|  
|**mergepublish**|**bit**|Если база данных была включена публикация слиянием; где значение **1** включен означает, что публикация слиянием.|  
|**dbowner**|**bit**|Если пользователь является членом **db_owner** предопределенной роли базы данных; где значение **1** указывает, что пользователь является членом этой роли.|  
|**dbreadonly**|**bit**|— Если база данных помечена как доступное только для чтения; где значение **1** означает, что базы данных только для чтения.|  
|**haspublications**|**bit**|Если база данных имеет все существующие публикации; где значение **1** означает, что публикации существуют.|  
|**haspullsubscriptions**|**bit**|Если база данных имеет все существующие подписки по запросу; где значение **1** означает, что существуют подписки по запросу.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpreplicationdboption** используется в моментальных снимков, транзакций и репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Членами **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_helpreplicationdboption** для любой базы данных. Членами **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_helpreplicationdboption** для этой базы данных.  
  
## <a name="see-also"></a>См. также  
 [sp_replicationdboption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
