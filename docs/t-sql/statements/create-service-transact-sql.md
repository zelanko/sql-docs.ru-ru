---
title: "Создание службы (Transact-SQL) | Документы Microsoft"
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
- CREATE_SERVICE_TSQL
- SERVICE
- CREATE SERVICE
- SERVICE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- services [Service Broker], creating
- CREATE SERVICE statement
- contracts [Service Broker], service creation
ms.assetid: fb804fa2-48eb-4878-a12f-4e0d5f4bc9e3
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f281cd0f60c0f4f2a37419af4870d927868183a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-service-transact-sql"></a>CREATE SERVICE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает новую службу. Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это имя конкретной задачи или набора бизнес-задач. Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] использует имя службы для маршрутизации сообщений, доставки сообщений в нужную очередь в базе данных и принудительного соблюдения контракта для диалога.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE SERVICE service_name  
   [ AUTHORIZATION owner_name ]  
   ON QUEUE [ schema_name. ]queue_name  
   [ ( contract_name | [DEFAULT][ ,...n ] ) ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Параметры SERVICE_NAME*  
 Имя создаваемой службы. Новая служба создается в текущей базе данных. Владельцем службы назначается участник, указанный в предложении AUTHORIZATION. Не могут быть указаны имена сервера, базы данных и схемы. *Service_name* должен быть допустимым **sysname**.  
  
> [!NOTE]  
>  Не создавайте службу, использующую ключевое слово ANY для *service_name*. При указании ключевого слова ANY для имени службы в инструкции CREATE BROKER PRIORITY приоритет применяется ко всем службам. Его применение не ограничивается службой с именем ANY.  
  
 АВТОРИЗАЦИЯ *owner_name*  
 Определяет в качестве владельца службы указанного пользователя или роль базы данных. Если текущий пользователь является **dbo** или **sa**, *owner_name* может быть именем любого допустимого пользователя или роли. В противном случае *owner_name* должен быть именем текущего пользователя, имя пользователя, что у текущего пользователя есть разрешение IMPERSONATE для или имя роли, к которой принадлежит текущий пользователь.  
  
 ОЧЕРЕДЬ ON [ *имя_схемы***.** ] *имя_очереди*  
 Указывает очередь, в которую поступают сообщения для службы. Очередь должна существовать в той же самой базе данных, что и служба. Если не *schema_name* предоставляется схемой является схема по умолчанию для пользователя, выполняющего инструкцию.  
  
 *contract_name*  
 Указывает контракт, для которого данная служба может быть целью. Служебные программы инициируют диалог с данной службой с помощью указанных контрактов. Если контракты не указаны, инициировать диалог может только служба.  
  
 **[**ПО УМОЛЧАНИЮ**]**  
 Указывает, что служба может быть целью для диалогов, которые следуют контракту DEFAULT. В контексте данного предложения слово DEFAULT не является ключевым словом и должно быть отделено как идентификатор. Контракт DEFAULT разрешает обеим сторонам диалога отправлять сообщения с типом сообщения DEFAULT. Тип сообщений DEFAULT не использует проверку.  
  
## <a name="remarks"></a>Замечания  
 Служба раскрывает функциональность, обеспечиваемую контрактами, с которыми она связана, так что они могут быть использованы другими службами. Инструкция CREATE SERVICE указывает контракты, для которых эта служба является целью. Службы могут быть целью только для диалогов, которые используют контракты, указанные службой. Служба, для которой не указаны контракты, не раскрывает функциональность другим службам.  
  
 Диалоги, инициированные такой службой, могут использовать любой контракт. Если служба только инициирует диалоги, ее можно создавать без определения контрактов.  
  
 Когда компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] принимает новый диалог от удаленной службы, имя целевой службы определяет очередь, в которую брокер размещает сообщения диалога.  
  
## <a name="permissions"></a>Permissions  
 Разрешение на создание службы по умолчанию предоставляется членам **db_ddladmin** или **db_owner** предопределенных ролей базы данных и **sysadmin** предопределенной роли сервера. Пользователь, выполняющий инструкцию CREATE SERVICE, должен иметь разрешение REFERENCES на очередь и все указанные контракты.  
  
 Разрешение REFERENCES для службы по умолчанию имеет владелец службы, члены **db_ddladmin** или **db_owner** фиксированной роли базы данных и члены **sysadmin** Предопределенная роль сервера. Разрешение SEND на службу по умолчанию владелец службы, члены **db_owner** фиксированной роли базы данных, а также члены **sysadmin** предопределенной роли сервера.  
  
 Служба не может быть временным объектом. Имена служб, начинающиеся с  **#**  разрешены, но являются постоянными объектами.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-service-with-one-contract"></a>A. Создание службы с одним контрактом  
 В следующем примере создается служба `//Adventure-Works.com/Expenses` в очереди `ExpenseQueue` в схеме `dbo`. Диалоги, которые задают данную службу, должны следовать контракту `//Adventure-Works.com/Expenses/ExpenseSubmission`.  
  
```  
CREATE SERVICE [//Adventure-Works.com/Expenses]  
    ON QUEUE [dbo].[ExpenseQueue]  
    ([//Adventure-Works.com/Expenses/ExpenseSubmission]) ;  
```  
  
### <a name="b-creating-a-service-with-multiple-contracts"></a>Б. Создание службы с несколькими контрактами  
 В следующем примере создается служба `//Adventure-Works.com/Expenses` в очереди `ExpenseQueue`. Диалоги, которые задают данную службу, должны следовать контракту `//Adventure-Works.com/Expenses/ExpenseSubmission` или `//Adventure-Works.com/Expenses/ExpenseProcessing`.  
  
```  
CREATE SERVICE [//Adventure-Works.com/Expenses] ON QUEUE ExpenseQueue  
    ([//Adventure-Works.com/Expenses/ExpenseSubmission],  
     [//Adventure-Works.com/Expenses/ExpenseProcessing]) ;  
```  
  
### <a name="c-creating-a-service-with-no-contracts"></a>В. Создание службы без контрактов  
 В следующем примере создается служба `//Adventure-Works.com/Expenses on the ExpenseQueue` очереди. Данная служба не имеет сведений о контракте. Поэтому она может быть только инициатором диалога.  
  
```  
CREATE SERVICE [//Adventure-Works.com/Expenses] ON QUEUE ExpenseQueue ;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER SERVICE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-service-transact-sql.md)   
 [Удаление службы &#40; Transact-SQL &#41;](../../t-sql/statements/drop-service-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

