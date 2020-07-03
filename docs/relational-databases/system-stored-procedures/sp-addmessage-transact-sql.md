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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: adf32fad3c233023529d362cd7382ca6376b3cee
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85877392"
---
# <a name="sp_addmessage-transact-sql"></a>sp_addmergefilter (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Сохраняет новое пользовательское сообщение об ошибке в экземпляре компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Сообщения, хранящиеся с помощью **sp_addmessage** , можно просмотреть с помощью представления каталога **sys. messages** .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmessage [ @msgnum= ] msg_id , [ @severity= ] severity , [ @msgtext= ] 'msg'   
     [ , [ @lang= ] 'language' ]   
     [ , [ @with_log= ] { 'TRUE' | 'FALSE' } ]   
     [ , [ @replace= ] 'replace' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @msgnum = ] msg_id`Идентификатор сообщения. *msg_id* имеет **тип int** и значение по умолчанию NULL. *msg_id* для определяемых пользователем сообщений об ошибках может быть целым числом от 50 001 до 2 147 483 647. Сочетание *msg_id* и *языка* должно быть уникальным; Если идентификатор уже существует для указанного языка, возвращается ошибка.  
  
`[ @severity = ]severity`Уровень серьезности ошибки. *уровень серьезности* — **smallint** и значение по умолчанию NULL. Допустимые уровни: от 1 до 25. Дополнительные сведения о степенях серьезности см. в разделе [Степени серьезности ошибок компонента Database Engine](../../relational-databases/errors-events/database-engine-error-severities.md).  
  
`[ @msgtext = ] 'msg'`Текст сообщения об ошибке. *MSG* имеет тип **nvarchar (255)** и значение по умолчанию NULL.  
  
`[ @lang = ] 'language'`Язык этого сообщения. *Language* имеет тип **sysname** и значение по умолчанию NULL. Поскольку на одном сервере можно установить несколько языков, *язык* определяет язык, на котором написано каждое сообщение. Если *язык* не указан, язык является языком по умолчанию для сеанса.  
  
`[ @with_log = ] { 'TRUE' | 'FALSE' }`Указывает, следует ли записывать сообщение в журнал приложений Windows при его возникновении. ** \@ WITH_LOG** имеет тип **varchar (5)** и значение по умолчанию false. Если указано значение TRUE, сообщение об ошибке всегда записывается в журнал приложений Windows. Если указано значение FALSE, то сообщение об ошибке может попасть в журнал приложений Windows в зависимости от того, как эта ошибка возникла. Только члены роли сервера **sysadmin** могут использовать этот параметр.  
  
> [!NOTE]  
>  Если сообщение заносится в журнал приложений Windows, оно также заносится и в журнал ошибок компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
`[ @replace = ] 'replace'`При указании в качестве *замены*строки существующее сообщение об ошибке перезаписывается новым текстом сообщения и уровнем серьезности. *Replace* имеет тип **varchar (7)** и значение по умолчанию NULL. Этот параметр необходимо указать, если *msg_id* уже существует. При замене сообщения английского языка (США), уровень серьезности заменяется для всех сообщений на всех языках, имеющих тот же *msg_id*.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Для версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на других языках версия сообщения на языке «Английский (США)» должна существовать перед добавлением сообщения на другом языке. Уровень серьезности двух разных версий одного сообщения должен совпадать.  
  
 При локализации сообщений, содержащих параметры, следует использовать номера параметров из исходного сообщения. После каждого номера параметра должен стоять восклицательный знак (!).  
  
|Исходное сообщение|Локализованное сообщение|  
|----------------------|-----------------------|  
|' Параметр исходного сообщения 1:% s,<br /><br /> параметр 2:% d|' Параметр локализованного сообщения 1: %1!,<br /><br /> параметр 2: %2!|  
  
 В связи с различиями в синтаксисе языков номера параметров в локализованных сообщениях могут менять свой изначальный порядок.  
  
## <a name="permissions"></a>Разрешения  
Требуется членство в предопределенных ролях сервера **sysadmin** или **serveradmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-defining-a-custom-message"></a>A. Определение пользовательского сообщения  
 В следующем примере пользовательское сообщение добавляется в представление **sys. messages**.  
  
```  
USE master;  
GO  
EXEC sp_addmessage 50001, 16,   
   N'Percentage expects a value between 20 and 100.   
   Please reexecute with a more appropriate value.';  
GO  
```  
  
### <a name="b-adding-a-message-in-two-languages"></a>Б. Добавление сообщения на двух языках  
 В следующем примере сначала создается сообщение на английском языке, а затем добавляется сообщение на французском`.`  
  
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
 В следующем примере сначала создается сообщение на английском языке, а затем добавляется локализованное сообщение с измененным порядком параметров.  
  
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
  
  
