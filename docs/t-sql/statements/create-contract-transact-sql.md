---
title: "Создание КОНТРАКТА (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONTRACT_TSQL
- CREATE_CONTRACT_TSQL
- CREATE CONTRACT
- CONTRACT
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE CONTRACT statement
- contracts [Service Broker], creating
- message types [Service Broker], contracts
ms.assetid: 494cbfa6-8e93-4161-a64d-90d681915211
caps.latest.revision: 48
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 962ce2d6568a597bd580f7fc9bcd2e9243e44dc4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-contract-transact-sql"></a>Инструкция CREATE CONTRACT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создание нового контракта. Контракт определяет типы сообщений, используемые в диалогах компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], а также определяет, какой из участников диалога может посылать сообщения этого типа. Каждый диалог соответствует контракту. Инициирующая служба определяет контракт для диалога перед его началом. Целевая служба определяет контракты, диалоги для которых она принимает.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE CONTRACT contract_name  
   [ AUTHORIZATION owner_name ]  
      (  {   { message_type_name | [ DEFAULT ] }  
          SENT BY { INITIATOR | TARGET | ANY }   
       } [ ,...n] )   
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *contract_name*  
 Имя создаваемого контракта. Новый контракт создается в текущей базе данных и передается во владение участнику, указанному в предложении AUTHORIZATION.  Не могут быть указаны имена сервера, базы данных и схемы. *Contract_name* может иметь длину до 128 символов.  
  
> [!NOTE]  
>  Не создавайте контракт, использующий ключевое слово ANY для *contract_name*. При указании ключевого слова ANY для имени контракта в инструкции CREATE BROKER PRIORITY приоритет применяется ко всем контрактам. Его применение не ограничивается контрактом с именем ANY.  
  
 АВТОРИЗАЦИЯ *owner_name*  
 Устанавливает в качестве владельца контракта определенного пользователя или роль базы данных. Если текущий пользователь является **dbo** или **sa**, *owner_name* может быть именем любого допустимого пользователя или роли. В противном случае *owner_name* должен быть именем текущего пользователя, имя пользователя, текущий пользователь имеет разрешение на impersonate или имя роли, к которой принадлежит текущий пользователь. Если это предложение опущено, контракт принадлежит текущему пользователю.  
  
 *message_type_name*  
 Имя типа сообщений, включаемого в качестве части контракта.  
  
 SENT BY  
 Указывает, какая из конечных точек может послать сообщение указанного типа сообщений. Контракты сохраняют сообщения, которые могут быть использованы службами для создания определенных диалогов. У каждого диалога есть две конечные точки: *инициатора* конечной точки, служба которой начала диалог, и *целевой* конечной точки, со службой которой связывается инициатор.  
  
 INITIATOR  
 Указывает на то, что только инициатор диалога может посылать сообщения определенного типа. Служба, которая начинает диалог, называют *инициатора* диалога.  
  
 TARGET  
 Указывает на то, что только цель диалога может посылать сообщения определенного типа. Служба, которая принимает диалог, инициированный другой службой, называют *целевой* диалога.  
  
 ANY  
 Указывает на то, что сообщения этого типа могут посылаться как инициатором, так и целью.  
  
 [ DEFAULT ]  
 Указывает на то, что данный контракт поддерживает сообщения с установленным по умолчанию типом сообщений. По умолчанию во всех базах данных содержится тип сообщений с названием DEFAULT. Этот тип данных использует проверку типа NONE.  В контексте данного предложения слово DEFAULT не является ключевым словом и должно быть отделено как идентификатор. Microsoft SQL Server также предоставляет контракт DEFAULT, указывающий тип сообщения DEFAULT.   
  
## <a name="remarks"></a>Замечания  
 Порядок типов сообщений в контракте не важен. После того, как цель получает первое сообщение, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] позволяет каждому участнику диалога в любое время посылать любые сообщения, разрешенные для этого участника. Например, если инициатор диалога может посылать сообщения типа **//Adventure-Works.com/Expenses/SubmitExpense**, [!INCLUDE[ssSB](../../includes/sssb-md.md)] позволяет инициатору посылать произвольное количество **SubmitExpense**сообщения во время диалога.  
  
 Типы и направление сообщений в контракте не могут быть изменены. Чтобы изменить параметр AUTHORIZATION для контракта, следует воспользоваться инструкцией ALTER AUTHORIZATION.  
  
 Необходимо, чтобы контракт позволял инициатору посылать сообщения. Инструкция CREATE CONTRACT завершается сбоем, если в контракте не содержится ни одного сообщения типа SENT BY ANY или SENT BY INITIATOR.  
  
 Независимо от контракта служба всегда может принимать типы сообщений `http://schemas.microsoft.com/SQL/ServiceBroker/DialogTimer`, `http://schemas.microsoft.com/SQL/ServiceBroker/Error`, и `http://schemas.microsoft.com/SQL/ServiceBroker/EndDialog`. Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] использует эти типы сообщений в системных сообщениях для приложения.  
  
 Контракт не может быть временным объектом. Контракты могут иметь имена, начинающиеся с символа #, но являются постоянными объектами.  
  
## <a name="permissions"></a>Permissions  
 По умолчанию члены **db_ddladmin** или **db_owner** предопределенных ролей базы данных и **sysadmin** предопределенной роли сервера можно создавать контракты.  
  
 По умолчанию, владелец контракта, члены **db_ddladmin** или **db_owner** фиксированной роли базы данных и члены **sysadmin** предопределенной роли сервера имеют ссылки разрешения на контракт.  
  
 Пользователь, выполняющий инструкцию CREATE CONTRACT, должен обладать разрешением REFERENCES на все указанные типы сообщений.  
  
## <a name="examples"></a>Примеры  
 **А. Создание контракта**  
  
 В следующем примере создается контракт компенсации расходов, основанный на трех типах сообщений.  
  
```  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]           
    VALIDATION = WELL_FORMED_XML ;           
  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/ExpenseApprovedOrDenied]           
    VALIDATION = WELL_FORMED_XML ;           
  
CREATE MESSAGE TYPE           
    [//Adventure-Works.com/Expenses/ExpenseReimbursed]           
    VALIDATION= WELL_FORMED_XML ;           
  
CREATE CONTRACT            
    [//Adventure-Works.com/Expenses/ExpenseSubmission]           
    ( [//Adventure-Works.com/Expenses/SubmitExpense]           
          SENT BY INITIATOR,           
      [//Adventure-Works.com/Expenses/ExpenseApprovedOrDenied]           
          SENT BY TARGET,           
      [//Adventure-Works.com/Expenses/ExpenseReimbursed]           
          SENT BY TARGET           
    ) ;  
```  
  
## <a name="see-also"></a>См. также:  
 [УДАЛИТЬ КОНТРАКТ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-contract-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
