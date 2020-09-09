---
description: sp_dropmessage (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: cb4480908dc508fb82e591b2a9dbab448f951961
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89536529"
---
# <a name="sp_dropmessage-transact-sql"></a>sp_dropmessage (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет заданное пользовательское сообщение об ошибке из экземпляра [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Определяемые пользователем сообщения можно просматривать с помощью представления каталога **sys. messages** .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropmessage [ @msgnum = ] message_number  
    [ , [ @lang = ] 'language' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @msgnum = ] message_number` Номер сообщения для удаления. *message_number* должно быть определяемым пользователем сообщением, имеющим номер сообщения, превышающий 50000. *message_number* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @lang = ] 'language'` Язык сообщения для удаления. Если указано значение **ALL** , то все языковые версии *message_number* удаляются. *Language* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенных ролях сервера **sysadmin** и **serveradmin** .  
  
## <a name="remarks"></a>Примечания  
 Если для *языка*не указано значение **ALL** , все локализованные версии сообщения должны быть удалены до тех пор, пока не будет удалена версия сообщения для английского языка (США).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-dropping-a-user-defined-message"></a>A. Удаление пользовательских сообщений  
 В следующем примере удаляется определяемое пользователем сообщение Number `50001` из представления **sys. messages**.  
  
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
  
  
