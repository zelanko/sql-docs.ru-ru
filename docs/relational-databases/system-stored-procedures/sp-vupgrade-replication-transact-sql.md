---
title: sp_vupgrade_replication (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_vupgrade_replication_TSQL
- sp_vupgrade_replication
helpviewer_keywords:
- sp_vupgrade_replication
ms.assetid: d2c0ed66-07d1-4adc-82e5-a654376879bc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e6ece6875e89f684bf0c98f54319e519a648fd84
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640372"
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
 Имя входа администратора системы, используемое при создании новых системных объектов в базе данных распространителя. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL. Этот параметр не является обязательным, если *security_mode* присваивается **1**, что означает проверку подлинности Windows.  
  
> [!NOTE]  
>  При обновлении до [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и поздних версий этот аргумент не используется.  
  
 [  **@password=**] **"***пароль***"**  
 Пароль администратора системы, используемый при создании новых системных объектов в базе данных распространителя. *пароль* — **sysname**, значение по умолчанию **''** (пустая строка). Этот параметр не является обязательным, если *security_mode* присваивается **1**, что означает проверку подлинности Windows.  
  
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
  
## <a name="remarks"></a>Примечания  
 **sp_vupgrade_replication** используется при обновлении всех типов репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_vupgrade_replication**.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Проверка реплицированных данных](../../relational-databases/replication/validate-replicated-data.md)  
  
  
