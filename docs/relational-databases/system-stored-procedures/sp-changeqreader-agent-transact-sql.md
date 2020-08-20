---
description: sp_changeqreader_agent (Transact-SQL)
title: sp_changeqreader_agent (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changeqreader_agent_TSQL
- sp_changeqreader_agent
helpviewer_keywords:
- sp_changeqreader_agent
ms.assetid: d3fe79c5-31ef-4565-bf38-b476b5fb16f7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 99dcccc85577d854996b37743ee8f8cdd32bbebe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481446"
---
# <a name="sp_changeqreader_agent-transact-sql"></a>sp_changeqreader_agent (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Изменяет свойства безопасности агента чтения очереди. Эта хранимая процедура выполняется на распространителе в базе данных распространителя или на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changeqreader_agent [ [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @frompublisher = ] frompublisher   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_login = ] 'job_login'` Имя входа для [!INCLUDE[msCoName](../../includes/msconame-md.md)] учетной записи Windows, под которой запускается агент. *job_login* имеет тип **nvarchar (257)** и значение по умолчанию NULL.  
  
`[ @job_password = ] 'job_password'` Пароль для учетной записи Windows, под которой запускается агент. Аргумент *job_password* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @frompublisher = ] frompublisher` Значение, если процедура выполняется на издателе. *фромпублишер* имеет бит и значение по умолчанию **0**. Значение **1** означает, что процедура выполняется из издателя в базе данных публикации.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_changeqreader_agent** используется в репликации транзакций.  
  
 **sp_changeqreader_agent** используется для изменения учетной записи Windows, с которой запускается агент чтения очереди. Можно изменить пароль существующего имени входа в систему Windows или ввести новое имя пользователя Windows и пароль.  
  
 После изменения имени входа и пароля агента необходимо остановить и повторно запустить агент, чтобы изменения вступили в силу.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_changeqreader_agent**.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение параметров безопасности репликации](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_addqreader_agent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md)  
  
  
