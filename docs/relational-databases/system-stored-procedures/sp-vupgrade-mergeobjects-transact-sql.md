---
title: sp_vupgrade_mergeobjects (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_vupgrade_mergeobjects
- sp_vupgrade_mergeobjects_TSQL
helpviewer_keywords:
- sp_vupgrade_mergeobjects
ms.assetid: 73257c2e-cc4c-48e7-9d66-7ef045bdd4f5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b4fb095a96a63e2a6e04e2a0a995d4d478965146
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47596248"
---
# <a name="spvupgrademergeobjects-transact-sql"></a>sp_vupgrade_mergeobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Повторно создает триггеры конкретных статей, хранимые процедуры и представления, с помощью которых отслеживаются и вносятся изменения данных для репликации слиянием. Эту процедуру следует выполнять в следующих случаях.  
  
-   Если объект, необходимый для репликации, случайно был удален.  
  
-   Если применяется обновление, например исправление, для которого требуется изменить один или несколько объектов репликации. После применения обновления процедуру следует выполнить на каждом узле.  
  
 Выполнение этой хранимой процедуры не требует повторной инициализации подписок. Эта процедура не является обязательной при установке пакета обновления или при обновлении до новой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_vupgrade_mergeobjects [ [@login = ] 'login' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @security_mode = ] security_mode ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@login=**] **"***входа***"**  
 Имя входа администратора системы, используемое при создании новых системных объектов в базе данных распространителя. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL. Этот параметр не является обязательным, если *security_mode* присваивается **1**, что означает проверку подлинности Windows.  
  
 [  **@password=**] **"***пароль***"**  
 Пароль администратора системы, используемый при создании новых системных объектов в базе данных распространителя. *пароль* — **sysname**, значение по умолчанию **''** (пустая строка). Этот параметр не является обязательным, если *security_mode* присваивается **1**, что означает проверку подлинности Windows.  
  
 [  **@security_mode=**] **"***security_mode***"**  
 Режим безопасности при входе в систему, используемый при создании новых системных объектов в базе данных распространителя. *security_mode* — **бит** со значением по умолчанию **1**. Если **0**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет использоваться проверка подлинности. Если **1**, будет использоваться проверка подлинности Windows. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_vupgrade_mergeobjects** используется только для репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Обновление реплицируемых баз данных](../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  
