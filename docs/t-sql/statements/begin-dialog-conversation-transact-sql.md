---
title: "BEGIN DIALOG CONVERSATION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
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
- DIALOG CONVERSATION
- DIALOG
- BEGIN_DIALOG_TSQL
- BEGIN_DIALOG_CONVERSATION_TSQL
- DIALOG_CONVERSATION_TSQL
- DIALOG_TSQL
- BEGIN DIALOG
- BEGIN DIALOG CONVERSATION
dev_langs:
- TSQL
helpviewer_keywords:
- conversations [Service Broker]
- beginning dialogs
- dialogs [Service Broker], beginning
- BEGIN DIALOG CONVERSATION statement
- cryptography [SQL Server], conversations
- opening conversations
- encryption [SQL Server], conversations
- starting conversations
ms.assetid: 8e814f9d-77c1-4906-b8e4-668a86fc94ba
caps.latest.revision: 47
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6e1f746ea0607759329b32499aed5887ee44b650
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="begin-dialog-conversation-transact-sql"></a>BEGIN DIALOG CONVERSATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает диалог между двумя службами. Диалог — это сеанс связи, который обеспечивает доставку сообщений строго по порядку между двумя службами.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BEGIN DIALOG [ CONVERSATION ] @dialog_handle  
   FROM SERVICE initiator_service_name  
   TO SERVICE 'target_service_name'  
       [ , { 'service_broker_guid' | 'CURRENT DATABASE' }]   
   [ ON CONTRACT contract_name ]  
   [ WITH  
   [  { RELATED_CONVERSATION = related_conversation_handle   
      | RELATED_CONVERSATION_GROUP = related_conversation_group_id } ]   
   [ [ , ] LIFETIME = dialog_lifetime ]   
   [ [ , ] ENCRYPTION = { ON | OFF }  ] ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 **@***dialog_handle*  
 Переменная, используемая для хранения дескриптора диалога, сформированного системой для нового диалога, который был возвращен инструкцией BEGIN DIALOG CONVERSATION. Переменная должна иметь тип **uniqueidentifier**.  
  
 ИЗ службы *initiator_service_name*  
 Указывает службу стороны, вызывающей диалог. Указанное имя должно быть именем службы в текущей базе данных. Очередь, указанная для вызывающей службы, получает сообщения, возвращенные целевой службой, и сообщения, созданные компонентом Service Broker для данного диалога.  
  
 СЛУЖБЕ **"***target_service_name***"**  
 Указывает целевую службу, с которой необходимо начать диалог. *Target_service_name* относится к типу **nvarchar(256)**. [!INCLUDE[ssSB](../../includes/sssb-md.md)]использует сравнение байт за байтом *target_service_name* строка. Другими словами, сравнение чувствительно к регистру и не использует текущие параметры сортировки.  
  
 *service_broker_guid*  
 Указывает базу данных, в которой расположена целевая служба. Если несколько баз данных содержат экземпляр целевой службы, для взаимодействия с определенной базы данных, предоставляя *service_broker_guid*.  
  
 *Service_broker_guid* относится к типу **nvarchar(128)**. Чтобы найти *service_broker_guid* для базы данных, выполните следующий запрос в базе данных:  
  
```  
SELECT service_broker_guid  
FROM sys.databases  
WHERE database_id = DB_ID() ;  
```  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 **"**ТЕКУЩЕЙ БАЗЫ ДАННЫХ**"**  
 Указывает, что диалог использует *service_broker_guid* в текущей базе данных.  
  
 Предложение ON CONTRACT *contract_name*  
 Указывает контракт, которого придерживается данный диалог. Контракт должен существовать в текущей базе данных. Если целевая служба не принимает новые диалоги по указанному контракту, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] возвращает сообщение об ошибке диалога. Если это предложение опущено, диалог придерживается контракта с именем **по умолчанию**.  
  
 RELATED_CONVERSATION  **=**  *related_conversation_handle*  
 Указывает существующую группу сообщений, к которой добавляется новый диалог. Если присутствует данное предложение, новый диалог принадлежит к той же группе сообщений, что диалог, определяемый дескриптором *related_conversation_handle*. *Related_conversation_handle*должен быть типа могут быть неявно преобразованы в тип **uniqueidentifier**. Выполнение инструкции завершается неудачно, если *related_conversation_handle* не ссылается на существующий диалог.  
  
 RELATED_CONVERSATION_GROUP  **=**  *related_conversation_group_id*  
 Указывает существующую группу сообщений, к которой добавляется новый диалог. Если присутствует данное предложение, новый диалог будет добавлен к группе сообщений, указанной в *related_conversation_group_id*. *Related_conversation_group_id*должен быть типа могут быть неявно преобразованы в тип **uniqueidentifier**. Если *related_conversation_group_id*ссылка существующей группой сообщений, компонент service broker создает новую группу сообщений с указанным *related_conversation_group_id* и связывает новый диалог с полученной группой сообщений.  
  
 Время СУЩЕСТВОВАНИЯ  **=**  *dialog_lifetime*  
 Указывает максимальный период времени, в течение которого диалог будет оставаться открытым. Для успешного завершения диалога обе конечные точки должны явно завершить диалог до истечения его времени жизни. *Dialog_lifetime* значение должно быть выражено в секундах. Аргумент имеет тип **int**. Если указано предложение LIFETIME время жизни диалога принимает максимальное значение **int** тип данных.  
  
 ENCRYPTION  
 Указывает, должны ли отправленные и полученные в данном диалоге сообщения шифроваться, если они отправляются за пределы экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Диалоговое окно, которое должен быть зашифрован — *защищенным диалогом*. Если используется предложение ENCRYPTION = ON, а сертификаты, необходимые для поддержки шифрования, не настроены, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] возвращает сообщение об ошибке диалога. Если ШИФРОВАНИЕ = OFF, шифрование используется в том случае, если привязка удаленной службы настроена для *target_service_name*; в противном случае сообщения отсылаются нешифрованными. Если данное предложение отсутствует, присваивается значение по умолчанию ON.  
  
> [!NOTE]  
>  Сообщения, которыми обмениваются службы в одном и том же экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], никогда не шифруются. Однако главный ключ базы данных и сертификаты на шифрование все еще требуются для диалогов, использующих шифрование, если службы, для которых создается диалог, находятся в разных базах данных. Благодаря чему диалоги могут быть продолжены, когда в процессе диалога одна из баз данных перемещается в другой экземпляр.  
  
## <a name="remarks"></a>Замечания  
 Все сообщения являются частью диалога. Следовательно, перед отправкой сообщения целевой службе служба вызывающей стороны должна начать с ней диалог. Данные, указанные в инструкции BEGIN DIALOG CONVERSATION, аналогичны адресу письма. Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] использует эти данные для отправки сообщений правильной службе. Указанная в предложении TO SERVICE служба — это адрес, по которому отправляются сообщения. Служба, указанная в предложении FROM SERVICE, является обратным адресом, используемым для ответных сообщений.  
  
 Целевой службе диалога не обязательно вызывать BEGIN DIALOG CONVERSATION. Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] создает диалог в целевой базе данных, когда от инициатора диалога поступает первое сообщение.  
  
 В начале диалога создается конечная точка диалога в базе данных для инициирующей службы, но сетевое подключение к экземпляру, на котором размещается целевая служба, не создается. Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] не устанавливает соединение с целевой службой диалога, пока не будет отправлено первое сообщение.  
  
 Если в инструкции BEGIN DIALOG CONVERSATION не указан связанный диалог или группа сообщений, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] создает новую группу сообщений для нового диалога.  
  
 Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] запрещает произвольное группирование диалогов. Для всех диалогов в группе сообщений в предложении FROM должна быть указана либо вызывающая служба, либо целевая служба диалога.  
  
 Команда BEGIN DIALOG CONVERSATION блокирует группу сообщений, содержащий *dialog_handle* возвращается. Если команда содержит предложение RELATED_CONVERSATION_GROUP, группой сообщений для *dialog_handle* группы сообщений задается в *related_conversation_group_id* параметра. Если команда содержит предложение RELATED_CONVERSATION, группой сообщений для *dialog_handle* группа сообщений связана с *related_conversation_handle* указанного.  
  
 Инструкция BEGIN DIALOG CONVERSATION не используется в функции, определяемой пользователем.  
  
## <a name="permissions"></a>Permissions  
 Чтобы создать диалог, текущий пользователь должен иметь разрешение RECEIVE на очередь для службы, указанной в предложении FROM команды, и разрешение REFERENCES на указанный контракт.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-beginning-a-dialog"></a>A. Создание диалога  
 В следующем примере начинается диалог, идентификатор которого сохраняется в параметре `@dialog_handle.`. Служба `//Adventure-Works.com/ExpenseClient` является инициатором диалога, а служба `//Adventure-Works.com/Expenses` — его целевой службой. Этот диалог следует контракту `//Adventure-Works.com/Expenses/ExpenseSubmission`.  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER ;  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission] ;  
```  
  
### <a name="b-beginning-a-dialog-with-an-explicit-lifetime"></a>Б. Создание диалога с явно заданным временем жизни  
 В следующем примере создается двусторонний диалог с сохранением идентификатора диалога в параметре `@dialog_handle`. Служба `//Adventure-Works.com/ExpenseClient` является инициатором диалога, а служба `//Adventure-Works.com/Expenses` — его целевой службой. Этот диалог следует контракту `//Adventure-Works.com/Expenses/ExpenseSubmission`. Если диалог не был закрыт при помощи команды END CONVERSATION в течение `60` секунд, компонент Service Broker завершает этот диалог с ошибкой.  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER ;  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]  
   WITH LIFETIME = 60 ;  
```  
  
### <a name="c-beginning-a-dialog-with-a-specific-broker-instance"></a>В. Создание диалога с определенным экземпляром брокера  
 В следующем примере создается двусторонний диалог с сохранением идентификатора диалога в параметре `@dialog_handle`. Служба `//Adventure-Works.com/ExpenseClient` является инициатором диалога, а служба `//Adventure-Works.com/Expenses` — его целевой службой. Этот диалог следует контракту `//Adventure-Works.com/Expenses/ExpenseSubmission`. Компонент Service Broker перенаправляет сообщения этого диалога компоненту Service Broker с идентификатором GUID `a326e034-d4cf-4e8b-8d98-4d7e1926c904.`  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER ;  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses',   
              'a326e034-d4cf-4e8b-8d98-4d7e1926c904'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission] ;  
```  
  
### <a name="d-beginning-a-dialog-and-relating-it-to-an-existing-conversation-group"></a>Г. Создание диалога и его соотнесение с существующей группой сообщений  
 В следующем примере создается двусторонний диалог с сохранением идентификатора диалога в параметре `@dialog_handle`. Служба `//Adventure-Works.com/ExpenseClient` является инициатором диалога, а служба `//Adventure-Works.com/Expenses` — его целевой службой. Этот диалог следует контракту `//Adventure-Works.com/Expenses/ExpenseSubmission`. Компонент Service Broker связывает этот диалог с группой сообщений, указанной параметром `@conversation_group_id`, а не создает новую группу сообщений.  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER ;  
DECLARE @conversation_group_id UNIQUEIDENTIFIER ;  
  
SET @conversation_group_id = <retrieve conversation group ID from database>  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]  
   WITH RELATED_CONVERSATION_GROUP = @conversation_group_id ;  
```  
  
### <a name="e-beginning-a-dialog-with-an-explicit-lifetime-and-relating-the-dialog-to-an-existing-conversation"></a>Д. Создание диалога с явно заданным временем жизни и соотнесение диалога с одним из существующих диалогов  
 В следующем примере создается двусторонний диалог с сохранением идентификатора диалога в параметре `@dialog_handle`. Служба `//Adventure-Works.com/ExpenseClient` является инициатором диалога, а служба `//Adventure-Works.com/Expenses` — его целевой службой. Этот диалог следует контракту `//Adventure-Works.com/Expenses/ExpenseSubmission`. Новый диалог принадлежит к той же группе сообщений, что и `@existing_conversation_handle`. Если диалог не был закрыт при помощи команды END CONVERSATION в течение `600` секунд, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] завершает этот диалог с ошибкой.  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER  
DECLARE @existing_conversation_handle UNIQUEIDENTIFIER  
  
SET @existing_conversation_handle = <retrieve conversation handle from database>  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]  
   WITH RELATED_CONVERSATION = @existing_conversation_handle  
   LIFETIME = 600 ;  
```  
  
### <a name="f-beginning-a-dialog-with-optional-encryption"></a>Е. Создание диалога с дополнительным шифрованием  
 В следующем примере создается двусторонний диалог с сохранением идентификатора диалога в параметре `@dialog_handle`. Служба `//Adventure-Works.com/ExpenseClient` является инициатором диалога, а служба `//Adventure-Works.com/Expenses` — его целевой службой. Этот диалог следует контракту `//Adventure-Works.com/Expenses/ExpenseSubmission`. Диалог в этом примере разрешает сообщению перемещаться в сети без шифрования в случае, если шифрование недоступно.  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]  
   WITH ENCRYPTION = OFF ;  
```  
  
## <a name="see-also"></a>См. также:  
 [BEGIN CONVERSATION TIMER &#40; Transact-SQL &#41;](../../t-sql/statements/begin-conversation-timer-transact-sql.md)   
 [END CONVERSATION &#40; Transact-SQL &#41;](../../t-sql/statements/end-conversation-transact-sql.md)   
 [ПЕРЕМЕСТИТЬ ДИАЛОГА &#40; Transact-SQL &#41;](../../t-sql/statements/move-conversation-transact-sql.md)   
 [sys.conversation_endpoints &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)  
  
  

