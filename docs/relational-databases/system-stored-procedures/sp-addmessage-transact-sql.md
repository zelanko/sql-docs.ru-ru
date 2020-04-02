---
title: sp_addmessage (Трансакт-СЗЛ) Документы Майкрософт
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
ms.openlocfilehash: d040fa0ccfe9b962f8847db0a841b95a534326fa
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531037"
---
# <a name="sp_addmessage-transact-sql"></a>sp_addmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Сохраняет новое пользовательское сообщение об ошибке в экземпляре компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Сообщения, хранящиеся с помощью **sp_addmessage,** можно просматривать с помощью представления каталога **sys.messages.**  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmessage [ @msgnum= ] msg_id , [ @severity= ] severity , [ @msgtext= ] 'msg'   
     [ , [ @lang= ] 'language' ]   
     [ , [ @with_log= ] { 'TRUE' | 'FALSE' } ]   
     [ , [ @replace= ] 'replace' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @msgnum = ] msg_id`Является идентификатором сообщения. *msg_id* является **int** с дефолтом NULL. *msg_id* для пользовательских сообщений об ошибках может быть бессетричным между 50,001 и 2,147,483,647. Сочетание *msg_id* и *языка* должно быть уникальным; ошибка возвращается, если идентификатор уже существует для указанного языка.  
  
`[ @severity = ]severity`Является ли уровень серьезности ошибки. *тяжесть* **является небольшой** с дефолтом NULL. Допустимые уровни: от 1 до 25. Дополнительные сведения о степенях серьезности см. в разделе [Степени серьезности ошибок компонента Database Engine](../../relational-databases/errors-events/database-engine-error-severities.md).  
  
`[ @msgtext = ] 'msg'`Является текстом сообщения об ошибке. *msg* **nvarchar (255)** с дефолтом NULL.  
  
`[ @lang = ] 'language'`Это язык для этого сообщения. *язык* **sysname** с по умолчанию NULL. Поскольку на одном сервере можно установить несколько языков, *язык* определяет язык, на котором написано каждое сообщение. Когда *язык* опущен, язык по умолчанию является языком для сеанса.  
  
`[ @with_log = ] { 'TRUE' | 'FALSE' }`Является ли сообщение должно быть записано в журнал приложений Windows, когда оно происходит. with_log **varchar (5)** с дефолтом FALSE. ** \@** Если указано значение TRUE, сообщение об ошибке всегда записывается в журнал приложений Windows. Если указано значение FALSE, то сообщение об ошибке может попасть в журнал приложений Windows в зависимости от того, как эта ошибка возникла. Использовать эту опцию могут только участники роли сервера **sysadmin.**  
  
> [!NOTE]  
>  Если сообщение заносится в журнал приложений Windows, оно также заносится и в журнал ошибок компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
`[ @replace = ] 'replace'`Если указано, как строка *заменить,* существующее сообщение об ошибке перезаписано с новым текстом сообщения и уровнем серьезности. *замена* **varchar (7)** с дефолтом NULL. Эта опция должна быть указана, если *msg_id* уже существует. При замене сообщения на английском языке в США уровень серьезности заменяется для всех сообщений на всех других языках, которые имеют одиников *msg_id.*  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Для версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на других языках версия сообщения на языке «Английский (США)» должна существовать перед добавлением сообщения на другом языке. Уровень серьезности двух разных версий одного сообщения должен совпадать.  
  
 При локализации сообщений, содержащих параметры, следует использовать номера параметров из исходного сообщения. После каждого номера параметра должен стоять восклицательный знак (!).  
  
|Исходное сообщение|Локализованное сообщение|  
|----------------------|-----------------------|  
|'Оригинальное сообщение пара м1: %s,<br /><br /> пара 2: %d'|'Локализованное сообщение param 1: %1!,<br /><br /> пара 2: %2!|  
  
 В связи с различиями в синтаксисе языков номера параметров в локализованных сообщениях могут менять свой изначальный порядок.  
  
## <a name="permissions"></a>Разрешения  
Требуется членство в **sysadmin** или **serveradmin** фиксированных ролей сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-defining-a-custom-message"></a>A. Определение пользовательского сообщения  
 Следующий пример добавляет пользовательское сообщение в **sys.messages.**  
  
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
  
## <a name="see-also"></a>См. также:  
 [&#41;«&#40;Трансакт-СЗЛ»](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_altermessage &#40;&#41;«Трансакт-СЗЛ»](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_dropmessage&#41;&#40;«Трансакт-СЗЛ»](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
