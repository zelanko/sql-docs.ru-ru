---
title: "BEGIN CONVERSATION TIMER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONVERSATION
- BEGIN_CONVERSATION_TSQL
- TIMER_TSQL
- TIMER
- CONVERSATION TIMER
- CONVERSATION_TIMER_TSQL
- BEGIN CONVERSATION TIMER
- BEGIN_CONVERSATION_TIMER_TSQL
- CONVERSATION_TSQL
- BEGIN CONVERSATION
dev_langs:
- TSQL
helpviewer_keywords:
- BEGIN CONVERSATION TIMER statement
- DialogTimer message
- dialogs [Service Broker], beginning
- timeouts [Service Broker]
- timer messages [Service Broker]
- conversations [Service Broker], timers
- starting timers [Service Broker]
- http://schemas.microsoft.com/SQL/ServiceBroker/DialogTimer message
ms.assetid: 98e49b3f-a38f-4180-8171-fa9cb30db4cb
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b70228860699b3fefe9a1b5adcfc0250ce5d34e1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="begin-conversation-timer-transact-sql"></a>BEGIN CONVERSATION TIMER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запускает таймер. По истечении времени ожидания [!INCLUDE[ssSB](../../includes/sssb-md.md)] помещает сообщение типа `http://schemas.microsoft.com/SQL/ServiceBroker/DialogTimer` в локальной очереди для диалога.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BEGIN CONVERSATION TIMER ( conversation_handle )  
   TIMEOUT = timeout   
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 BEGIN CONVERSATION TIMER **(***conversation_handle***)**  
 Указывает диалог, длительность которого нужно проконтролировать. *Conversation_handle* должен иметь тип **uniqueidentifier**.  
  
 TIMEOUT   
 Указывает время ожидания (в секундах) перед добавлением сообщения в очередь.  
  
## <a name="remarks"></a>Замечания  
 Таймер диалога предоставляет приложению способ получения сообщения в диалоге по истечении заданного времени. Вызов BEGIN CONVERSATION TIMER в диалоге до истечения времени ожидания устанавливает новое значение времени ожидания. В отличие от времени жизни диалога у каждой стороны диалога имеется свой таймер диалога. **DialogTimer** сообщение поступает в локальной очереди без влияния на удаленной стороне диалога. Поэтому приложение может использовать сообщение таймера для любых нужд.  
  
 Например, можно использовать таймер диалога для предотвращения слишком долгого ожидания приложением запоздалого отклика. Если завершение диалога ожидается в течение 30 секунд, то можно установить таймер для этого диалога на 60 секунд (30 секунд плюс 30 секунд допустимой задержки). Если диалог все еще открыт по истечении 60 секунд, приложение получит в очереди этого диалога сообщение об истечении времени ожидания.  
  
 В качестве альтернативы приложение может использовать таймер диалога для запроса активации в определенный момент. Например, можно создать службу, которая каждые пять минут сообщает число активных подключений. или службу, которая каждый вечер сообщает число открытых заказов на покупку. Служба устанавливает таймер диалога истекает в нужное время; После истечения срока действия таймера, [!INCLUDE[ssSB](../../includes/sssb-md.md)] отправляет **DialogTimer** сообщения. **DialogTimer** сообщений причины [!INCLUDE[ssSB](../../includes/sssb-md.md)] для запуска активации хранимой процедуры для очереди. Хранимая процедура отправляет сообщение удаленной службе и перезапускает таймер диалога.  
  
 Инструкция BEGIN CONVERSATION TIMER не может использоваться в пользовательских функциях.  
  
## <a name="permissions"></a>Permissions  
 Разрешением на установку таймера диалога значения по умолчанию для пользователей, которые есть разрешение SEND для службы в диалоге, члены **sysadmin** фиксированной серверной роли и члены **db_owner** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
 Этот пример устанавливает двухминутное время ожидания для диалога с дескриптором `@dialog_handle`.  
  
```  
-- @dialog_handle is of type uniqueidentifier and  
-- contains a valid conversation handle.  
  
BEGIN CONVERSATION TIMER (@dialog_handle)  
TIMEOUT = 120 ;  
```  
  
## <a name="see-also"></a>См. также:  
 [BEGIN DIALOG CONVERSATION &#40; Transact-SQL &#41;](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [END CONVERSATION &#40; Transact-SQL &#41;](../../t-sql/statements/end-conversation-transact-sql.md)   
 [ПОЛУЧИТЬ &#40; Transact-SQL &#41;](../../t-sql/statements/receive-transact-sql.md)  
  
  

