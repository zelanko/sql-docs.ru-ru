---
title: sp_changereplicationserverpasswords (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changereplicationserverpasswords_TSQL
- sp_changereplicationserverpasswords
helpviewer_keywords:
- sp_changereplicationserverpasswords
ms.assetid: 9333da96-3a1c-4adb-9a74-5dac9ce596df
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9feddab12ea972ea4d7764fccfdd91a7f9b89cec
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68762251"
---
# <a name="sp_changereplicationserverpasswords-transact-sql"></a>sp_changereplicationserverpasswords (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Изменяет сохраненные пароли для учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или имени входа, используемого агентами репликации при подключении к серверам в топологии репликации. Обычно требуется менять пароль для каждого отдельного агента, выполняемого на сервере, даже если все они используют одно и то же имя входа или учетную запись. Эта хранимая процедура позволяет сменить пароль для всех экземпляров данного имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или учетной записи Windows, используемой всеми агентами репликации, выполняемыми на сервере. Эта хранимая процедура выполняется на любом сервере в топологии репликации в базе данных master.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changereplicationserverpasswords [ @login_type = ] login_type  
        , [ @login = ] 'login'   
        , [ @password = ] 'password'  
    [ , [ @server = ] 'server' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @login_type = ] login_type`Тип проверки подлинности для предоставленных учетных данных. *LOGIN_TYPE* имеет тип **tinyint**и не имеет значения по умолчанию.  
  
 **1** = встроенная проверка подлинности Windows  
  
 **0** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверка подлинности  
  
`[ @login = ] 'login'`Имя изменяемой учетной записи Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа. *имя для входа* — **nvarchar (257)**, без значения по умолчанию  
  
`[ @password = ] 'password'`Новый пароль, который будет сохранен для указанного *имени входа*. Аргумент *Password* имеет тип **sysname**и не имеет значения по умолчанию.  
  
> [!NOTE]  
>  После изменения пароля репликации необходимо остановить и перезапустить каждый агент, пользующийся этим паролем, прежде чем изменение вступит в силу для этого агента.  
  
`[ @server = ] 'server'`Соединение с сервером, для которого изменяется сохраненный пароль. *Server* имеет тип **sysname**и может принимать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|**распространение**|Все соединения агентов с распространителем.|  
|**издателя**|Все соединения агентов с издателем.|  
|**абонент**|Все соединения агентов с подписчиком.|  
|**%** параметры|Все соединения агентов со всеми серверами в топологии репликации.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_changereplicationserverpasswords** используется со всеми типами репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_changereplicationserverpasswords**.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение параметров безопасности репликации](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
