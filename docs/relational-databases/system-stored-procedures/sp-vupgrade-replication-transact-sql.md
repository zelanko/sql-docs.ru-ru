---
title: "sp_vupgrade_replication (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- sp_vupgrade_replication_TSQL
- sp_vupgrade_replication
helpviewer_keywords:
- sp_vupgrade_replication
ms.assetid: d2c0ed66-07d1-4adc-82e5-a654376879bc
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d07f50261726675d921f39226cd97f9b163b1f7f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spvupgradereplication-transact-sql"></a>sp_vupgrade_replication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Активируется программой установки при обновлении сервера репликации. Производит необходимое обновление схемы и системных данных для поддержки репликации на текущем уровне продукта. Создает новые системные объекты репликации в системных и пользовательских базах данных. Эта хранимая процедура выполняется на машине, на которой должно производиться обновление репликации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_vupgrade_replication [ [@login=] 'login' ]  
    [ , [ @password= ] 'password' ]  
    [ , [ @ver_old= ] 'old_version' ]  
    [ , [ @force_remove= ] 'force_removal' ]  
    [ , [ @security_mode= ] security_mode ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@login=**] **"***входа***"**  
 Имя входа администратора системы, используемое при создании новых системных объектов в базе данных распространителя. *Имя входа* — **sysname**, значение по умолчанию NULL. Этот параметр не является обязательным, если *security_mode* равно **1**, что означает проверку подлинности Windows.  
  
> [!NOTE]  
>  При обновлении до [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и поздних версий этот аргумент не используется.  
  
 [  **@password=**] **"***пароль***"**  
 Пароль администратора системы, используемый при создании новых системных объектов в базе данных распространителя. *пароль* — **sysname**, значение по умолчанию **''** (пустая строка). Этот параметр не является обязательным, если *security_mode* равно **1**, что означает проверку подлинности Windows.  
  
> [!NOTE]  
>  При обновлении до [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий этот параметр не обрабатывается.  
  
 [  **@ver_old=**] **"***old_version***"**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 Данная хранимая процедура является устаревшей и в следующей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет удалена.  
  
 [  **@force_remove=**] **"***force_removal***"**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@security_mode=**] **"***security_mode***"**  
 Режим безопасности при входе в систему, используемый при создании новых системных объектов в базе данных распространителя. *security_mode* — **бит** со значением по умолчанию **0**. Если **0**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет использоваться проверка подлинности. Если **1**, будет использоваться проверка подлинности Windows.  
  
> [!NOTE]  
>  При обновлении до [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и поздних версий этот аргумент не используется.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_vupgrade_replication** используется при обновлении всех типов репликации.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_vupgrade_replication**.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Проверка реплицированных данных](../../relational-databases/replication/validate-replicated-data.md)  
  
  
