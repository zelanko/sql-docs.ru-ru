---
title: sp_dropmessage (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropmessage_TSQL
- sp_dropmessage
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropmessage
ms.assetid: 17287a15-cdde-43d1-bb18-9f920bc15db8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b36c576fb5bb3bb3cc168430902223802ca937a3
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535176"
---
# <a name="spdropmessage-transact-sql"></a>sp_dropmessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет заданное пользовательское сообщение об ошибке из экземпляра [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Определяемые пользователем сообщения можно просматривать при помощи **sys.messages** представления каталога.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropmessage [ @msgnum = ] message_number  
    [ , [ @lang = ] 'language' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @msgnum = ] message_number` — Это номер удаляемого сообщения. *message_number* должно быть определенное пользователем сообщение с номером более 50000. *message_number* — **int**, значение по умолчанию NULL.  
  
`[ @lang = ] 'language'` — Это язык сообщения. Если **все** указан, все языковые версии *message_number* удаляются. *Язык* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **sysadmin** и **serveradmin** предопределенных ролей сервера.  
  
## <a name="remarks"></a>Примечания  
 Если не **все** указывается для *языка*, всех остальных локализованных версий сообщения должны быть удалены перед США Английская версия сообщения может быть удалена.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-dropping-a-user-defined-message"></a>A. Удаление пользовательских сообщений  
 В следующем примере удаляется пользовательское сообщение, номер `50001`, из **sys.messages**.  
  
```  
USE master;  
GO  
EXEC sp_dropmessage 50001;  
```  
  
### <a name="b-dropping-a-user-defined-message-that-includes-a-localized-version"></a>Б. Удаление пользовательского сообщения, у которого есть локализованная версия  
 В следующем примере удаляется пользовательское сообщение с номером `60000`, у которого есть локализованная версия.  
  
```  
USE master;  
GO  
  
-- Create a user-defined message in U.S. English  
EXEC sp_addmessage   
    @msgnum = 60000,  
    @severity = 16,  
    @msgtext = N'The item named %s already exists in %s.',   
    @lang = 'us_english';  
  
-- Create a localized version of the same message.  
EXEC sp_addmessage   
    @msgnum = 60000,  
    @severity = 16,  
    @msgtext = N'L''élément nommé %1! existe déjà dans %2!',  
    @lang = 'French';  
GO  
  
-- This statement will fail as long as the localized version  
-- of the message exists.  
EXEC sp_dropmessage 60000;  
GO  
  
-- This statement will drop the message.  
EXEC sp_dropmessage  
    @msgnum = 60000,  
    @lang = 'all';  
GO  
```  
  
### <a name="c-dropping-a-localized-version-of-a-user-defined-message"></a>В. Удаление локализованной версии пользовательского сообщения  
 В этом примере удаляется только локализованная версия пользовательского сообщения с номером `60000`, а само сообщение не удаляется.  
  
```  
USE master;  
GO  
  
-- Create a user-defined message in U.S. English  
EXEC sp_addmessage   
    @msgnum = 60000,  
    @severity = 16,  
    @msgtext = N'The item named %s already exists in %s.',   
    @lang = 'us_english';  
  
-- Create a localized version of the same message.  
EXEC sp_addmessage   
    @msgnum = 60000,  
    @severity = 16,  
    @msgtext = N'L''élément nommé %1! existe déjà dans %2!',  
    @lang = 'French';  
GO  
-- This statement will remove only the localized version of the   
-- message.  
EXEC sp_dropmessage  
    @msgnum = 60000,  
    @lang = 'French';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_addmessage (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sp_altermessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)   
 [sys.messages (Transact-SQL)](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
