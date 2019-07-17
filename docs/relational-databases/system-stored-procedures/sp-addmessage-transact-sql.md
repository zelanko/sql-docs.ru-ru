---
title: sp_addmessage (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addmessage
- sp_addmessage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addmessage
ms.assetid: 54746d30-f944-40e5-a707-f2d9be0fb9eb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52d3db15c46af273e2f151e769a6b04be322ce5b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061839"
---
# <a name="spaddmessage-transact-sql"></a>sp_addmessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Сохраняет новое пользовательское сообщение об ошибке в экземпляре компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Сообщения, сохраненные с помощью **sp_addmessage** можно просмотреть с помощью **sys.messages** представления каталога.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmessage [ @msgnum= ] msg_id , [ @severity= ] severity , [ @msgtext= ] 'msg'   
     [ , [ @lang= ] 'language' ]   
     [ , [ @with_log= ] { 'TRUE' | 'FALSE' } ]   
     [ , [ @replace= ] 'replace' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ \@msgnum = ] msg_id` — Идентификатор сообщения. *msg_id* — **int** значение по умолчанию NULL. *msg_id* для ошибки, определенные пользователем сообщения может быть в диапазоне от 50 001 до 2 147 483 647. Сочетание *msg_id* и *языка* должно быть уникальным; ошибка возвращается, если такой идентификатор уже задан для указанного языка.  
  
`[ \@severity = ]severity` — Это уровень серьезности ошибки. *уровень серьезности* — **smallint** значение по умолчанию NULL. Допустимые уровни: от 1 до 25. Дополнительные сведения о степенях серьезности см. в разделе [Степени серьезности ошибок компонента Database Engine](../../relational-databases/errors-events/database-engine-error-severities.md).  
  
`[ \@msgtext = ] 'msg'` — Текст сообщения об ошибке. *msg* — **nvarchar(255)** значение по умолчанию NULL.  
  
`[ \@lang = ] 'language'` — Это язык для данного сообщения. *Язык* — **sysname** значение по умолчанию NULL. Поскольку несколько языков, которые могут быть установлены на одном сервере, *языка* указывает язык, на котором написано каждое сообщение. Когда *языка* — этот параметр опущен, язык — язык по умолчанию для сеанса.  
  
`[ \@with_log = ] { 'TRUE' | 'FALSE' }` Является ли сообщение записываться в журнал приложений Windows, при его возникновении. **\@WITH_LOG** — **varchar(5)** значение по умолчанию FALSE. Если указано значение TRUE, сообщение об ошибке всегда записывается в журнал приложений Windows. Если указано значение FALSE, то сообщение об ошибке может попасть в журнал приложений Windows в зависимости от того, как эта ошибка возникла. Только члены **sysadmin** роли сервера могут использовать этот параметр.  
  
> [!NOTE]  
>  Если сообщение заносится в журнал приложений Windows, оно также заносится и в журнал ошибок компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
`[ \@replace = ] 'replace'` Если указано строковое *замените*, сообщение об ошибке существующих перезаписывается новые сообщения текстом и уровнем серьезности. *Замените* — **varchar(7)** значение по умолчанию NULL. Этот параметр должен быть задан, если *msg_id* уже существует. Если перезаписать сообщение на американском английском, Сообщение на английском языке, уровень серьезности будет переопределен для всех сообщений на других языках, которые имеют одинаковые *msg_id*.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Для версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на языках, отличных от английского, версия сообщения на американском английском уже должна существовать перед добавлением сообщения на другом языке. Уровень серьезности двух разных версий одного сообщения должен совпадать.  
  
 При локализации сообщений, содержащих параметры, следует использовать номера параметров из исходного сообщения. После каждого номера параметра должен стоять восклицательный знак (!).  
  
|Исходное сообщение|Локализованное сообщение|  
|----------------------|-----------------------|  
|' Параметр 1 оригинального сообщения: %s<br /><br /> PARAM 2: %d "|"1 оригинального сообщения: %1!,<br /><br /> PARAM 2: %2! "|  
  
 В связи с различиями в синтаксисе языков номера параметров в локализованных сообщениях могут менять свой изначальный порядок.  
  
## <a name="permissions"></a>Разрешения  
Требуется членство в **sysadmin** или **serveradmin** предопределенных ролей сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-defining-a-custom-message"></a>A. Определение пользовательского сообщения  
 В следующем примере добавляется сообщение, **sys.messages**.  
  
```  
USE master;  
GO  
EXEC sp_addmessage 50001, 16,   
   N'Percentage expects a value between 20 and 100.   
   Please reexecute with a more appropriate value.';  
GO  
```  
  
### <a name="b-adding-a-message-in-two-languages"></a>Б. Добавление сообщения на двух языках  
 В следующем примере впервые добавляется сообщение на американском английском, затем то же сообщение добавляется на французском`.`  
  
```  
USE master;  
GO  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'The item named %s already exists in %s.',   
   @lang = 'us_english';  
  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'L''élément nommé %1! existe déjà dans %2!',   
   @lang = 'French';  
GO  
```  
  
### <a name="c-changing-the-order-of-parameters"></a>В. Изменение порядка параметров  
 В следующем примере впервые добавляется сообщение на американском английском, затем добавляется локализованное сообщение с измененным порядком параметров.  
  
```  
USE master;  
GO  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        N'This is a test message with one numeric  
        parameter (%d), one string parameter (%s),   
        and another string parameter (%s).',  
    @lang = 'us_english';  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        -- In the localized version of the message,  
        -- the parameter order has changed. The   
        -- string parameters are first and second  
        -- place in the message, and the numeric   
        -- parameter is third place.  
        N'Dies ist eine Testmeldung mit einem   
        Zeichenfolgenparameter (%3!),  
        einem weiteren Zeichenfolgenparameter (%2!),   
        und einem numerischen Parameter (%1!).',  
    @lang = 'German';  
GO    
  
-- Changing the session language to use the U.S. English  
-- version of the error message.  
SET LANGUAGE us_english;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2') -- error, severity, state,  
GO                                       -- parameters.  
  
-- Changing the session language to use the German  
-- version of the error message.  
SET LANGUAGE German;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2'); -- error, severity, state,   
GO                                       -- parameters.  
```  
  
## <a name="see-also"></a>См. также  
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_altermessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_dropmessage (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
