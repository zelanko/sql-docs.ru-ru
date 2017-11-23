---
title: "SEND (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SEND_ON_CONVERSATION_TSQL
- ON_CONVERSATION_TSQL
- SEND
- SEND_TSQL
- SEND ON CONVERSATION
- ON CONVERSATION
dev_langs: TSQL
helpviewer_keywords:
- conversations [Service Broker], message sending
- SEND statement
- messages [Service Broker], sending
- sending messages
ms.assetid: b6e66aeb-1714-4c2b-b7c2-d386d77b0d46
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7d40948dad23dca9dc4905d29a94995f087f78b1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="send-transact-sql"></a>SEND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отправляет сообщение с помощью одного или нескольких существующих диалогов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SEND  
   ON CONVERSATION [(]conversation_handle [,.. @conversation_handle_n][)]  
   [ MESSAGE TYPE message_type_name ]  
   [ ( message_body_expression ) ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 В ДИАЛОГЕ *conversation_handle [... @conversation_handle_n]*  
 Указывает диалоги, к которым принадлежит сообщение. *Conversation_handle* должен содержать правильный идентификатор диалога. Один дескриптор диалога можно использовать только один раз.  
  
 Тип сообщения *message_type_name*  
 Указывает тип отправляемого сообщения. Этот тип сообщений должен входить в контракты служб, используемых этими диалогами. Эти контракты должны позволять отправить сообщение данного типа с этой стороны диалога. Например, целевые службы диалогов могут отправлять только сообщения, отмеченные в контракте как SENT BY TARGET или SENT BY ANY. Если это предложение пропущено, то сообщение принадлежит к типу сообщений DEFAULT.  
  
 *message_body_expression*  
 Содержит выражение, представляющее тело сообщения. *Message_body_expression* является необязательным. Однако если *message_body_expression* присутствует выражение должно иметь тип, который может быть преобразован в **varbinary(max)**. Выражение не может иметь значение NULL. Если это предложение не указано, то тело сообщения пустое.  
  
## <a name="remarks"></a>Замечания  
  
> [!IMPORTANT]  
>  Если инструкция SEND не является первой в пакете или хранимой процедуре, то предшествующая ей инструкция должна заканчиваться точкой с запятой (;).  
  
 Инструкция SEND передает сообщение от служб на одном конце одного или нескольких диалогов компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] службам на другом конце этих диалогов. Инструкция RECEIVE используется для получения отправленного сообщения из очередей, связанных с целевыми службами.  
  
 Указываемые в предложении ON CONVERSATION дескрипторы диалогов берутся из одного из трех источников.  
  
-   При отправке сообщения, не являющегося ответом на полученное от другой службы сообщение, возможно использование дескриптора диалога, возвращенного инструкцией BEGIN DIALOG, с помощью которой был создан диалог.  
  
-   При отправке сообщения, являющегося ответом на полученное от другой службы сообщение, возможно использование дескриптора диалога, возвращенного инструкцией RECEIVE, которая вернула исходное сообщение.  
  
 Часто код, содержащий инструкцию SEND, отделен от кода, содержащего инструкции BEGIN DIALOG или RECEIVE, которые предоставляют дескриптор диалога. В этих случаях дескриптор диалога должен быть одним из элементов данных в сведениях о состоянии, передаваемых коду, содержащему инструкцию SEND.  
  
 Сообщения, отправленные службам в других экземплярах компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], хранятся в очереди передачи текущей базы данных, пока они не будут переданы в очереди обслуживания удаленных экземпляров. Сообщения, отправленные службам в рамках одного экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], помещаются непосредственно в связанные с этими службами очереди. Если поместить локальное сообщение непосредственно в очередь целевой службы невозможно, оно будет сохранено в очереди передачи до появления такой возможности. Это может происходить, например, при некоторых ошибках или в случае, если очередь целевой службы неактивна. Можно использовать **sys.transmission_queue** системного представления для просмотра сообщений в очереди передачи.  
  
 SEND является атомарной инструкцией: если ей не удается отправить сообщение нескольким диалогам (например, из-за того, что в одном диалоге произошла ошибка), то сообщения не сохраняются в очереди передачи и не помещаются в очередь целевой службы.  
  
 Компонент Service Broker оптимизирует хранение и передачу сообщений, отправляемых нескольким диалогам в одной инструкции SEND.  
  
 Передача сообщений, находящихся в очередях передачи экземпляра, выполняется в последовательности, которая определяется:  
  
-   уровнем приоритета связанной с ними конечной точки диалога;  
  
-   последовательности отправки в диалоге при одинаковом приоритете.  
  
 Уровни приоритета, указанные в приоритетах диалога, применяются к сообщениям в очереди передачи только в случае, если параметр базы данных HONOR_BROKER_PRIORITY имеет значение ON. Если параметр HONOR_BROKER_PRIORITY установлен в значение OFF, все сообщения, помещаемые в очередь передачи для этой базы данных, получают приоритет по умолчанию, равный 5. Уровни приоритета не применяются к инструкции SEND, если сообщения помещаются непосредственно в очередь обслуживания одного экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Инструкция SEND по отдельности блокирует каждый диалог, в который отправляется сообщение, чтобы обеспечить упорядоченную доставку для каждого диалога.  
  
 Инструкция SEND недопустима в определяемых пользователем функциях.  
  
## <a name="permissions"></a>Permissions  
 Для отправки сообщения у текущего пользователя должно быть разрешение RECEIVE для очереди в каждой из служб, которые отправляют сообщение.  
  
## <a name="examples"></a>Примеры  
 В этом примере инициируется диалог и отправляется XML-сообщение. Чтобы отправить сообщение, в примере выполняется преобразование XML-объект **varbinary(max)**.  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER,  
        @ExpenseReport XML ;  
  
SET @ExpenseReport = < construct message as appropriate for the application > ;  
  
BEGIN DIALOG @dialog_handle  
FROM SERVICE [//Adventure-Works.com/Expenses/ExpenseClient]  
TO SERVICE '//Adventure-Works.com/Expenses'  
ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseProcessing] ;  
  
SEND ON CONVERSATION @dialog_handle  
    MESSAGE TYPE [//Adventure-Works.com/Expenses/SubmitExpense]  
    (@ExpenseReport) ;  
```  
  
 В этом примере инициируется три диалога и в каждый из них отправляется XML-сообщение.  
  
```  
DECLARE @dialog_handle1 UNIQUEIDENTIFIER,  
        @dialog_handle2 UNIQUEIDENTIFIER,  
        @dialog_handle3 UNIQUEIDENTIFIER,  
        @OrderMsg XML ;  
  
SET @OrderMsg = < construct message as appropriate for the application > ;  
  
BEGIN DIALOG @dialog_handle1  
FROM SERVICE [//InitiatorDB/InitiatorService]  
TO SERVICE '//TargetDB1/TargetService’  
ON CONTRACT [//AllDBs/OrderProcessing] ;  
  
BEGIN DIALOG @dialog_handle2  
FROM SERVICE [//InitiatorDB/InitiatorService]  
TO SERVICE '//TargetDB2/TargetService’  
ON CONTRACT [//AllDBs/OrderProcessing] ;  
  
BEGIN DIALOG @dialog_handle3  
FROM SERVICE [//InitiatorDB/InitiatorService]  
TO SERVICE '//TargetDB3/TargetService’  
ON CONTRACT [//AllDBs/OrderProcessing] ;  
  
SEND ON CONVERSATION (@dialog_handle1, @dialog_handle2, @dialog_handle3)  
    MESSAGE TYPE [//AllDBs/OrderMsg]  
    (@OrderMsg) ;  
```  
  
## <a name="see-also"></a>См. также:  
 [BEGIN DIALOG CONVERSATION &#40; Transact-SQL &#41;](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [END CONVERSATION &#40; Transact-SQL &#41;](../../t-sql/statements/end-conversation-transact-sql.md)   
 [ПОЛУЧИТЬ &#40; Transact-SQL &#41;](../../t-sql/statements/receive-transact-sql.md)   
 [sys.transmission_queue &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-transmission-queue-transact-sql.md)  
  
  
